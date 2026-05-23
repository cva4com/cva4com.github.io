---
linkTitle: Supertonic-3
title: Install Supertonic-3 TTS on Windows with Conda
weight: 6
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


## Video tutorial

{{< youtube hA6G0L_ebYs >}}


## Step 1. Install Miniconda Package

Download Miniconda: https://www.anaconda.com/download/success?reg=skipped

Direct link: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


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