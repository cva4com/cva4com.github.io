---
linkTitle: ZipVoice
title: Cài đặt ZipVoice bằng Conda
weight: 17
cascade:
  type: docs
tags:
  - TTS
  - ZipVoice
  - Open Weights
---

## Giới thiệu

ZipVoice là một loạt các mô hình chuyển văn bản thành giọng nói (TTS) nhanh và chất lượng cao dựa trên nguyên tắc khớp luồng âm thanh.

GitHub: https://github.com/k2-fsa/ZipVoice  
ONNX: https://github.com/thewh1teagle/zipvoice-onnx  
Hugging Face: https://hf.co/k2-fsa/ZipVoice  
Demo: https://zipvoice.github.io  
Paper: https://arxiv.org/abs/2506.13053  
Audio Samples: https://zipvoice.github.io  


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
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
| CUDA 11.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118` |
| CUDA 12.1 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121` |
| CUDA 12.6 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126` |
| CUDA 12.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128` |
| CUDA 13.0 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130` |


## Video hướng dẫn

{{< youtube 0w1seD5rypo >}}


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
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch CUDA 12.6 wheels
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: zipvoice
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version
  - python=3.11

  # Install FFmpeg for torchaudio library
  - ffmpeg

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio
      - torchcodec

      # Core dependencies
      - numpy
      - lhotse
      - huggingface_hub
      - safetensors
      - urllib3
      - tensorboard
      - vocos
      - pydub

      # Normalization
      - cn2an
      - inflect

      # Tokenization
      - jieba
      - pypinyin

      # piper_phonemize wheel cho Windows
      - --find-links https://k2-fsa.github.io/icefall/piper_phonemize.html
      - piper_phonemize

      # Pin setuptools to avoid build errors with older packages
      - "setuptools<81"
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate zipvoice
```

Clone và cài ZipVoice từ source (chạy sau khi kích hoạt môi trường)

```bash
git clone https://github.com/k2-fsa/ZipVoice.git
cd ZipVoice
```

Tải xuống bản ghi âm tham khảo

```bash
curl -L -O "http://cva4.com/audio/prompt_english_female1.wav"
```

Mẫu âm thanh tham khảo: `prompt_english_female1.wav`

<audio controls>
  <source src="/audio/prompt_english_female1.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

**Lưu ý**: `RuntimeWarning: Couldn't find ffmpeg or avconv - defaulting to ffmpeg, but may not work` có thể được bỏ qua nếu bạn chỉ làm việc với các tệp âm thanh định dạng WAV, vì Pydub hỗ trợ đọc và ghi tệp WAV mà không cần đến FFmpeg. Tuy nhiên, FFmpeg là bắt buộc nếu bạn muốn xử lý các định dạng âm thanh khác như MP3, OGG, FLAC, hoặc thực hiện chuyển đổi định dạng âm thanh.


## Bước 3. Chạy suy luận

Chạy ZipVoice Single-speaker

```bash
python -m zipvoice.bin.infer_zipvoice --model-name zipvoice --prompt-wav prompt_english_female1.wav --prompt-text "In order to win, you must expect to win." --text "I am the text to be synthesized." --res-wav-path result.wav
```

Kết quả sẽ là tệp âm thanh `result.wav`


## Cài đặt k2 để huấn luyện hoặc suy luận hiệu quả

**k2 cần thiết cho việc huấn luyện** và có thể tăng tốc quá trình suy luận. Tuy nhiên, bạn vẫn có thể sử dụng chế độ suy luận của ZipVoice mà không cần cài đặt k2.

> **Lưu ý:**  Hãy chắc chắn cài đặt phiên bản k2 phù hợp với phiên bản PyTorch và CUDA của bạn. Ví dụ, nếu bạn đang sử dụng pytorch 2.5.1 và CUDA 12.1, bạn có thể cài đặt k2 như sau:

```bash
pip install k2==1.24.4.dev20250208+cuda12.1.torch2.5.1 -f https://k2-fsa.github.io/k2/cuda.html
```

Vui lòng tham khảo https://k2-fsa.org/get-started/k2/ để biết thêm chi tiết.  
Người dùng tại Trung Quốc đại lục có thể tham khảo https://k2-fsa.org/zh-CN/get-started/k2/.

- Để kiểm tra cài đặt k2:

```bash
python3 -c "import k2; print(k2.__file__)"
```