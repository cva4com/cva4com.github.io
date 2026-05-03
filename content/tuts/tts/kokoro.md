---
linkTitle: Kokoro 82M
title: Install Kokoro 82M TTS on Windows with Conda
weight: 3
prev: /tts/tts-open-weights
# next: /tts/a
cascade:
  type: docs
tags:
  - TTS
  - Kokoro
  - Open Weights
---

## Introduction

Kokoro is an open-weight TTS model with 82 million parameters. Despite its lightweight architecture, it delivers comparable quality to larger models while being significantly faster and more cost-efficient. With Apache-licensed weights, Kokoro can be deployed anywhere from production environments to personal projects.

GitHub: https://github.com/hexgrad/kokoro  
Hugging Face: https://hf.co/hexgrad/Kokoro-82M  
Demo: https://hf.co/spaces/hexgrad/Kokoro-TTS

## Video tutorial

{{< youtube -VLmk9PqOYo >}}

## Step 1. Install Miniconda Package

Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Step 2. Install eSpeak NG

The library needs `espeak-ng` (Required for Windows) for text-to-phoneme conversion. On Windows:

1. Go to [espeak-ng releases](https://github.com/espeak-ng/espeak-ng/releases)
2. Click on [Latest release](https://github.com/espeak-ng/espeak-ng/releases/latest)
3. Download the appropriate .msi file (e.g., espeak-ng.msi)
4. Run the downloaded installer
5. Follow the installation wizard

For detailed Windows configuration, see the [official espeak-ng Windows guide](https://github.com/espeak-ng/espeak-ng/blob/master/docs/guide.md)


## Step 3. Create Conda Environment

Create a conda environment:

```yml
name: kokoro
channels:
  - defaults
dependencies:
  - python==3.10
  - pip:
    - kokoro>=0.9.4
    - soundfile
    - misaki[en]
```

Activate conda environment:

```bash
conda env create -f environment.yml
conda activate kokoro
```


## Step 4. Create a Python Script

Create a file named kokoro_test.py:

```python
from kokoro import KPipeline
import soundfile as sf

# Initialize pipeline (American English)
pipeline = KPipeline(lang_code='a')

# Your text
text = "Hello, this is Kokoro text to speech on Windows!"

# Generate audio
generator = pipeline(text, voice='af_heart')

# Save audio files
for i, (gs, ps, audio) in enumerate(generator):
    print(f"Part {i}: {gs}")
    sf.write(f'output_{i}.wav', audio, 24000)
```

Run it:

```bash
python kokoro_test.py
```

The result will be the audio file `output_0.wav`