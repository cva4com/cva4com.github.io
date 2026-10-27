---
linkTitle: Supertonic-3
title: Install Supertonic-3 TTS with Conda
weight: 15
cascade:
  type: docs
tags:
  - TTS
  - Supertonic
  - Open Weights
---

## Introduction

Supertonic is a lightning-fast, on-device multilingual text-to-speech system designed for local inference with minimal overhead. Powered by ONNX Runtime, it runs entirely on your device—no cloud, no API calls, no privacy concerns.

GitHub: https://github.com/supertone-inc/supertonic  
Hugging Face: https://hf.co/Supertone/supertonic-3  
Paper: https://hf.co/papers/2410.06885  
Demo: https://hf.co/spaces/Supertone/supertonic-3  
Audio Samples: https://supertonic3.github.io  
Available Voices: https://supertone-inc.github.io/supertonic-py/voices/  


## Languages

🌍 Supported Languages (31)

Arabic (`ar`), Bulgarian (`bg`), Croatian (`hr`), Czech (`cs`), Danish (`da`), Dutch (`nl`), English (`en`), Estonian (`et`), Finnish (`fi`), French (`fr`), German (`de`), Greek (`el`), Hindi (`hi`), Hungarian (`hu`), Indonesian (`id`), Italian (`it`), Japanese (`ja`), Korean (`ko`), Latvian (`lv`), Lithuanian (`lt`), Polish (`pl`), Portuguese (`pt`), Romanian (`ro`), Russian (`ru`), Slovak (`sk`), Slovenian (`sl`), Spanish (`es`), Swedish (`sv`), Turkish (`tr`), Ukrainian (`uk`), Vietnamese (`vi`)

> **Not sure which language your text is in?** Pass `lang="na"` and Supertonic will handle the input in a language-agnostic way — no explicit language tag required.


## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** version >= 3.10 required
*   **Disk Space:** 10GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
*   **The GPU** is optional but HIGHLY Recommended for Performance.
*   **Internet:** For downloading dependencies and models from Hugging Face Hub.

{{< tabs >}}

  {{< tab name="CPU only" >}}
| Requirements | CPU | RAM |
| :--- | :--- | :--- |
| Minimum | Intel Core i3 or AMD Ryzen 3 | 8 GB |
| Recommended | Intel Core i5 or AMD Ryzen 5 | 16 GB |
| High-performance | Intel Core i7/i9 or AMD Ryzen 7/9 | 32 GB |
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
[Install PyTorch for NVIDIA](https://pytorch.org/get-started/locally/)
![PyTorch](/images/2026/pytorch.png)

Note: CUDA version check by command

```bash
nvidia-smi
```

![PyTorch](/images/2026/nvidia-smi.png)
  {{< /tab >}}

  {{< tab name="AMD" >}}
[Install PyTorch for ROCm](https://rocm.docs.amd.com/projects/ai-ecosystem/en/latest/frameworks/pytorch/install.html)
![PyTorch](/images/2026/ROCm.png)
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
PyTorch can be installed and used on macOS. Depending on your system and GPU capabilities, your experience with PyTorch on macOS may vary in terms of processing time.
  {{< /tab >}}

{{< /tabs >}}

| Environment | Run this Command |
| :-- | :-- |
| CPU only  | pip3 install torch torchvision |
| Apple Silicon | pip3 install torch torchvision |
| AMD ROCm | [Install PyTorch for ROCm](https://rocm.docs.amd.com/projects/ai-ecosystem/en/latest/frameworks/pytorch/install.html) |
| CUDA 11.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130 |


## Video tutorial

{{< youtube hA6G0L_ebYs >}}


## Step 1. Install Miniconda Package

{{< tabs >}}

  {{< tab name="Windows" >}}
Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe  
Direct link: https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-arm64.exe

> How to [Install Miniconda on Windows](https://cva4.com/tuts/tts/miniconda/)
  {{< /tab >}}

  {{< tab name="Mac" >}}
Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-MacOSX-arm64.pkg

> How to [Install Miniconda on MacOS](https://cva4.com/tuts/tts/miniconda/#install-miniconda-on-macos)
  {{< /tab >}}

  {{< tab name="Linux" >}}
Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh  
Direct link: https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh

> How to [Install Miniconda on Linux](https://cva4.com/tuts/tts/miniconda/#install-miniconda-on-linux)
  {{< /tab >}}

{{< /tabs >}}


## Step 2. Create Conda Environment

Create a conda environment:

```yml
name: supertonic
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.10

  - pip
  - pip:
      # Supertonic TTS
      - supertonic

      # Local HTTP Server
      - supertonic[serve]
```

Activate conda environment:

```bash
conda env create -f environment.yml
conda activate supertonic
```


## Step 3. Create a Python Script

Create a file named supertonic_tts_test.py:

```python
from supertonic import TTS

# First run downloads the model from Hugging Face automatically.
tts = TTS(auto_download=True)

style = tts.get_voice_style(voice_name="M1")

text = "Supertonic is a lightning fast, on-device TTS system."

wav, duration = tts.synthesize(
    text=text,
    lang="en",                      # Language code (e.g., "en", "ko", "na" for language-agnostic)
    voice_style=style,              # Voice style object
    total_steps=8,                  # Quality: 5 (low) to 12 (high), default 8 (medium)
    speed=1.05,                     # Speed: 0.7 (slow) to 2.0 (fast)
)
# wav: numpy array of shape (1, num_samples,) with dtype=np.float32, sampled at 44100 Hz
# duration: numpy array of shape (1,) containing the duration of the generated audio in seconds

tts.save_audio(wav, "output.wav")
# import soundfile as sf
# sf.write("output.wav", wav.squeeze(), 44100)

print(f"Generated {duration[0]:.2f}s of audio")
```

Run it:

```bash
python supertonic_tts_test.py
```

The result will be the audio file `output.wav`


### Local HTTP Server

The Python SDK can also run Supertonic as a local HTTP service. This is useful when you want to call Supertonic from tools that already speak HTTP, such as local agents, browser extensions, Electron apps, workflow automation tools, or OpenAI-compatible audio clients.

```bash
supertonic serve --host 127.0.0.1 --port 7788
```

Once running, use the native `POST /v1/tts` endpoint or the OpenAI-compatible `POST /v1/audio/speech` endpoint. The server also exposes interactive OpenAPI docs at `http://127.0.0.1:7788/docs`. See the [supertonic-py serve guide](https://supertone-inc.github.io/supertonic-py/cli/serve/) for request examples, batch synthesis, and custom Voice Builder JSON import.