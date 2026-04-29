---
linkTitle: Kokoro 82M
title: Cài đặt Kokoro 82M TTS trên Windows bằng Conda
weight: 2
prev: /tts/
# next: /tts/a
cascade:
  type: docs
tags:
  - TTS
  - Kokoro
  - Open Weights
---

## Video hướng dẫn

{{< youtube -VLmk9PqOYo >}}

## Bước 1. Cài đặt Miniconda

Tải xuống Miniconda: https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Bước 2. Cài đặt eSpeak NG

Thư viện `espeak-ng` (Bắt buộc đối với Windows) cần  để chuyển đổi văn bản thành âm vị. Trên Windows:

1. Truy cập [espeak-ng releases](https://github.com/espeak-ng/espeak-ng/releases)
2. Nhấp vào [Bản phát hành mới nhất](https://github.com/espeak-ng/espeak-ng/releases/latest)
3. Tải xuống tệp .msi phù hợp (ví dụ: espeak-ng.msi)
4. Chạy trình cài đặt đã tải xuống
5. Làm theo hướng dẫn của trình hướng dẫn cài đặt

Để biết cấu hình chi tiết cho Windows, hãy xem [hướng dẫn chính thức của espeak-ng dành cho Windows](https://github.com/espeak-ng/espeak-ng/blob/master/docs/guide.md)


## Bước 3. Tạo môi trường Conda

Tạo tệp environment.yml:

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

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate kokoro
```


## Bước 4. Tạo một tệp Python

Tạo một tệp có tên kokoro_test.py:

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

Chạy thử:

```bash
python kokoro_test.py
```

Kết quả sẽ là tệp âm thanh `output_0.wav`