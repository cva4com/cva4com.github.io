---
linkTitle: NeuTTS
title: Cài đặt NeuTTS bằng Conda
weight: 11
cascade:
  type: docs
tags:
  - TTS
  - Neu
  - Open Weights
---

## Giới thiệu

Công nghệ AI giọng nói tiên tiến nhất từ ​​lâu đã bị giới hạn trong các API web. NeuTTS là tập hợp các mô hình ngôn ngữ chuyển văn bản thành giọng nói (TTS) mã nguồn mở, hoạt động trực tiếp trên thiết bị và hỗ trợ sao chép giọng nói tức thì. Được phát triển dựa trên nền tảng các mô hình ngôn ngữ lớn (LLM), NeuTTS mang đến khả năng tạo giọng nói tự nhiên, hiệu suất thời gian thực, tính năng bảo mật tích hợp và khả năng sao chép giọng nói ngay trên thiết bị của bạn – mở ra một phân khúc mới cho các tác nhân giọng nói nhúng, trợ lý ảo, đồ chơi thông minh và các ứng dụng đáp ứng tiêu chuẩn tuân thủ.

GitHub: https://github.com/neuphonic/neutts  
Hugging Face: https://hf.co/neuphonic/neutts-air  
Demo: https://hf.co/neuphonic/spaces  

Các tính năng chính:

- 🗣Độ chân thực hàng đầu trong phân khúc kích thước - tạo ra giọng nói tự nhiên, cực kỳ chân thực và giống người, đạt sự cân bằng tối ưu giữa tốc độ, kích thước và chất lượng cho các ứng dụng thực tế
- 📱Tối ưu hóa để triển khai trực tiếp trên thiết bị - hỗ trợ định dạng lượng tử hóa GGUF, sẵn sàng chạy trên điện thoại, máy tính xách tay hoặc thậm chí là Raspberry Pi
- 👫Sao chép giọng nói tức thì - tạo giọng nói riêng chỉ với đoạn âm thanh ngắn từ 3 giây
- 🚄Kiến trúc LM + codec đơn giản - giúp việc phát triển và triển khai trở nên dễ dàng


## Yêu cầu hệ thống

* **Hệ điều hành:** Windows 10/11 (64-bit), macOS hoặc Linux (Debian/Ubuntu).
* **Python:** Yêu cầu phiên bản >= 3.10
* **Dung lượng ổ cứng:** Khuyến nghị 4GB trở lên (cho các thư viện phụ thuộc và bộ nhớ cache mô hình). Ít nhất 400 MB cho Miniconda; 3 GB trở lên cho Anaconda đầy đủ.
* **GPU:** là tùy chọn. Nó chạy mượt mà trên CPU của máy tính xách tay.
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
| CUDA 11.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 |
| CUDA 12.1 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121 |
| CUDA 12.6 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126 |
| CUDA 12.8 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128 |
| CUDA 13.0 | pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130 |


## Video hướng dẫn

<!-- Sắp ra mắt! -->
{{< youtube dreLvnl678M >}}


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
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch CPU only. It runs smoothly on a laptop CPU.
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="NVIDIA" >}}
```yml
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch CUDA is optional. It runs smoothly on a laptop CPU.
      - --extra-index-url https://download.pytorch.org/whl/cu126
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

  {{< tab name="AMD" >}}
> Coming soon!
  {{< /tab >}}

  {{< tab name="Apple Silicon" >}}
```yml
name: neutts
channels:
  - conda-forge
  - defaults
dependencies:
  # Python version (requires >= 3.10)
  - python=3.10
  - pyaudio            # for streaming playback examples

  - pip
  - pip:
      # PyTorch MPS (Metal Performance Shaders)
      - torch
      - torchaudio

      # For fix ModuleNotFoundError: No module named 'torchao.dtypes.nf4tensor'
      - torchao==0.13.0

      # Install NeuTTS
      - neutts

      # Download the model from Hugging Face
      - huggingface_hub
```
  {{< /tab >}}

{{< /tabs >}}


Kích hoạt môi trường conda:

```bash
conda env create -f environment.yml
conda activate neutts
```

Clone NeuTTS từ source (chạy sau khi kích hoạt môi trường)

```bash
git clone https://github.com/neuphonic/neutts.git
cd neutts
```

Mẫu âm thanh tham khảo:
https://github.com/neuphonic/neutts/tree/main/samples


## Bước 3. Quyền truy cập vào mô hình

Vì mô hình này được cài đặt chế độ hạn chế, bạn phải đăng ký quyền truy cập trước:

1. Đăng nhập vào tài khoản Hugging Face của bạn trên trình duyệt.
2. Truy cập trực tiếp vào trang mô hình của NeuTTS Nano và NeuCodec:
   - https://huggingface.co/neuphonic/neutts-nano
   - https://huggingface.co/neuphonic/neucodec
3. Điền các thông tin bắt buộc và nhấp vào nút `Agree and access repository`.
4. Tạo một token với quyền `Read` (Đọc) bằng cách vào mục **Settings > Access Tokens** trong tài khoản Hugging Face của bạn.
5. Mở terminal và chạy lệnh: `hf auth login`
   CLI sẽ yêu cầu bạn thực hiện theo một trong hai cách sau:
   - Login with your browser
   - Paste an Access Token
6. Chọn tùy chọn đầu tiên. Giao diện dòng lệnh (CLI) sẽ hiển thị một mã ngắn và yêu cầu bạn truy cập một đường dẫn URL (https://huggingface.co/oauth/device). Hãy dán mã này vào trình duyệt để xác nhận đăng nhập ngay lập tức.
7. Chọn tùy chọn thứ hai. Dán mã token của bạn khi được yêu cầu và nhấn Enter.

Yêu cầu truy cập kho lưu trữ này của bạn đã được gửi và đang chờ các tác giả của kho lưu trữ xem xét. Bạn có thể kiểm tra trạng thái của tất cả các yêu cầu truy cập trong phần [cài đặt](https://huggingface.co/settings/gated-repos).


## Bước 4. Chạy suy luận

Bây giờ, hãy chạy tập lệnh ví dụ cơ bản để tổng hợp giọng nói:

```bash
python -m examples.basic_example --input_text "My name is Sophie. I'm 25 and I just moved to London." --ref_audio samples/sophie.wav --ref_text samples/sophie.txt
```

Kết quả sẽ là tệp âm thanh `output.wav`


### Chạy suy luận từ tệp Python

```python
from neutts import NeuTTS
import soundfile as sf

tts = NeuTTS(
   backbone_repo="neuphonic/neutts-nano", # or 'neuphonic/neutts-nano-q4-gguf' with llama-cpp-python installed
   backbone_device="cpu",
   codec_repo="neuphonic/neucodec",
   codec_device="cpu"
)
input_text = "My name is Andy. I'm 25 and I just moved to London. The underground is pretty confusing, but it gets me around in no time at all."

ref_text = "samples/jo.txt"
ref_audio_path = "samples/jo.wav"

ref_text = open(ref_text, "r").read().strip()
ref_codes = tts.encode_reference(ref_audio_path)

wav = tts.infer(input_text, ref_codes, ref_text)
sf.write("test.wav", wav, 24000)
```