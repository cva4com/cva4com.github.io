---
linkTitle: NeuTTS
title: Install Neu TTS with Conda
weight: 11
cascade:
  type: docs
tags:
  - TTS
  - Neu
  - Open Weights
---

## Introduction

State-of-the-art Voice AI has been locked behind web APIs for too long. NeuTTS is a collection of open source, on-device, TTS speech language models with instant voice cloning. Built off of LLM backbones, NeuTTS brings natural-sounding speech, real-time performance, built-in security and speaker cloning to your local device - unlocking a new category of embedded voice agents, assistants, toys, and compliance-safe apps.

GitHub: https://github.com/neuphonic/neutts  
Hugging Face: https://hf.co/neuphonic/neutts-air  
Demo: https://hf.co/neuphonic/spaces  

Key Features

- 🗣Best-in-class realism for their size - produce natural, ultra-realistic voices that sound human, at the sweet spot between speed, size, and quality for real-world applications
- 📱Optimised for on-device deployment - quantisations provided in GGUF format, ready to run on phones, laptops, or even Raspberry Pis
- 👫Instant voice cloning - create your own speaker with as little as 3 seconds of audio
- 🚄Simple LM + codec architecture - making development and deployment simple

## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** version >= 3.10 required
*   **Disk Space:** 4GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
*   **The GPU** is optional. It runs smoothly on a laptop CPU.
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

<!-- Coming soon! -->
{{< youtube dreLvnl678M >}}


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
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch CPU only. It runs smoothly on a laptop CPU.
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch CUDA is optional. It runs smoothly on a laptop CPU.
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate neutts
```

Clone NeuTTS from source (run after activating the environment)

```bash
git clone https://github.com/neuphonic/neutts.git
cd neutts
```

The reference audio
https://github.com/neuphonic/neutts/tree/main/samples


## Step 3. Access to model

Request Access on the Hugging Face Website. Because this model has restricted access, you must manually accept its terms first:

1. Log in to your Hugging Face account in your browser.
2. Go directly to the model page of NeuTTS Nano and NeuCodec:
   - https://huggingface.co/neuphonic/neutts-nano
   - https://huggingface.co/neuphonic/neucodec
3. Fill out any required information and click the `Agree and access repository` button.
4. Generate a token with `Read` permissions by going to your Hugging Face **Settings > Access Tokens**.
5. Open your terminal and run: `hf auth login`
   The CLI will prompt you in one of two ways:
   - Login with your browser
   - Paste an Access Token
6. Select the first option. The CLI will display a short code and ask you to open a URL (https://huggingface.co/oauth/device). Paste the code into your browser window to instantly approve the login.
7. Select the second option. Paste your token when prompted and hit Enter.

Note: Your request to access this repository has been submitted and is awaiting a review from the repository authors. You can check the status of all your access requests in [your settings](https://huggingface.co/settings/gated-repos).

## Step 4. Run the Inference

Now, run the basic example script to synthesize speech:

```bash
python -m examples.basic_example --input_text "My name is Sophie. I'm 25 and I just moved to London." --ref_audio samples/sophie.wav --ref_text samples/sophie.txt
```

The result will be the audio file `output.wav`


### One-Code Block Usage

```python
from neutts import NeuTTS
import soundfile as sf

tts = NeuTTS(
   backbone_repo="neuphonic/neutts-nano", # or 'neuphonic/neutts-nano-q4-gguf' with llama-cpp-python installed
   backbone_device="cpu",
   codec_repo="neuphonic/neucodec",
   codec_device="cpu"
)
input_text = "My name is Andy. I'm 25 and I just moved to London. The underground is pretty confusing, but it gets me around in no time at all."

ref_text = "samples/jo.txt"
ref_audio_path = "samples/jo.wav"

ref_text = open(ref_text, "r").read().strip()
ref_codes = tts.encode_reference(ref_audio_path)

wav = tts.infer(input_text, ref_codes, ref_text)
sf.write("test.wav", wav, 24000)
```