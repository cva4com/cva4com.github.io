---
linkTitle: VoxCPM2
title: Cài đặt VoxCPM2 trên Windows bằng Conda
weight: 9
cascade:
  type: docs
tags:
  - TTS
  - VoxCPM2
  - Open Weights
---

## Giới thiệu

VoxCPM2 là một công cụ chuyển văn bản thành giọng nói (TTS) không cần bộ mã hóa từ, hỗ trợ tạo giọng nói đa ngôn ngữ, thiết kế giọng nói sáng tạo và sao chép giọng nói chân thực.

GitHub: https://github.com/OpenBMB/VoxCPM  
Hugging Face: https://hf.co/openbmb/VoxCPM2  
Demo: https://hf.co/spaces/openbmb/VoxCPM-Demo  
Docs: https://voxcpm.readthedocs.io/en/latest/  
Audio Samples: https://openbmb.github.io/voxcpm2-demopage/  


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
* **Dung lượng ổ cứng:** Khuyến nghị 10GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất
* **Internet:** Để tải xuống các thư viện phụ thuộc và mô hình từ Hugging Face Hub.


| Environment | Run this Command |
| :-- | :-- |
| CPU only  | pip3 install torch torchvision |
| CUDA 11.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130 |

![PyTorch](/images/2026/pytorch.png)

Lưu ý: Kiểm tra phiên bản CUDA bằng lệnh

```bash
nvidia-smi
```

![PyTorch](/images/2026/nvidia-smi.png)


## Video hướng dẫn

Đang cập nhật
<!-- {{< youtube 8h2ypng72nA >}} -->


## Bước 1. Cài đặt Miniconda

Tải xuống [Miniconda](https://cva4.com/tuts/tts/miniconda/): https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

```yml
name: voxcpm
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.10

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      # - --extra-index-url https://download.pytorch.org/whl/cu126
      # - torch
      # - torchaudio
      # - torchcodec

      # VoxCPM2: Tokenizer-Free TTS
      - voxcpm
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate voxcpm
```


## Bước 3. Tạo một tệp Python

Tạo một tệp có tên voxcpm_test.py:

```python
from voxcpm import VoxCPM
import soundfile as sf

model = VoxCPM.from_pretrained(
  "openbmb/VoxCPM2",
  load_denoiser=False,
)

wav = model.generate(
    text="VoxCPM2 is the current recommended release for realistic multilingual speech synthesis.",
    cfg_value=2.0,
    inference_timesteps=10,
)
sf.write("demo.wav", wav, model.tts_model.sample_rate)
print("saved: demo.wav")
```

Chạy thử:

```bash
python voxcpm_test.py
```

Kết quả sẽ là tệp âm thanh `demo.wav`


### Khởi chạy Giao diện Web (Gradio Web UI)

Sau khi cài đặt xong, bạn không cần viết code mà có thể bật ngay một giao diện Web UI cục bộ bằng lệnh:

```bash
python app.py --port 8808
```

Mở trình duyệt và truy cập vào địa chỉ [http://localhost:8808](http://localhost:8808) để bắt đầu sử dụng. Hệ thống sẽ tự động tải các file Model (Trọng số cấu hình mã nguồn) từ HuggingFace trong lần đầu chạy.

Lưu ý: Bạn có thể tải xuống tệp app.py [tại đây](https://github.com/OpenBMB/VoxCPM/blob/main/app.py).