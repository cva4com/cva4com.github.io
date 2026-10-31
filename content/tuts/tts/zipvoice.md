---
linkTitle: ZipVoice
title: Install ZipVoice TTS with Conda
weight: 17
cascade:
  type: docs
tags:
  - TTS
  - ZipVoice
  - Open Weights
---

## Introduction

ZipVoice is a series of fast and high-quality zero-shot TTS models based on flow matching.

GitHub: https://github.com/k2-fsa/ZipVoice  
ONNX: https://github.com/thewh1teagle/zipvoice-onnx  
Hugging Face: https://hf.co/k2-fsa/ZipVoice  
Demo: https://zipvoice.github.io  
Paper: https://arxiv.org/abs/2506.13053  
Audio Samples: https://zipvoice.github.io  


## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** version >= 3.10 required
*   **Disk Space:** 10GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
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
| CPU only  | `pip3 install torch torchvision` |
| Apple Silicon | `pip3 install torch torchvision` |
| AMD ROCm | [Install PyTorch for ROCm](https://rocm.docs.amd.com/projects/ai-ecosystem/en/latest/frameworks/pytorch/install.html) |
| CUDA 11.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118` |
| CUDA 12.1 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121` |
| CUDA 12.6 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126` |
| CUDA 12.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128` |
| CUDA 13.0 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130` |


## Video tutorial

{{< youtube 0w1seD5rypo >}}


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
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate zipvoice
```

Clone and install ZipVoice from source (run after activating the environment)

```bash
git clone https://github.com/k2-fsa/ZipVoice.git
cd ZipVoice
```

Download the reference audio

```bash
curl -L -O "http://cva4.com/audio/prompt_english_female1.wav"
```

Reference audio sample voice: `prompt_english_female1.wav`

<audio controls>
  <source src="/audio/prompt_english_female1.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

**Note**: `RuntimeWarning: Couldn't find ffmpeg or avconv - defaulting to ffmpeg, but may not work` can be safely ignored if you only work with WAV audio files, as Pydub supports reading and writing WAV files natively without FFmpeg. However, FFmpeg is required for processing other audio formats such as MP3, OGG, and FLAC, as well as for audio format conversion.


## Step 3. Run the Inference

Inference of a single sentence

```bash
python -m zipvoice.bin.infer_zipvoice --model-name zipvoice --prompt-wav prompt_english_female1.wav --prompt-text "In order to win, you must expect to win." --text "I am the text to be synthesized." --res-wav-path result.wav
```

The result will be the audio file `result.wav`


## Install k2 for training or efficient inference

**k2 is necessary for training** and can speed up inference. Nevertheless, you can still use the inference mode of ZipVoice without installing k2.

> **Note:**  Make sure to install the k2 version that matches your PyTorch and CUDA version. For example, if you are using pytorch 2.5.1 and CUDA 12.1, you can install k2 as follows:

```bash
pip install k2==1.24.4.dev20250208+cuda12.1.torch2.5.1 -f https://k2-fsa.github.io/k2/cuda.html
```

Please refer to https://k2-fsa.org/get-started/k2/ for details.
Users in China mainland can refer to https://k2-fsa.org/zh-CN/get-started/k2/.

- To check the k2 installation:

```bash
python3 -c "import k2; print(k2.__file__)"
```