---
linkTitle: Korva
title: Install KorvaTTS with Conda
weight: 12
cascade:
  type: docs
tags:
  - TTS
  - Korva
  - KorvaTTS
  - Open Weights
params:
  tabs:
    sync: true
---

## Introduction

KorvaTTS is an open-source text-to-speech system focused on **Vietnamese with natural code-switching** (Vietnamese sentences that contain English words, brand names, tech terms). It runs entirely on-device through ONNX Runtime: no GPU required, no API calls, 44.1 kHz output.

GitHub: https://github.com/dogenthq/KorvaTTS  
Hugging Face: https://hf.co/collections/dogenthq/KorvaTTS  
Demo Page: https://hf.co/spaces/hugging-apps/korvatts-demo  
Try it online: https://heykorva.com  

The model is our own re-implementation of the 99M-parameter [Supertonic 3](https://github.com/supertone-inc/supertonic) architecture (flow-matching TTS), **trained from scratch** on Vietnamese data, with a vocoder based on [BlueCodec](https://github.com/maxmelichov/BlueTTS). Upstream Supertonic is being archived by its authors; KorvaTTS continues the line with a Vietnamese focus and an open roadmap toward voice cloning and training.

**🌐 Try it in your browser — no install:** [heykorva.com](https://heykorva.com/)

## Highlights

- 🇻🇳 **Vietnamese-first** — trained on Vietnamese audiobook speech plus a private code-switching set
- 🔀 **Code-switching** — English words inside Vietnamese sentences are read naturally
- ⚡ **Fast on CPU** — real-time factor well below 1 on a laptop CPU; GPU optional
- 🔊 **44.1 kHz WAV** output, no external upsampler
- 🧩 **Drop-in compatible** with Supertonic 3 runtimes (see [Compatibility](#compatibility-with-supertonic))
- 🪪 **Apache-2.0** for both code and weights


## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** version >= 3.10 required
*   **Disk Space:** 5GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
*   **The GPU** is optional but HIGHLY Recommended for Performance.
*   **Internet:** For downloading dependencies and models from Hugging Face Hub.

ONNX Runtime doesn't publish a separate build per `cuXXX` tag the way PyTorch does. There are only three CUDA builds, so your list collapses into three groups:

| Your CUDA | Build to install |
|---|---|
| cu118 | CUDA 11.8 build (`onnxruntime-gpu` 1.20.x) |
| cu121, cu124, cu126, cu128, cu129 | CUDA 12.x build (`onnxruntime-gpu<1.27`) |
| cu130, cu132, cu134 | CUDA 13.x build (`onnxruntime-gpu>=1.27`) |


## Video tutorial

Coming soon!
<!-- {{< youtube mqFtFIAlvB4 >}} -->


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

Create an environment.yml file

{{< tabs >}}

  {{< tab name="CPU only" >}}
```yml
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # GPU version of ONNX runtime
      # This is for < CUDA 12.x
      # - onnxruntime-gpu==1.20.*

      # This is for CUDA 12.x
      - onnxruntime-gpu[cuda,cudnn]<1.27

      # This is for CUDA 13.x
      # - onnxruntime-gpu[cuda,cudnn]>=1.27

      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate korvatts
```

### Download weights

```bash
korvatts voices
```


## Step 3. Run the Inference

### Command Line Interface

Now, run the basic example command to synthesize speech:

```bash
korvatts synth "Xin chào, đây là KorvaTTS." -v khanh_vy -o hello.wav
```

The result will be the audio file `output.wav`


### Python Script

Create a file named `korva_test.py`:

```python
from korvatts import TTS

tts = TTS()  # first run downloads weights + voices from Hugging Face
print(tts.list_voices())

wav, duration = tts.synthesize(
    "Hôm nay team mình sẽ demo tính năng text-to-speech mới.",
    voice="khanh_vy",
    lang="vi",
    total_steps=32,  # default; best quality. Lower (8-16) for faster synthesis
    speed=1.05,      # default; 0.5 (slow) .. 2.0 (fast)
)
tts.save_audio(wav, "output.wav")
```

Run the script to convert text to speech:

```bash
python korva_test.py
```

The result will be the audio file `output.wav`


<!-- ### Web Demo (Gradio) -->


## Error and Warning

| Order | Type | Message (shortened) | Impact | Fix |
|---|------|---------------------|----------|-----|
| 1 | `UserWarning` (huggingface_hub) | `cache-system uses symlinks by default ... your machine does not support them` | Uses extra disk space only | Enable Developer Mode, or silence it with `setx HF_HUB_DISABLE_SYMLINKS_WARNING 1` |
| 2 | `Warning` (huggingface_hub) | `You are sending unauthenticated requests to the HF Hub. Please set a HF_TOKEN` | Slower downloads, rate limits | Create a Read token, then `setx HF_TOKEN hf_xxx` or `hf auth login` |

Notes
- Correction to my earlier advice: the newer Hugging Face login command is `hf auth login`, not `huggingface-cli login`.