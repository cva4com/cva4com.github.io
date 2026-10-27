---
linkTitle: ICE-012
title: Cài đặt ICE-012 TTS bằng Conda
weight: 9
cascade:
  type: docs
tags:
  - TTS
  - ICE-012
  - Open Weights
params:
  tabs:
    sync: true
---

## Giới thiệu

ICE-012 Audio là một mô hình TTS đa ngôn ngữ với đầu ra truyền phát và sao chép giọng nói dựa trên tham chiếu. Nó giới thiệu một bộ điều hợp âm thanh chủ động — xử lý các mã nhúng codec trước khi truyền tải dữ liệu chính và tinh chỉnh các trạng thái ẩn sau đó.

Hugging Face: https://hf.co/darkps/ice-012-audio  
Demo: https://hf.co/spaces/hugging-apps/ice-012-audio-tts  
Website: https://dark.ps  

![ICE-012](/images/2026/language_stats.png)


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

Sắp ra mắt!
<!-- {{< youtube tMWyfCxGbGA >}} -->


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
name: ice-tts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio

      # Install the dependencies
      - transformers
      - accelerate
      - soundfile
      - pydub

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: ice-tts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # This is the PyTorch CUDA 12.6 wheels.
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Install the dependencies
      - transformers
      - accelerate
      - soundfile
      - pydub

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Sắp ra mắt!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: ice-tts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Install the dependencies
      - transformers
      - accelerate
      - soundfile
      - pydub

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate ice-tts
```


## Bước 3. Chạy suy luận

Tạo một tệp có tên `02.py`:

```python
import argparse
import soundfile as sf
from transformers import AutoModelForCausalLM

p = argparse.ArgumentParser()
p.add_argument("--text")
p.add_argument("--text-file")
p.add_argument("--language", default="en")
p.add_argument("--instruct", default=None, help='e.g. "female, young adult, high pitch"')
p.add_argument("--speed", type=float, default=1.0)
p.add_argument("--reference", help="reference wav for voice cloning")
p.add_argument("--reference-text", help="transcript of reference (skips Whisper ASR)")
p.add_argument("--output", default="out.wav")
a = p.parse_args()

text = open(a.text_file, encoding="utf-8").read() if a.text_file else a.text
assert text, "provide --text or --text-file"

model = AutoModelForCausalLM.from_pretrained(
    "darkps/ice-012-audio", trust_remote_code=True, device_map="auto"
)
audio = model.generate(
    text=text,
    language=a.language,
    instruct=a.instruct,
    ref_audio=a.reference,
    ref_text=a.reference_text,
    speed=a.speed,
)
sf.write(a.output, audio[0], model.sampling_rate)
print("saved", a.output)
```

Bây giờ, hãy chạy tập lệnh ví dụ cơ bản để tổng hợp giọng nói:

```bash
python 02.py --text "Hello world" --language en --instruct "female, young adult" --output out.wav
```

Kết quả sẽ là tệp âm thanh `out.wav`


### Nhân bản giọng nói

Tải xuống bản ghi âm tham khảo

```bash
curl -L -O "http://cva4.com/audio/prompt_english_female1.wav"
```

Mẫu âm thanh tham khảo: `prompt_english_female1.wav`

<audio controls>
  <source src="/audio/prompt_english_female1.wav" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>


Bây giờ, hãy chạy tập lệnh để tạo bản sao âm thanh dựa trên tệp âm thanh tham chiếu:

```bash
python 02.py --text "Hello world" --reference prompt_english_female1.wav --reference-text "In order to win, you must expect to win." --output clone.wav
```

Kết quả sẽ là tệp âm thanh `clone.wav`