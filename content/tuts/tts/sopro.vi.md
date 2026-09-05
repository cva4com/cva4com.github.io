---
linkTitle: SoproTTS
title: Cài đặt Nari SoproTTS trên Windows bằng Conda
weight: 10
cascade:
  type: docs
tags:
  - TTS
  - Sopro
  - Open Weights
---

## Giới thiệu

Sopro (bắt nguồn từ từ "hơi thở/luồng hơi" trong tiếng Bồ Đào Nha) là một dòng mô hình chuyển đổi văn bản thành giọng nói (TTS) có khả năng sao chép giọng nói và sở hữu trọng lượng nhẹ. Kho lưu trữ này cung cấp **sopro-v2-turbo** – một mô hình mã nguồn mở với 120 triệu tham số, hỗ trợ xử lý luồng (streaming), vận hành mượt mà trên CPU máy tính xách tay hoặc ngay trong trình duyệt, đồng thời đạt chất lượng độ rõ nét ngang tầm các hệ thống lớn hơn nhiều (đạt chuẩn SOTA).

GitHub: https://github.com/samuel-vitorino/sopro  
Hugging Face: https://hf.co/samuel-vitorino/sopro-v2-turbo  
Demo: https://hf.co/spaces/samuel-vitorino/sopro-v2-turbo-tts  
Example: https://samuel-vitorino.github.io/sopro/  

Các tính năng chính:

- **120 triệu tham số**
- **Hỗ trợ tiếng Anh, tiếng Bồ Đào Nha (châu Âu), tiếng Pháp và tiếng Đức**
- **Phát trực tuyến (streaming)** với thời gian tạo đoạn âm thanh đầu tiên khoảng 300 ms trên CPU máy tính xách tay
- **Sao chép giọng nói "zero-shot"** (không cần huấn luyện thêm) từ 5-20 giây âm thanh tham chiếu
- **Tốc độ xử lý (RTF): 0,24 (ngoại tuyến) / 0,21 (trực tuyến)** trên CPU M3; **0,07** trên GPU H100
- **Chạy trực tiếp trên trình duyệt** thông qua môi trường thực thi ONNX (ONNX runtime)


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
* **Dung lượng ổ cứng:** Khuyến nghị 4GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn. Nó chạy mượt mà trên CPU của máy tính xách tay.
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
<!-- {{< youtube FWFvAXpiaAM >}} -->


## Bước 1. Cài đặt Miniconda

Tải xuống [Miniconda](https://cva4.com/tuts/tts/miniconda/): https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe

> Cài đặt [Miniconda trên Windows](https://cva4.com/tuts/tts/miniconda/)


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

```yml
name: soprotts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch CUDA is optional. It runs smoothly on a laptop CPU.
      # - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Install SoproTTS directly from GitHub.
      - git+https://github.com/samuel-vitorino/sopro.git
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate soprotts
```

Tải xuống bản ghi âm tham khảo

```bash
curl -L -O "https://github.com/thewh1teagle/zipvoice-onnx/releases/download/model-files-v1.0/prompt_english_female1.wav"
```

Mẫu âm thanh tham khảo:  `prompt_english_female1.wav`

<audio controls>
  <source src="/audio/prompt_english_female1.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>


## Bước 3. Chạy suy luận

Bây giờ, hãy chạy thử một vài ví dụ.

```bash
soprotts "Sopro is a lightweight 120 million parameter text-to-speech model that streams and runs on device." --ref prompt_english_female1.wav --out out.wav
```

Kết quả sẽ là tệp âm thanh `out.wav`


### Khởi chạy Giao diện Web (Gradio Web UI)

Sau khi cài đặt xong, bạn có thể chạy mô hình và mở bản demo bằng một lệnh duy nhất:

```bash
soprotts serve
```

Mở trình duyệt và truy cập vào địa chỉ [http://127.0.0.1:7860](http://127.0.0.1:7860) để bắt đầu sử dụng. Hệ thống sẽ tự động tải các file Model (Trọng số cấu hình mã nguồn) từ HuggingFace trong lần đầu chạy.