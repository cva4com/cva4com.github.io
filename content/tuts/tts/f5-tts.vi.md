---
linkTitle: F5-TTS
title: Cài đặt SWivid/F5-TTS trên Windows bằng Conda
weight: 5
cascade:
  type: docs
tags:
  - TTS
  - F5-TTS
  - Open Weights
---

## Giới thiệu

Qwen3-TTS là một bộ mô hình chuyển văn bản thành giọng nói (TTS) mã nguồn mở được phát triển bởi nhóm Qwen tại Alibaba Cloud, hỗ trợ tạo giọng nói ổn định, biểu cảm và liên tục, thiết kế giọng nói tự do và sao chép giọng nói sống động.

GitHub: https://github.com/QwenLM/Qwen3-TTS  
Hugging Face: https://hf.co/collections/Qwen/qwen3-tts  
Demo: https://hf.co/spaces?q=Qwen3-TTS


## Yêu cầu hệ thống

*   **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
*   **Python:** Yêu cầu phiên bản 3.12
*   **Dung lượng ổ cứng:** Khuyến nghị 6GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
*   **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất
*   **Internet:** Để tải xuống các thư viện phụ thuộc và mô hình từ Hugging Face Hub.


| Environment | Run this Command |
| :-- | :-- |
| CPU only  | pip3 install torch torchaudio |
| CUDA 11.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu130 |

![PyTorch](/images/2026/pytorch.png)

Lưu ý: Kiểm tra phiên bản CUDA bằng lệnh

```bash
nvidia-smi
```

![PyTorch](/images/2026/nvidia-smi.png)


## Video hướng dẫn

{{< youtube nsYZWjd9I1Q >}}


## Bước 1. Cài đặt Miniconda

Tải xuống [Miniconda](https://cva4.com/tuts/tts/miniconda/): https://www.anaconda.com/download/success?reg=skipped

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


## Bước 2. Tạo môi trường Conda

Tạo tệp environment.yml:

```yml
name: f5-tts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.11

  # Install FFmpeg if you haven't yet
  - ffmpeg

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # --- CPU only ---
      # - torch
      # - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate f5-tts
```


## Bước 3. Chạy chương trình

### CLI Inference

Mẫu âm thanh tham khảo:

<audio controls>
  <source src="/audio/ref_audio.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

```bash
# Run with flags
# Leave --ref_text "" will have ASR model transcribe (extra GPU memory usage)
f5-tts_infer-cli --model F5TTS_v1_Base \
--ref_audio "D:\f5-tts\ref_audio.wav" \
--ref_text "The piper was very glad to see the pig and said to Tom" \
--gen_text "Some text you want TTS model generate for you."
```

Kết quả sẽ là tệp âm thanh `tests\infer_cli_basic.wav`


### Chạy app demo bằng Gradio (web interface)

```bash
# Launch a Gradio app (web interface)
f5-tts_infer-gradio
```

Starting app...
* Running on local URL:  http://127.0.0.1:7860

![F5-TTS](/images/2026/f5-tts.png)