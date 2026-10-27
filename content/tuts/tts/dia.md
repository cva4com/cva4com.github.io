---
linkTitle: Dia
title: Install Nari Dia TTS with Conda
weight: 6
cascade:
  type: docs
tags:
  - TTS
  - Dia
  - Open Weights
---

## Introduction

Dia is a 1.6B parameter text to speech model created by Nari Labs. Dia capable of generating ultra-realistic dialogue in one pass. 

GitHub: https://github.com/nari-labs/dia  
Hugging Face: https://hf.co/nari-labs/Dia-1.6B-0626  
Demo: https://hf.co/spaces/nari-labs/Dia-1.6B  
Example: https://yummy-fir-7a4.notion.site/dia  


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
| CPU only  | pip3 install torch torchvision |
| CUDA 11.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118` |
| CUDA 12.1 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121` |
| CUDA 12.6 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126` |
| CUDA 12.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128` |
| CUDA 13.0 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130` |


## Video tutorial

{{< youtube FWFvAXpiaAM >}}


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
name: dia
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio

      # Nari TTS Install Dia directly from GitHub.
      - git+https://github.com/nari-labs/dia.git
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: dia
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Nari TTS Install Dia directly from GitHub.
      - git+https://github.com/nari-labs/dia.git
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: dia
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Nari TTS Install Dia directly from GitHub.
      - git+https://github.com/nari-labs/dia.git
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate dia
```

Clone and install Dia from source (run after activating the environment)

```bash
git clone https://github.com/nari-labs/dia.git
cd dia
```


## Step 3. Run the Inference

Now, run some examples.

```bash
python example/simple.py
```

```bash
generate: starting generation loop
generate step 86: speed=1.168 tokens/s, realtime factor=0.014x
generate step 172: speed=1.192 tokens/s, realtime factor=0.014x
generate step 258: speed=1.221 tokens/s, realtime factor=0.014x
generate step 344: speed=1.141 tokens/s, realtime factor=0.013x
generate step 430: speed=1.156 tokens/s, realtime factor=0.013x
generate step 516: speed=1.067 tokens/s, realtime factor=0.012x
generate step 602: speed=1.092 tokens/s, realtime factor=0.013x
generate step 688: speed=1.112 tokens/s, realtime factor=0.013x
generate step 774: speed=1.113 tokens/s, realtime factor=0.013x
generate: avg steps=831.0, total duration=751.395s
```

The result will be the audio file `simple.mp3`


### Gradio app (web interface)

Try Dia without coding:

```bash
python app.py
```

Open your browser and navigate to [http://127.0.0.1:7860](http://127.0.0.1:7860). The system will automatically download the required model weights from HuggingFace during this first run.