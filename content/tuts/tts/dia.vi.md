---
linkTitle: Dia
title: Cài đặt Nari Dia trên Windows bằng Conda
weight: 4
cascade:
  type: docs
tags:
  - TTS
  - Dia
  - Open Weights
---

## Giới thiệu

Dia là một mô hình chuyển văn bản thành giọng nói với 1,6 tỷ tham số được tạo ra bởi Nari Labs. Dia có khả năng tạo ra các đoạn hội thoại cực kỳ chân thực chỉ trong một lần xử lý.

GitHub: https://github.com/nari-labs/dia  
Hugging Face: https://hf.co/nari-labs/Dia-1.6B-0626  
Demo: https://hf.co/spaces/nari-labs/Dia-1.6B  


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

Sắp ra mắt!
<!-- {{< youtube 0w1seD5rypo >}} -->


## Bước 1. Cài đặt Miniconda

Tải xuống [Miniconda](https://cva4.com/tuts/tts/miniconda/): https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

```yml
name: dia
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Nari TTS Install Dia directly from GitHub.
      - git+https://github.com/nari-labs/dia.git
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate dia
```

Clone và cài Dia từ source (chạy sau khi kích hoạt môi trường)

```bash
git clone https://github.com/nari-labs/dia.git
cd dia
```


## Bước 3. Chạy chương trình

Bây giờ, hãy chạy thử một vài ví dụ.

```bash
python example/simple.py
```

```bash
generate: starting generation loop
generate step 86: speed=1.168 tokens/s, realtime factor=0.014x
generate step 172: speed=1.192 tokens/s, realtime factor=0.014x
generate step 258: speed=1.221 tokens/s, realtime factor=0.014x
generate step 344: speed=1.141 tokens/s, realtime factor=0.013x
generate step 430: speed=1.156 tokens/s, realtime factor=0.013x
generate step 516: speed=1.067 tokens/s, realtime factor=0.012x
generate step 602: speed=1.092 tokens/s, realtime factor=0.013x
generate step 688: speed=1.112 tokens/s, realtime factor=0.013x
generate step 774: speed=1.113 tokens/s, realtime factor=0.013x
generate: avg steps=831.0, total duration=751.395s
```

Kết quả sẽ là tệp âm thanh `simple.wav`


### Khởi chạy Giao diện Web (Gradio Web UI)

Sau khi cài đặt xong, bạn không cần viết code mà có thể bật ngay một giao diện Web UI cục bộ bằng lệnh:

```bash
python app.py
```

Mở trình duyệt và truy cập vào địa chỉ [http://127.0.0.1:7860](http://127.0.0.1:7860) để bắt đầu sử dụng. Hệ thống sẽ tự động tải các file Model (Trọng số cấu hình mã nguồn) từ HuggingFace trong lần đầu chạy.