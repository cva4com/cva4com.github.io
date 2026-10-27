---
linkTitle: Kokoro 82M
title: Cài đặt Kokoro 82M TTS bằng Conda
weight: 10
prev: /tts/tts-open-weights
# next: /tts/a
cascade:
  type: docs
tags:
  - TTS
  - Kokoro
  - Open Weights
---

## Giới thiệu

Kokoro là một mô hình TTS (Text-to-Speech) mã nguồn mở với 82 triệu tham số. Mặc dù có kiến ​​trúc nhẹ, nó mang lại chất lượng tương đương với các mô hình lớn hơn trong khi nhanh hơn và tiết kiệm chi phí hơn đáng kể. Với các tham số được cấp phép theo giấy phép Apache, Kokoro có thể được triển khai ở bất cứ đâu, từ môi trường sản xuất đến các dự án cá nhân.

GitHub: https://github.com/hexgrad/kokoro  
Hugging Face: https://hf.co/hexgrad/Kokoro-82M  
Demo: https://hf.co/spaces/hexgrad/Kokoro-TTS


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
* **Dung lượng ổ cứng:** Khuyến nghị 10GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất.
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
| Apple Silicon | pip3 install torch torchvision |
| AMD ROCm | [Install PyTorch for ROCm](https://rocm.docs.amd.com/projects/ai-ecosystem/en/latest/frameworks/pytorch/install.html) |
| CUDA 11.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118` |
| CUDA 12.1 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121` |
| CUDA 12.6 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126` |
| CUDA 12.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128` |
| CUDA 13.0 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130` |


## Video hướng dẫn

{{< youtube -VLmk9PqOYo >}}

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