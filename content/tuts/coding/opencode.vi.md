---
linkTitle: OpenCode
title: "OpenCode: Giải pháp thay thế mã nguồn mở tốt nhất cho Claude Code"
weight: 2
cascade:
  type: docs
tags:
  - AI
  - Coding
  - Agents
---

Phù hợp nhất cho: các nhà phát triển muốn có một công cụ lập trình AI gốc terminal hoạt động trên mọi trình soạn thảo và mọi nhà cung cấp mô hình.

OpenCode là công cụ lập trình AI mã nguồn mở được đánh giá cao nhất mà tôi tìm thấy: hơn 162.000 lượt đánh dấu sao trên GitHub và con số này vẫn đang tăng lên. Nhóm SST đã xây dựng nó như một giải pháp mã nguồn mở cho Claude Code: một công cụ gốc terminal với giao diện người dùng dựa trên văn bản (TUI) đầy đủ, ứng dụng máy tính để bàn và các tiện ích mở rộng IDE. Trong khi Claude Code chỉ cho phép bạn sử dụng Anthropic, OpenCode hoạt động với hơn 75 nhà cung cấp thông qua Models.dev, bao gồm Claude, OpenAI, Gemini và các mô hình cục bộ. Quy trình làm việc tương tự, nhưng lựa chọn mô hình đầy đủ.

Kho lưu trữ vẫn hoạt động trong suốt thời gian đánh giá này, và kiến ​​trúc máy khách/máy chủ có nghĩa là bạn có thể chạy máy chủ trên một máy tính từ xa và điều khiển nó từ terminal, máy tính để bàn hoặc ứng dụng di động của mình.


## Các tính năng chính

- Hơn 75 nhà cung cấp LLM: Claude, OpenAI, Gemini, Ollama và các nhà cung cấp khác thông qua Models.dev (không bị giới hạn bởi bất kỳ nhà cung cấp nào)
- Hai tác nhân tích hợp sẵn: "build" (truy cập đầy đủ để đọc, ghi và thực thi) và "plan" (phân tích và khám phá chỉ đọc), có thể chuyển đổi bằng phím Tab
- Hỗ trợ LSP: Tự động tải máy chủ ngôn ngữ chính xác cho ngôn ngữ trong thư mục làm việc của bạn
- Đa phiên: Chạy nhiều tác nhân trên cùng một dự án song song
- Chia sẻ liên kết: Chia sẻ liên kết đến bất kỳ phiên nào để gỡ lỗi hoặc xem lại
- Đa nền tảng: Giao diện người dùng TUI trên thiết bị đầu cuối, ứng dụng máy tính để bàn (macOS, Windows, Linux beta) và tiện ích mở rộng IDE
- Ưu tiên quyền riêng tư: Không có mã hoặc dữ liệu ngữ cảnh nào được lưu trữ ở phía máy chủ
- Đăng nhập GitHub Copilot và ChatGPT: Đăng nhập bằng tài khoản GitHub Copilot hoặc ChatGPT Plus hiện có để sử dụng các tín dụng mô hình đó

**Ưu điểm**

- Hơn 162.000 lượt đánh dấu sao trên GitHub, cộng đồng lập trình AI mã nguồn mở lớn nhất mà tôi tìm thấy
- Không phụ thuộc vào nhà cung cấp: thay đổi mô hình mà không cần thay đổi quy trình làm việc
- Thiết kế thân thiện với dòng lệnh, phù hợp với các nhà phát triển thường xuyên sử dụng dòng lệnh
- Đảm bảo quyền riêng tư: không lưu trữ dữ liệu, chạy hoàn toàn cục bộ với Ollama

**Nhược điểm**

- Giao diện người dùng dòng lệnh (Terminal UI) có độ khó học cao hơn so với các công cụ GUI gốc
- Không tích hợp sâu với trình soạn thảo cụ thể nào (không phụ thuộc vào trình soạn thảo có nghĩa là không có các tính năng gốc của trình soạn thảo)
- Gói mô hình quản lý "Zen" tùy chọn là trả phí; gói miễn phí yêu cầu bạn có khóa API riêng

**Giấy phép và Lưu trữ**

Được cấp phép theo giấy phép MIT. Chạy hoàn toàn trên máy tính của bạn. Không có dữ liệu nào rời khỏi hệ thống của bạn trừ khi bạn gửi nó đến nhà cung cấp AI. Cài đặt thông qua `curl -fsSL https://opencode.ai/install | bash`, npm, Homebrew hoặc Scoop.

**Phù hợp nhất cho**

Dành cho các nhà phát triển muốn có một trình quản lý terminal kiểu Claude Code mà không bị ràng buộc bởi Anthropic. Mạnh mẽ cho bất kỳ ai thường xuyên chuyển đổi trình soạn thảo, làm việc với nhiều cơ sở mã hoặc chạy trình quản lý trên máy từ xa.

Hãy bỏ qua OpenCode nếu bạn muốn tích hợp sâu với VS Code (Cline cung cấp cho bạn khả năng giám sát Lập kế hoạch/Thực hiện ngay trong VS Code) hoặc một trình quản lý hoàn toàn tự động trả về một yêu cầu kéo hoàn chỉnh (OpenHands xử lý việc này tốt hơn).


## Danh sách Model AI miễn phí được hỗ trợ

| Model ID | Tên hiển thị | Ngữ cảnh | Đầu ra |
|----------|-------------|----------|----------|
| big-pickle | Big Pickle | 200K | 32K |
| mimo-v2.5-free | MiMo-V2.5 Free | 200K | 32K |
| laguna-s-2.1-free | Laguna S 2.1 Free | 256K | 32K |
| ling-3.0-flash-free | Ling-3.0-flash Free | 262K | 32K |
| north-mini-code-free | North Mini Code Free | 256K | 64K |
| nemotron-3-ultra-free | Nemotron 3 Ultra Free | 1M | 128K |
| deepseek-v4-flash-free | DeepSeek V4 Flash Free | 200K | 128K |


## Benchmark

![Benchmark](/images/2026/laguna-xs2-1-chart.svg)

| Model              | Size (total params.) | SWE-bench Verified | SWE-bench Multilingual | SWE-Bench Pro (Public Dataset) | Terminal-Bench 2.0 |
|--------------------|---------------------:|-------------------:|-----------------------:|-------------------------------:|-------------------:|
| Laguna XS 2.1      | 33B                  | 70.9%              | 63.1%                  | 47.6%                          | 37.5%              |
| Laguna XS.2        | 33B                  | 69.9%              | 57.7%                  | 46.3%                          | 35.7%              |
| Qwen3.6-35B-A3B    | 35B                  | 73.4%              | 67.2%                  | 49.5%                          | 51.5%              |
| North Mini Code    | 30B                  | 67.6%              | -                      | 40.2%                          | 36.0%              |
| MAI-Code-1-Flash   | 137B                 | 71.6%              | 65.5%                  | 51.2%                          | 54.8%              |
| gpt-oss-120B       | 120B                 | -                  | -                      | 16.2%                          | 18.7%              |
| Claude Haiku 4.5   | -                    | 73.3%              | -                      | 39.5%                          | 29.8%              |
| GPT-5.4 Nano       | -                    | -                  | -                      | 52.4%                          | 46.3%              |