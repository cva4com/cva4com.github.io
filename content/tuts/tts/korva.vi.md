---
linkTitle: Korva
title: Cài đặt Korva TTS bằng Conda
weight: 12
cascade:
  type: docs
tags:
  - TTS
  - Korva
  - KorvaTTS
  - Open Weights
params:
  tabs:
    sync: true
---

## Giới thiệu

KorvaTTS là hệ thống text-to-speech mã nguồn mở tập trung vào **tiếng Việt có code-switching** (câu tiếng Việt chứa từ tiếng Anh, tên thương hiệu, thuật ngữ kỹ thuật). Toàn bộ chạy on-device qua ONNX Runtime: không cần GPU, không gọi API, âm thanh 44.1 kHz.

GitHub: https://github.com/dogenthq/KorvaTTS  
Hugging Face: https://hf.co/collections/dogenthq/KorvaTTS  
Demo Page: https://hf.co/spaces/hugging-apps/korvatts-demo  
Try it online: https://heykorva.com  

Model là bản re-implement của chúng tôi theo kiến trúc [Supertonic 3](https://github.com/supertone-inc/supertonic) (99M tham số, flow-matching TTS), **train từ đầu** trên dữ liệu tiếng Việt, với vocoder dựa trên [BlueCodec](https://github.com/maxmelichov/BlueTTS). Nhóm tác giả Supertonic đang archive repo gốc; KorvaTTS tiếp nối hướng đi này với trọng tâm tiếng Việt và lộ trình mở hướng tới voice cloning và training.

**🌐 Dùng thử ngay trên trình duyệt — không cần cài đặt:** [heykorva.com](https://heykorva.com/)

## Điểm nổi bật

- 🇻🇳 **Ưu tiên tiếng Việt** — huấn luyện trên audiobook tiếng Việt cộng thêm bộ dữ liệu code-switching riêng
- 🔀 **Code-switching** — từ tiếng Anh nằm trong câu tiếng Việt được đọc tự nhiên
- ⚡ **Nhanh trên CPU** — real-time factor nhỏ hơn 1 trên CPU laptop; GPU là tuỳ chọn
- 🔊 Xuất **WAV 44.1 kHz**, không cần upsampler ngoài
- 🧩 **Tương thích trực tiếp** với các runtime Supertonic 3 (xem [Tương thích](#tương-thích-với-supertonic))
- 🪪 **Apache-2.0** cho cả code lẫn weight


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
* **Dung lượng ổ cứng:** Khuyến nghị 5GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn nhưng RẤT KHUYÊN DÙNG để tăng hiệu suất.
* **Internet:** Để tải xuống các thư viện phụ thuộc và mô hình từ Hugging Face Hub.

ONNX Runtime không phát hành bản build riêng cho từng tag `cuXXX` như PyTorch. Chỉ có 3 nhóm build, nên danh sách của bạn gộp lại như sau:

| CUDA của bạn | Bản cần cài |
|---|---|
| cu118 | Build CUDA 11.8 (`onnxruntime-gpu` 1.20.x) |
| cu121, cu124, cu126, cu128, cu129 | Build CUDA 12.x (`onnxruntime-gpu<1.27`) |
| cu130, cu132, cu134 | Build CUDA 13.x (`onnxruntime-gpu>=1.27`) |


## Video hướng dẫn

Sắp ra mắt!
<!-- {{< youtube mqFtFIAlvB4 >}} -->


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
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # GPU version of ONNX runtime
      # This is for < CUDA 12.x
      # - onnxruntime-gpu==1.20.*

      # This is for CUDA 12.x
      - onnxruntime-gpu[cuda,cudnn]<1.27

      # This is for CUDA 13.x
      # - onnxruntime-gpu[cuda,cudnn]>=1.27

      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Sắp ra mắt!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: korvatts
channels:
  - conda-forge
  - defaults

dependencies:
  # Python version (requires >= 3.10)
  - python=3.10

  - pip
  - pip:
      # Install KorvaTTS directly from PyPI
      - korvatts
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate korvatts
```

### Tải xuống các trọng số

```bash
korvatts voices
```


## Bước 3. Chạy suy luận

### Command Line Interface

Bây giờ, hãy chạy lệnh cơ bản để tổng hợp giọng nói:

```bash
korvatts synth "Xin chào, đây là KorvaTTS." -v khanh_vy -o hello.wav
```

Kết quả sẽ là tệp âm thanh `output.wav`


### Chạy suy luận bằng tệp Python

Tạo một tệp có tên `korva_test.py`:

```python
from korvatts import TTS

tts = TTS()  # first run downloads weights + voices from Hugging Face
print(tts.list_voices())

wav, duration = tts.synthesize(
    "Hôm nay team mình sẽ demo tính năng text-to-speech mới.",
    voice="khanh_vy",
    lang="vi",
    total_steps=32,  # default; best quality. Lower (8-16) for faster synthesis
    speed=1.05,      # default; 0.5 (slow) .. 2.0 (fast)
)
tts.save_audio(wav, "output.wav")
```

Chạy tập lệnh để chuyển đổi văn bản thành giọng nói:

```bash
python korva_test.py
```

Kết quả sẽ là tệp âm thanh `output.wav`


<!-- ### Khởi chạy giao diện Web -->


## Bảng tổng hợp lỗi và cảnh báo

| Loại | Thông báo (rút gọn) | Mức độ | Nguyên nhân | Cách xử lý |
|------|---------------------|--------|-------------|------------|
| `UserWarning` (huggingface_hub) | `cache-system uses symlinks by default ... your machine does not support them` | Cảnh báo, bỏ qua | Windows không cho tạo symlink khi chưa bật Developer Mode hoặc chưa chạy quyền admin | Cache vẫn hoạt động, chỉ tốn thêm ổ đĩa. Bật Developer Mode, hoặc tắt cảnh báo: `setx HF_HUB_DISABLE_SYMLINKS_WARNING 1`. |
| Warning (huggingface_hub) | `You are sending unauthenticated requests to the HF Hub. Please set a HF_TOKEN` | Cảnh báo, bỏ qua | Tải model khi chưa đăng nhập, bị giới hạn tốc độ | Tạo token Read tại huggingface.co/settings/tokens, rồi `setx HF_TOKEN hf_xxx` hoặc `hf auth login`. |

Thông tin quan trọng khác
- **Sửa lại một chi tiết trước đó**: lệnh đăng nhập Hugging Face bản mới là `hf auth login`, không phải `huggingface-cli login`.
