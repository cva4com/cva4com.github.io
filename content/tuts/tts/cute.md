---
linkTitle: CuteTTS
title: Install OPPO CuteTTS TTS with Conda
weight: 6
cascade:
  type: docs
tags:
  - TTS
  - OPPO
  - CuteTTS
  - Open Weights
params:
  tabs:
    sync: true
---

## Introduction

CuteTTS: a lightweight continuous autoregressive TTS model that runs efficiently on GPUs, CPUs, and Apple silicon.

GitHub: https://github.com/OPPO-Mente-Lab/CuteTTS  
Hugging Face: https://hf.co/OPPOer/CuteTTS  
Hugging Face: https://hf.co/OPPOer/CuteTTS-distill  
Demo: https://hf.co/spaces/hugging-apps/cutetts-demo  
Paper: https://arxiv.org/abs/2608.08638  

![CuteTTS](/images/2026/cute_backbone.png)

- A lightweight (~230M-parameter) continuous autoregressive TTS model that runs efficiently on GPUs, CPUs, and Apple silicon.
- Ultra-low latency: `~40 ms` to the first audio chunk and a throughput of ~9× real time on an NVIDIA RTX 4090.
- Excellent speech quality and voice cloning performance.
- Web demo, Python API, and CLI.
- Multilingual support: English, Chinese, French, German, and Spanish.


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

![CuteTTS](/images/2026/performance.svg)
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

Coming soon!
<!-- {{< youtube LXRTv9bbIXA >}} -->


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
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # This is the PyTorch CUDA 12.6 wheels.
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

{{< /tabs >}}


Activate conda environment:

```bash
conda env create -f environment.yml
conda activate cutetts
```

Clone and install CuteTTS from source (run after activating the environment)

```bash
git clone https://github.com/OPPO-Mente-Lab/CuteTTS.git
cd CuteTTS
```

### Download weights

Download [CuteTTS](https://huggingface.co/OPPOer/CuteTTS) or [CuteTTS-distill](https://huggingface.co/OPPOer/CuteTTS-distill) into `./model`:

```bash
# Create the model directory
mkdir model

# Download the CuteTTS model (or CuteTTS-distill for lower-end hardware)
hf download OPPOer/CuteTTS --local-dir ./model/CuteTTS
hf download OPPOer/CuteTTS-distill --local-dir ./model/CuteTTS-distill
```

### Directory structure

The expected directory structure is:

```
D:\cute\
├── CuteTTS\
│   ├── assets\
│   ├── LICENSES\
│   ├── model\
│   │   ├── CuteTTS\
│   │   └── CuteTTS-distill\
│   ├── src\
│   │   └── cutetts\
│   ├── .gitignore
│   ├── LICENSE
│   ├── NOTICE
│   ├── README.md
│   ├── README_zh.md
│   ├── infer.py
│   └── pyproject.toml
├── cute_test.py
└── environment.yml
```


## Step 3. Run the Inference

### Command line

```bash
# sanity check
cutetts --help
```

```bash
usage: cutetts [-h] --model-dir MODEL_DIR --text TEXT [--mode {tts,voice_clone}] [--reference-audio REFERENCE_AUDIO] [--output OUTPUT] [--device DEVICE] [--cfg-strength CFG_STRENGTH]
               [--diffusion-steps DIFFUSION_STEPS] [--diffusion-sway-coefficient DIFFUSION_SWAY_COEFFICIENT] [--max-decode-length MAX_DECODE_LENGTH] [--seed SEED] [--no-progress]

Generate speech with CuteTTS.

options:
  -h, --help            show this help message and exit
  --model-dir MODEL_DIR
  --text TEXT
  --mode {tts,voice_clone}
  --reference-audio REFERENCE_AUDIO
  --output OUTPUT
  --device DEVICE       Inference device: auto, cuda, mps, or cpu (default: auto).
  --cfg-strength CFG_STRENGTH
  --diffusion-steps DIFFUSION_STEPS
  --diffusion-sway-coefficient DIFFUSION_SWAY_COEFFICIENT
  --max-decode-length MAX_DECODE_LENGTH
  --seed SEED
  --no-progress
```

Now, run the basic example script to synthesize speech:

```bash
cutetts --model-dir ./model/CuteTTS --mode tts --text "The voice generated by this model sounds amazing!" --output tts.wav
```

The result will be the audio file `tts.wav`

**Test Voice Cloning**

```bash
cutetts --model-dir ./model/CuteTTS --mode voice_clone --reference-audio ./assets/default_reference.wav --text "The voice generated by this model sounds amazing!" --output clone.wav
```


### Python Script

Create a file named `cute_test.py`:

```python
from cutetts import CuteTTS
import soundfile as sf

model = CuteTTS.from_pretrained("./CuteTTS/model/CuteTTS", device="auto")
result = model.generate("The voice generated by this model sounds amazing!", mode="tts")
sf.write("tts.wav", result.waveform.squeeze(0).numpy(), result.sample_rate)

clone = model.generate(
    "The voice generated by this model sounds amazing!",
    mode="voice_clone",
    reference_audio="./CuteTTS/assets/default_reference.wav",
)
sf.write("clone.wav", clone.waveform.squeeze(0).numpy(), clone.sample_rate)
```

Run the script to clone voice:

```bash
python cute_test.py
```

The result will be the audio file `clone.wav`

<!-- **Streaming Python API** -->


### Web demo

Try CuteTTS without coding:

```bash
cutetts-demo --model-dir ./model --device auto --host 127.0.0.1 --port 7860
```

Open your browser and navigate to [http://127.0.0.1:7860](http://127.0.0.1:7860). The system will automatically download the required model weights from HuggingFace during this first run.
