---
linkTitle: Supertonic-3
title: Cài đặt Supertonic-3 bằng Conda
weight: 15
cascade:
  type: docs
tags:
  - TTS
  - Supertonic
  - Open Weights
---

## Giới thiệu

Supertonic là một hệ thống chuyển văn bản thành giọng nói đa ngôn ngữ cực nhanh, hoạt động trên thiết bị, được thiết kế để suy luận cục bộ với chi phí tối thiểu. Được hỗ trợ bởi ONNX Runtime, nó chạy hoàn toàn trên thiết bị của bạn—không cần đám mây, không cần gọi API, không lo ngại về quyền riêng tư.

GitHub: https://github.com/supertone-inc/supertonic  
Hugging Face: https://hf.co/Supertone/supertonic-3  
Paper: https://hf.co/papers/2410.06885  
Demo: https://hf.co/spaces/Supertone/supertonic-3  
Audio Samples: https://supertonic3.github.io  
Available Voices: https://supertone-inc.github.io/supertonic-py/voices/  


##  Ngôn ngữ

🌍 31 ngôn ngữ được hỗ trợ:


Arabic (`ar`), Bulgarian (`bg`), Croatian (`hr`), Czech (`cs`), Danish (`da`), Dutch (`nl`), English (`en`), Estonian (`et`), Finnish (`fi`), French (`fr`), German (`de`), Greek (`el`), Hindi (`hi`), Hungarian (`hu`), Indonesian (`id`), Italian (`it`), Japanese (`ja`), Korean (`ko`), Latvian (`lv`), Lithuanian (`lt`), Polish (`pl`), Portuguese (`pt`), Romanian (`ro`), Russian (`ru`), Slovak (`sk`), Slovenian (`sl`), Spanish (`es`), Swedish (`sv`), Turkish (`tr`), Ukrainian (`uk`), Vietnamese (`vi`)

> **Không chắc văn bản của bạn thuộc ngôn ngữ nào?** Hãy truyền `lang="na"` và Supertonic sẽ xử lý đầu vào theo cách không phụ thuộc vào ngôn ngữ — không cần thẻ ngôn ngữ cụ thể.


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

{{< youtube hA6G0L_ebYs >}}


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

```yml
name: supertonic
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version >= 3.10 required
  - python=3.10

  - pip
  - pip:
      # Supertonic TTS
      - supertonic

      # Local HTTP Server
      - supertonic[serve]
```

Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate supertonic
```


## Bước 3. Tạo một tệp Python

Tạo một tệp có tên supertonic_tts_test.py:

```python
from supertonic import TTS

# First run downloads the model from Hugging Face automatically.
tts = TTS(auto_download=True)

style = tts.get_voice_style(voice_name="M1")

text = "Supertonic is a lightning fast, on-device TTS system."

wav, duration = tts.synthesize(
    text=text,
    lang="en",                      # Language code (e.g., "en", "ko", "na" for language-agnostic)
    voice_style=style,              # Voice style object
    total_steps=8,                  # Quality: 5 (low) to 12 (high), default 8 (medium)
    speed=1.05,                     # Speed: 0.7 (slow) to 2.0 (fast)
)
# wav: numpy array of shape (1, num_samples,) with dtype=np.float32, sampled at 44100 Hz
# duration: numpy array of shape (1,) containing the duration of the generated audio in seconds

tts.save_audio(wav, "output.wav")
# import soundfile as sf
# sf.write("output.wav", wav.squeeze(), 44100)

print(f"Generated {duration[0]:.2f}s of audio")
```

Chạy thử:

```bash
python supertonic_tts_test.py
```

Kết quả sẽ là tệp âm thanh `output.wav`


### Máy chủ HTTP cục bộ

Bộ SDK Python cũng có thể chạy Supertonic như một dịch vụ HTTP cục bộ. Điều này hữu ích khi bạn muốn gọi Supertonic từ các công cụ đã hỗ trợ HTTP, chẳng hạn như các tác nhân cục bộ, tiện ích mở rộng trình duyệt, ứng dụng Electron, công cụ tự động hóa quy trình làm việc hoặc các máy khách âm thanh tương thích với OpenAI.

```bash
supertonic serve --host 127.0.0.1 --port 7788
```

Sau khi khởi chạy, hãy sử dụng điểm cuối `POST /v1/tts` gốc hoặc điểm cuối `POST /v1/audio/speech` tương thích với OpenAI. Máy chủ cũng cung cấp tài liệu OpenAPI tương tác tại `http://127.0.0.1:7788/docs`. Xem hướng dẫn [supertonic-py serve](https://supertone-inc.github.io/supertonic-py/cli/serve/) để biết các ví dụ về yêu cầu, tổng hợp hàng loạt và nhập JSON tùy chỉnh của Voice Builder.