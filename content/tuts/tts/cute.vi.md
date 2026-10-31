---
linkTitle: CuteTTS
title: Cài đặt OPPO CuteTTS bằng Conda
weight: 6
cascade:
  type: docs
tags:
  - TTS
  - OPPO
  - CuteTTS
  - Open Weights
params:
  tabs:
    sync: true
---

## Giới thiệu

CuteTTS: một mô hình chuyển đổi văn bản thành giọng nói (TTS) tự hồi quy liên tục, có trọng lượng nhẹ và vận hành hiệu quả trên các nền tảng GPU, CPU cũng như chip Apple silicon.

GitHub: https://github.com/OPPO-Mente-Lab/CuteTTS  
Hugging Face: https://hf.co/OPPOer/CuteTTS  
Hugging Face: https://hf.co/OPPOer/CuteTTS-distill  
Demo: https://hf.co/spaces/hugging-apps/cutetts-demo  
Paper: https://arxiv.org/abs/2608.08638  

![CuteTTS](/images/2026/cute_backbone.png)

- Một mô hình chuyển văn bản thành giọng nói (TTS) tự hồi quy liên tục, có trọng lượng nhẹ (~230 triệu tham số), vận hành hiệu quả trên cả GPU, CPU và các dòng chip Apple silicon.
- Độ trễ cực thấp: chỉ mất khoảng `40 ms` để tạo ra đoạn âm thanh đầu tiên, với tốc độ xử lý nhanh gấp khoảng 9 lần thời gian thực trên card đồ họa NVIDIA RTX 4090.
- Chất lượng giọng nói vượt trội cùng khả năng sao chép giọng nói (voice cloning) ấn tượng.
- Cung cấp bản demo trên nền tảng web, API Python và giao diện dòng lệnh (CLI).
- Hỗ trợ đa ngôn ngữ: tiếng Anh, tiếng Trung, tiếng Pháp, tiếng Đức và tiếng Tây Ban Nha.


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

![CuteTTS](/images/2026/performance.svg)
  {{< /tab >}}

{{< /tabs >}}

| Environment | Run this Command |
| :-- | :-- |
| CPU only  | `pip3 install torch torchvision` |
| Apple Silicon | `pip3 install torch torchvision` |
| AMD ROCm | [Install PyTorch for ROCm](https://rocm.docs.amd.com/projects/ai-ecosystem/en/latest/frameworks/pytorch/install.html) |
| CUDA 11.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118` |
| CUDA 12.1 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121` |
| CUDA 12.6 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126` |
| CUDA 12.8 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128` |
| CUDA 13.0 | `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130` |


## Video hướng dẫn

Sắp ra mắt!
<!-- {{< youtube LXRTv9bbIXA >}} -->


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
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # PyTorch CPU only
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # This is the PyTorch CUDA 12.6 wheels.
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Sắp ra mắt!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: cutetts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.12

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # Install CuteTTS directly from GitHub.
      - git+https://github.com/OPPO-Mente-Lab/CuteTTS.git

      # Download the model from Hugging Face / ModelScope
      - huggingface_hub
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate cutetts
```

Clone và cài CuteTTS từ source (chạy sau khi kích hoạt môi trường)

```bash
git clone https://github.com/OPPO-Mente-Lab/CuteTTS.git
cd CuteTTS
```

### Tải xuống các trọng số

Tải xuống [CuteTTS](https://huggingface.co/OPPOer/CuteTTS) hoặc [CuteTTS-distill](https://huggingface.co/OPPOer/CuteTTS-distill) vào thư mục `./model`:

```bash
# Tạo thư mục model (Windows tự động xử lý việc tạo thư mục cha)
mkdir model

# Tải model CuteTTS (hoặc CuteTTS-distill nếu máy yếu hơn)
hf download OPPOer/CuteTTS --local-dir ./model/CuteTTS
hf download OPPOer/CuteTTS-distill --local-dir ./model/CuteTTS-distill
```

### Cấu trúc thư mục

Cấu trúc thư mục được mong đợi là:

```
D:\cute\
├── CuteTTS\
│   ├── assets\
│   ├── LICENSES\
│   ├── model\
│   │   ├── CuteTTS\
│   │   └── CuteTTS-distill\
│   ├── src\
│   │   └── cutetts\
│   ├── .gitignore
│   ├── LICENSE
│   ├── NOTICE
│   ├── README.md
│   ├── README_zh.md
│   ├── infer.py
│   └── pyproject.toml
├── cute_test.py
└── environment.yml
```


## Bước 3. Chạy suy luận

### CLI Inference

```bash
# sanity check
cutetts --help
```

```bash
usage: cutetts [-h] --model-dir MODEL_DIR --text TEXT [--mode {tts,voice_clone}] [--reference-audio REFERENCE_AUDIO] [--output OUTPUT] [--device DEVICE] [--cfg-strength CFG_STRENGTH]
               [--diffusion-steps DIFFUSION_STEPS] [--diffusion-sway-coefficient DIFFUSION_SWAY_COEFFICIENT] [--max-decode-length MAX_DECODE_LENGTH] [--seed SEED] [--no-progress]

Generate speech with CuteTTS.

options:
  -h, --help            show this help message and exit
  --model-dir MODEL_DIR
  --text TEXT
  --mode {tts,voice_clone}
  --reference-audio REFERENCE_AUDIO
  --output OUTPUT
  --device DEVICE       Inference device: auto, cuda, mps, or cpu (default: auto).
  --cfg-strength CFG_STRENGTH
  --diffusion-steps DIFFUSION_STEPS
  --diffusion-sway-coefficient DIFFUSION_SWAY_COEFFICIENT
  --max-decode-length MAX_DECODE_LENGTH
  --seed SEED
  --no-progress
```

Bây giờ, hãy chạy tập lệnh ví dụ cơ bản để tổng hợp giọng nói:

```bash
cutetts --model-dir ./model/CuteTTS --mode tts --text "The voice generated by this model sounds amazing!" --output tts.wav
```

Kết quả sẽ là tệp âm thanh `tts.wav`

**Chạy thử sao chép giọng nói**

```bash
cutetts --model-dir ./model/CuteTTS --mode voice_clone --reference-audio ./assets/default_reference.wav --text "The voice generated by this model sounds amazing!" --output clone.wav
```


### Chạy suy luận bằng tệp Python

Tạo một tệp có tên `cute_test.py`:

```python
from cutetts import CuteTTS
import soundfile as sf

model = CuteTTS.from_pretrained("./CuteTTS/model/CuteTTS", device="auto")
result = model.generate("The voice generated by this model sounds amazing!", mode="tts")
sf.write("tts.wav", result.waveform.squeeze(0).numpy(), result.sample_rate)

clone = model.generate(
    "The voice generated by this model sounds amazing!",
    mode="voice_clone",
    reference_audio="./CuteTTS/assets/default_reference.wav",
)
sf.write("clone.wav", clone.waveform.squeeze(0).numpy(), clone.sample_rate)
```

Chạy tập lệnh để sao chép giọng nói:

```bash
python cute_test.py
```

Kết quả sẽ là tệp âm thanh `out.wav`

<!-- **Streaming Python API** -->


### Khởi chạy giao diện Web

Sau khi cài đặt xong, bạn không cần viết code mà có thể bật ngay một giao diện Web UI cục bộ bằng lệnh:

```bash
cutetts-demo --model-dir ./model --device auto --host 127.0.0.1 --port 7860
```

Mở trình duyệt và truy cập vào địa chỉ [http://127.0.0.1:7860](http://127.0.0.1:7860) để bắt đầu sử dụng. Hệ thống sẽ tự động tải các file Model (Trọng số cấu hình mã nguồn) từ HuggingFace trong lần đầu chạy.
