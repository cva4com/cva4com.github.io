---
linkTitle: F5-TTS
title: Cài đặt SWivid/F5-TTS bằng Conda
weight: 7
cascade:
  type: docs
tags:
  - TTS
  - F5-TTS
  - Open Weights
---

## Giới thiệu

F5-TTS là một hệ thống tổng hợp giọng nói từ văn bản dựa trên phương pháp khớp luồng, tạo ra giọng nói chất lượng cao từ văn bản đầu vào. Hệ thống này triển khai phương pháp khớp luồng có điều kiện (Conditional Flow Matching - CFM) với kiến ​​trúc dựa trên bộ biến đổi để tạo ra giọng nói tự nhiên với khả năng sao chép giọng nói.

| Mô hình | Kiến trúc | Cấu trúc chính | Mô tả |
| :-- | :-- | :-- | :-- |
| F5-TTS | Bộ chuyển đổi khuếch tán | `DiT`, `MMDiT` | Dựa trên ConvNeXt V2, tối ưu hóa tốc độ |
| E2-TTS | Bộ chuyển đổi Flat-UNet | `UNetT` | Bản sao chính xác của bài báo E2-TTS |

GitHub: https://github.com/swivid/f5-tts  
Hugging Face: https://hf.co/SWivid/F5-TTS  
Paper: https://hf.co/papers/2410.06885  
Demo: https://hf.co/spaces/mrfakename/E2-F5-TTS


## Yêu cầu hệ thống

*   **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
*   **Python:** Yêu cầu phiên bản 3.12
*   **Dung lượng ổ cứng:** Khuyến nghị 6GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
*   **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất
*   **Internet:** Để tải xuống các thư viện phụ thuộc và mô hình từ Hugging Face Hub.

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
| CPU only  | pip3 install torch torchaudio |
| CUDA 11.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchaudio --index-url https://download.pytorch.org/whl/cu130 |


## Video hướng dẫn

{{< youtube nsYZWjd9I1Q >}}


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
      # PyTorch CPU only
      - torch
      - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
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

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
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
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Allow run Gradio app (web interface)
      - gradio

      # F5-TTS
      - f5-tts
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate f5-tts
```

**Lưu ý**: `RuntimeWarning: Couldn't find ffmpeg or avconv - defaulting to ffmpeg, but may not work` có thể được bỏ qua nếu bạn chỉ làm việc với các tệp âm thanh định dạng WAV, vì Pydub hỗ trợ đọc và ghi tệp WAV mà không cần đến FFmpeg. Tuy nhiên, FFmpeg là bắt buộc nếu bạn muốn xử lý các định dạng âm thanh khác như MP3, OGG, FLAC, hoặc thực hiện chuyển đổi định dạng âm thanh.


## Bước 3. Chạy suy luận

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