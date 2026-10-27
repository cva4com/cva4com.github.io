---
linkTitle: F5-TTS
title: Install SWivid/F5-TTS with Conda
weight: 7
cascade:
  type: docs
tags:
  - TTS
  - F5-TTS
  - Open Weights
---

## Introduction

F5-TTS is a flow matching-based text-to-speech synthesis system that generates high-quality speech from text input. The system implements Conditional Flow Matching (CFM) with transformer-based architectures to produce natural-sounding speech with voice cloning capabilities.

| Model | Architecture | Backbone | Description |
| :-- | :-- | :-- | :-- |
| F5-TTS | Diffusion Transformer | `DiT`, `MMDiT` | ConvNeXt V2-based, optimized for speed |
| E2-TTS | Flat-UNet Transformer | `UNetT` | Faithful reproduction of E2-TTS paper |

GitHub: https://github.com/swivid/f5-tts  
Hugging Face: https://hf.co/SWivid/F5-TTS  
Paper: https://hf.co/papers/2410.06885  
Demo: https://hf.co/spaces/mrfakename/E2-F5-TTS


## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** Version >=3.10 required
*   **Disk Space:** 6GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
*   **The GPU** is optional but HIGHLY Recommended for Performance
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
| CPU only  | pip3 install torch torchaudio |
| CUDA 11.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu130 |


## Video tutorial

{{< youtube nsYZWjd9I1Q >}}


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

{{< tabs >}}

  {{< tab name="CPU only" >}}
```yml
name: f5-tts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.11

  # Install FFmpeg if you haven't yet
  - ffmpeg

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: f5-tts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.11

  # Install FFmpeg if you haven't yet
  - ffmpeg

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: f5-tts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.11

  # Install FFmpeg if you haven't yet
  - ffmpeg

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate f5-tts
```


## Step 3. Run the Inference

### CLI Inference

Reference audio sample voice:

<audio controls>
  <source src="/audio/ref_audio.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

```bash
# Run with flags
# Leave --ref_text "" will have ASR model transcribe (extra GPU memory usage)
f5-tts_infer-cli --model F5TTS_v1_Base \
--ref_audio "D:\f5-tts\ref_audio.wav" \
--ref_text "The piper was very glad to see the pig and said to Tom" \
--gen_text "Some text you want TTS model generate for you."
```

The result will be the audio file `tests\infer_cli_basic.wav`


### Gradio app (web interface)

```bash
# Launch a Gradio app (web interface)
f5-tts_infer-gradio
```

Starting app...
* Running on local URL:  http://127.0.0.1:7860

![F5-TTS](/images/2026/f5-tts.png)