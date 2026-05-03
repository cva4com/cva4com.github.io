---
linkTitle: Miniconda
title: Cài đặt Miniconda
weight: 5
prev: /tts
# next: /tts/kokoro
cascade:
  type: docs
tags:
  - conda
  - Miniconda
  - Anaconda
---

## Cài đặt Miniconda

{{< youtube AgnAs0nPEVg >}}


## Miniconda là gì?

Miniconda là trình cài đặt tối giản miễn phí cho Conda. Nó là một lựa chọn thay thế nhỏ gọn hơn cho Anaconda. Nó bao gồm Python, Conda và các thư viện phụ thuộc cần thiết.

Với Miniconda, bạn có thể tạo môi trường biệt lập. Điều này giúp tránh xung đột giữa các dự án khác nhau. Nó lý tưởng cho các nhà phát triển cần sự linh hoạt.


### Tải xuống Miniconda

Hãy làm theo các bước sau để tải xuống Miniconda:

1. Truy cập trang tải xuống chính thức của Miniconda (https://www.anaconda.com).
2. Chọn trình cài đặt (https://www.anaconda.com/download/success) cho hệ điều hành của bạn.
<!-- 3. Chọn phiên bản Python (khuyến nghị 3.x). -->

Đối với Windows, tải xuống tệp .exe. Đối với macOS và Linux, chọn tập lệnh shell phù hợp.

Liên kết trực tiếp: https://anaconda.com/api/installers/Miniconda3-latest-Windows-x86_64.exe


### Cài đặt trên Windows

Làm theo các bước sau để cài đặt trên Windows:

1. Nhấp đúp vào tệp .exe đã tải xuống.
2. Làm theo hướng dẫn của trình hướng dẫn cài đặt.
3. Chọn "Add Miniconda to PATH" nếu được nhắc.
4. Hoàn tất cài đặt.

Để xác minh, hãy mở Command Prompt và chạy:

```bash
conda --version
```


### Cài đặt trên macOS/Linux

{{< youtube QWta2QPUJ2E >}}

Đối với macOS và Linux, hãy sử dụng terminal:

1. Mở cửa sổ terminal.
2. Điều hướng đến thư mục đã tải xuống.
3. Chạy tập lệnh shell:

```bash
bash Miniconda3-latest-MacOSX-x86_64.sh
```

{{< youtube Y02Su_I-XUM >}}

<!--more-->

{{< cards >}}
  {{< card link="tts" title="Text-to-Speech" icon="book-open" >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
{{< /cards >}}