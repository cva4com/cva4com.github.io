---
linkTitle: Qwen3-TTS
title: Cài đặt Qwen3-TTS trên Windows bằng Conda
weight: 4
# prev: /tts/tts-open-weights
# next: /tts/a
cascade:
  type: docs
tags:
  - TTS
  - Qwen3-TTS
  - Open Weights
---

## Giới thiệu

Qwen3-TTS là một bộ mô hình chuyển văn bản thành giọng nói (TTS) mã nguồn mở được phát triển bởi nhóm Qwen tại Alibaba Cloud, hỗ trợ tạo giọng nói ổn định, biểu cảm và liên tục, thiết kế giọng nói tự do và sao chép giọng nói sống động.

GitHub: https://github.com/QwenLM/Qwen3-TTS  
Hugging Face: https://hf.co/collections/Qwen/qwen3-tts  
Demo: https://hf.co/spaces?q=Qwen3-TTS


## Video hướng dẫn

Sắp ra mắt
<!-- {{< youtube -VLmk9PqOYo >}} -->

## Bước 1. Cài đặt Miniconda

Tải xuống Miniconda: https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

```yml
name: qwen3-tts
channels:
  - pytorch
  - nvidia
  - defaults
dependencies:
  - python=3.12
  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchvision
      - torchaudio

      # Qwen3-TTS
      - qwen-tts

      # Đọc/ghi file âm thanh
      - soundfile

      # Tải model từ Hugging Face / ModelScope
      - huggingface_hub[cli]
      - modelscope
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate qwen3-tts
```


## Bước 3. Tạo một tệp Python

Tạo một tệp có tên qwen3_tts_test.py:

```python
import torch
import soundfile as sf
from qwen_tts import Qwen3TTSModel

# Use float16 instead of bfloat16 if your older GPU doesn't support bfloat16.
model = Qwen3TTSModel.from_pretrained(
    "Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice",
    device_map="cuda:0",
    dtype=torch.bfloat16,
    # Do not use attn_implementation="flash_attention_2" on Windows.
    #attn_implementation="flash_attention_2",
)

# single inference
wavs, sr = model.generate_custom_voice(
    text="Hello, this is a test.",
    language="English",
    speaker="Ryan",
)

sf.write("output.wav", wavs[0], sr)
print("output.wav has been saved!")
```

Chạy thử:

```bash
python qwen3_tts_test.py
```

Kết quả sẽ là tệp âm thanh output.wav`