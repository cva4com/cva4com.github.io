---
linkTitle: OmniVoice
title: Install OmniVoice TTS on Windows with Conda
weight: 6
cascade:
  type: docs
tags:
  - TTS
  - OmniVoice
  - Open Weights
---

## Introduction

OmniVoice is a state-of-the-art massively multilingual zero-shot text-to-speech (TTS) model supporting over 600 languages. Built on a novel diffusion language model-style architecture, it generates high-quality speech with superior inference speed, supporting voice cloning and voice design.

GitHub: https://github.com/k2-fsa/OmniVoice  
Hugging Face: https://hf.co/k2-fsa/OmniVoice  
Paper: https://arxiv.org/abs/2604.00688  
Demo: https://hf.co/spaces/k2-fsa/OmniVoice  
Audio Samples: Coming soon!  


## Prerequisites

System requirements:
*   **Operating System:** Windows 10/11 (64-bit), macOS, or Linux (Debian/Ubuntu).
*   **Python:** version >= 3.10 required
*   **Disk Space:** 10GB+ recommended (for dependencies and model cache). At least 400 MB for Miniconda; 3 GB+ for full Anaconda.
*   **The GPU** is optional but HIGHLY Recommended for Performance
*   **Internet:** For downloading dependencies and models from Hugging Face Hub.


| Environment | Run this Command |
| :-- | :-- |
| CPU only  | pip3 install torch torchvision |
| CUDA 11.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130 |

![PyTorch](/images/2026/pytorch.png)

Note: CUDA version check by command

```bash
nvidia-smi
```

![PyTorch](/images/2026/nvidia-smi.png)


## Video tutorial

{{< youtube 8h2ypng72nA >}}


## Step 1. Install Miniconda Package

Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Step 2. Create Conda Environment

Create a conda environment:

```yml
name: omnivoice
channels:
  - pytorch
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.10
  # Install FFmpeg for pydub audio library
  - ffmpeg
  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # OmniVoice-TTS
      - omnivoice
```

Activate conda environment:

```bash
conda env create -f environment.yml
conda activate omnivoice
```


## Step 3. Create a Python Script

Create a file named omnivoice_tts_test.py:

```python
from omnivoice import OmniVoice
import soundfile as sf
import torch

model = OmniVoice.from_pretrained(
    "k2-fsa/OmniVoice",
    device_map="cuda:0",
    dtype=torch.float16
)
# Apple Silicon users: use device_map="mps" instead
# Intel Arc GPU users: use device_map="xpu" instead

audio = model.generate(
    text="Hello, this is a test of zero-shot voice cloning.",
    # ref_audio="ref.wav",
    # ref_text="Transcription of the reference audio.",
    instruct="female, young adult, high pitch, british accent",
) # audio is a list of `np.ndarray` with shape (T,) at 24 kHz.

# If you don't want to input `ref_text` manually, you can directly omit the `ref_text`.
# The model will use Whisper ASR to auto-transcribe it.

sf.write("out.wav", audio[0], 24000)
```

Run it:

```bash
python omnivoice_tts_test.py
```

The result will be the audio file `out.wav`


### Launch the local web UI

Try OmniVoice without coding:

```bash
omnivoice-demo --ip 0.0.0.0 --port 8001
```

Open your browser and navigate to [http://127.0.0.1:8001](http://127.0.0.1:8001). The system will automatically download the required model weights from HuggingFace during this first run.