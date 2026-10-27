---
linkTitle: Qwen3-TTS
title: Cài đặt Qwen3-TTS bằng Conda
weight: 13
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


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản 3.12
* **Dung lượng ổ cứng:** Khuyến nghị 10GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất
* **Internet:** Để tải xuống các thư viện phụ thuộc và mô hình từ Hugging Face Hub.

{{< tabs >}}

  {{< tab name="CPU only" >}}
| Mức yêu cầu | CPU | RAM |
| :--- | :--- | :--- |
| Tối thiểu | Intel Core i3 hoặc AMD Ryzen 3 | 8 GB |
| Khuyến nghị | Intel Core i5 hoặc AMD Ryzen 5 | 16 GB |
| Hiệu năng cao | Intel Core i7/i9 hoặc AMD Ryzen 7/9 | 32 GB |
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
[Install PyTorch for NVIDIA](https://pytorch.org/get-started/locally/)
![PyTorch](/images/2026/pytorch.png)

Lưu ý: Kiểm tra phiên bản CUDA bằng lệnh

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
PyTorch có thể được cài đặt và sử dụng trên macOS. Tùy thuộc vào hệ thống và khả năng của GPU, trải nghiệm của bạn khi sử dụng PyTorch trên macOS có thể khác biệt về thời gian xử lý.
  {{< /tab >}}

{{< /tabs >}}

| Environment | Run this Command |
| :-- | :-- |
| CPU only  | pip3 install torch torchvision |
| CUDA 11.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130 |


## Video hướng dẫn

{{< youtube a00--jPR9Ns >}}


## Bước 1. Cài đặt Miniconda

{{< tabs >}}

  {{< tab name="Windows" >}}
Tải xuống Miniconda: https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe  
Liên kết trực tiếp: https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-arm64.exe

> Cài đặt [Miniconda trên Windows](https://cva4.com/vi/tuts/tts/miniconda/)
  {{< /tab >}}

  {{< tab name="Mac" >}}
Tải xuống Miniconda: https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-MacOSX-arm64.pkg

> Cài đặt [Miniconda trên MacOS](https://cva4.com/vi/tuts/tts/miniconda/#c%c3%a0i-%c4%91%e1%ba%b7t-tr%c3%aan-macoslinux)
  {{< /tab >}}

  {{< tab name="Linux" >}}
Tải xuống Miniconda: https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh  
Liên kết trực tiếp: https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh

> Cài đặt [Miniconda trên Linux](https://cva4.com/vi/tuts/tts/miniconda/#c%c3%a0i-%c4%91%e1%ba%b7t-tr%c3%aan-macoslinux)
  {{< /tab >}}

{{< /tabs >}}


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

{{< tabs >}}

  {{< tab name="CPU only" >}}
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
      # PyTorch CPU only
      - torch
      - torchvision
      - torchaudio

      # Qwen3-TTS
      - qwen-tts

      # Read/write audio files
      - soundfile

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub[cli]
      - modelscope
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
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

      # Read/write audio files
      - soundfile

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub[cli]
      - modelscope
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
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
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchvision
      - torchaudio

      # Qwen3-TTS
      - qwen-tts

      # Read/write audio files
      - soundfile

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub[cli]
      - modelscope
```
  {{< /tab >}}

{{< /tabs >}}


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

Kết quả sẽ là tệp âm thanh `output.wav`


## Âm thanh mẫu

| Speaker | Voice Description  |  Native language |
| --- | --- | --- |
| Vivian | Giọng nữ trẻ trung, sáng sủa, hơi cá tính. | Tiếng Trung |
| Serena | Giọng nữ trẻ trung, ấm áp, dịu dàng. | Tiếng Trung |
| Uncle_Fu | Giọng nam dày dặn kinh nghiệm với âm sắc trầm ấm. | Tiếng Trung |
| Dylan | Giọng nam trẻ trung đến từ Bắc Kinh với âm sắc trong trẻo, tự nhiên. | Tiếng Trung (Bắc Kinh) |
| Eric | Giọng nam sôi nổi đến từ Thành Đô với độ sáng hơi khàn. | Tiếng Trung (Tứ Xuyên) |
| Ryan | Giọng nam năng động với nhịp điệu mạnh mẽ. | Tiếng Anh |
| Aiden | Giọng nam Mỹ tươi sáng với âm vực trung rõ ràng. | Tiếng Anh |
| Ono_Anna | Giọng nữ Nhật Bản tinh nghịch với âm sắc nhẹ nhàng, linh hoạt. | Tiếng Nhật |
| Sohee | Giọng nữ Hàn Quốc ấm áp với nhiều cảm xúc. | Tiếng Hàn |