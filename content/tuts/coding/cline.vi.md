---
linkTitle: Cline
title: "Cline: Công cụ mã hóa Agentic tốt nhất cho VS Code"
weight: 3
cascade:
  type: docs
tags:
  - AI
  - Coding
  - Agents
---

Cline là trợ lý ảo tự động nhất mà tôi từng sử dụng. Cài đặt tiện ích mở rộng VS Code, cấu hình nhà cung cấp BYOK, giao cho nó một tác vụ và xem nó hoạt động. Nó đọc tệp, viết mã, chạy các lệnh terminal, xử lý lỗi và lặp lại – thường không cần nhắc bạn giữa các bước.

Nhược điểm là chi phí khá cao. Vì nó sử dụng công cụ rất nhiều, một phiên Cline trên Claude Sonnet có thể dễ dàng tốn từ 5-10 đô la. Hãy kết hợp nó với một mô hình rẻ hơn cho các công việc thường ngày. Gemini 2.5 Flash và GPT-5 Mini đều hoạt động tốt đáng ngạc nhiên với giá chỉ bằng một phần nhỏ.

Phù hợp nhất cho: Các nhà phát triển muốn có thao tác "nhấn nút chạy và để đó" mà không cần rời khỏi VS Code.


## Các tính năng chính

- Tách biệt Lập kế hoạch/Thực hiện: Cline hiển thị cho bạn kế hoạch trước khi thực hiện. Bạn có thể phê duyệt, sửa đổi hoặc từ chối kế hoạch trước khi bất kỳ thay đổi nào được thực hiện trên tập tin.
- Truy cập terminal: Chạy lệnh `npm run test`, `git commit`, các script xây dựng và các lệnh shell tùy ý như một phần của quá trình thực thi tác vụ
- Tạo và chỉnh sửa tập tin: Tạo tập tin mới, sửa đổi các tập tin hiện có và xóa những gì không còn cần thiết
- Tự động hóa trình duyệt: Điều khiển trình duyệt không giao diện người dùng để kiểm tra giao diện web như một phần của tác vụ tự động
- Hỗ trợ nhiều mô hình: Claude Sonnet 4.6, GPT-40, Gemini 2.5 Pro hoặc bất kỳ mô hình cục bộ nào thông qua Ollama
- Tích hợp MCP: Các trình kết nối được hỗ trợ bởi Marketplace đến cơ sở dữ liệu, API, công cụ thiết kế và dịch vụ phát triển
- Giám sát chi phí theo thời gian thực: Theo dõi việc sử dụng token để các lần chạy tự động không tạo ra hóa đơn bất ngờ

**Ưu điểm**

- Mô hình Lập kế hoạch/Thực thi là sự trừu tượng hóa phù hợp: AI thực hiện công việc, bạn vẫn kiểm soát ở mỗi điểm quyết định
- Hệ sinh thái MCP cho phép xây dựng các tác nhân hiểu được hệ thống thực tế của bạn, không chỉ tập tin hiện tại
- Cộng đồng đủ lớn để hầu hết các câu hỏi về tích hợp đã được trả lời trên Discord hoặc GitHub
- Hoạt động với các mô hình cục bộ thông qua Ollama để hoàn toàn riêng tư, ngoại tuyến Sử dụng

**Nhược điểm**

- Phù hợp nhất vẫn là quy trình làm việc ưu tiên trình soạn thảo. Những người thích sử dụng terminal thuần túy có thể thích Aider hoặc OpenCode hơn.
- Các tác vụ tự động tiêu tốn mã thông báo API nhanh hơn các công cụ chỉ hoàn thành. Cần dự trù ngân sách phù hợp.
- Mô tả nhiệm vụ mơ hồ sẽ cho kết quả kém hơn. Độ chính xác trong lời nhắc quan trọng hơn ở đây so với các công cụ hoàn thành.
- Không được tối ưu hóa cho việc hoàn thành nội tuyến nhẹ. Kết hợp với Continue để làm điều đó.

**Giấy phép và Lưu trữ**

- Giấy phép: Apache-2.0. Không có hạn chế thương mại.
- Tự lưu trữ: Các mô hình cục bộ thông qua Ollama chạy hoàn toàn trên máy của bạn. API đám mây (Anthropic, OpenAI) gửi mã đến máy chủ của nhà cung cấp.
- Cài đặt: VS Code Extension Marketplace. Tìm kiếm "Cline".

**Phù hợp nhất cho**

Các nhà phát triển đang thực hiện công việc ở cấp độ tính năng trong VS Code, những người muốn AI xử lý toàn bộ nhiệm vụ, chứ không chỉ dòng tiếp theo. Nếu hiện tại bạn viết một tính năng từ mô tả phiếu yêu cầu, Cline sẽ thay đổi điều đó thành: mô tả nhiệm vụ, xem xét kế hoạch, phê duyệt, lặp lại khi xem xét.

Nếu bạn không sử dụng VS Code, muốn dùng tính năng tự động hoàn thành thuần túy hoặc muốn ủy quyền hoàn toàn các tác vụ mà không cần phê duyệt ở mỗi bước, hãy bỏ qua Cline.


## Danh sách Model AI miễn phí được Cline hỗ trợ

Dựa trên file cấu hình OpenRouter được lưu trong Cline (`C:\Users\<username>\AppData\Roaming\Code\User\globalStorage\saoudrizwan.claude-dev\cache\openrouter_models.json`), các model hoàn toàn miễn phí (giá input = 0 và output = 0) được hỗ trợ như sau:


## 🤖 Các model miễn phí (input & output = 0)

| Model ID | Tên hiển thị | Ngữ cảnh |
|----------|-------------|----------|
| `inclusionai/ling-3.0-flash:free` | Ling-3.0-flash (free) | 262K |
| `poolside/laguna-s-2.1:free` | Poolside: Laguna S 2.1 (free) | 262K |
| `poolside/laguna-xs-2.1:free` | Poolside: Laguna XS 2.1 (free) | 262K |
| `cohere/north-mini-code:free` | Cohere: North Mini Code (free) | 256K |
| `google/gemma-4-31b-it:free` | Google: Gemma 4 31B (free) | 262K |
| `google/gemma-4-26b-a4b-it:free` | Google: Gemma 4 26B A4B (free) | 262K |
| `nvidia/nemotron-3-ultra-550b-a55b:free` | NVIDIA: Nemotron 3 Ultra (free) | 1M |
| `nvidia/nemotron-3-super-120b-a12b:free` | NVIDIA: Nemotron 3 Super (free) | 262K |
| `nvidia/nemotron-3-nano-30b-a3b:free` | NVIDIA: Nemotron 3 Nano 30B A3B (free) | 256K |
| `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free` | NVIDIA: Nemotron 3 Nano Omni (free) | 256K |
| `nvidia/nemotron-nano-12b-v2-vl:free` | NVIDIA: Nemotron Nano 12B 2 VL (free) | 128K |
| `nvidia/nemotron-nano-9b-v2:free` | NVIDIA: Nemotron Nano 9B V2 (free) | 128K |
| `nvidia/nemotron-3.5-content-safety:free` | NVIDIA: Nemotron 3.5 Content Safety (free) | 128K |
| `openai/gpt-oss-20b:free` | OpenAI: gpt-oss-20b (free) | 131K |


## 💡 Khuyến nghị cho việc lập trình

Các model miễn phí tốt nhất cho tác vụ coding trong số trên là:

1. **NVIDIA Nemotron 3 Ultra** (miễn phí) — 550B, ngữ cảnh lớn, mạnh về reasoning
2. **NVIDIA Nemotron 3 Super** (miễn phí) — 120B, tối ưu multi-agent
3. **Cohere North Mini Code** (miễn phí) — chuyên biệt cho coding agent
4. **Poolside Laguna S 2.1** (miễn phí) — model coding agent
5. **OpenAI gpt-oss-20b** (miễn phí) — open-weight của OpenAI

Bạn có thể sử dụng `openrouter/free` để tự động chọn model miễn phí tốt nhất cho từng tác vụ.


## 🌐 Router miễn phí

- **`openrouter/free`** — *Free Models Router*: tự động chọn ngẫu nhiên một model miễn phí từ danh sách model miễn phí của OpenRouter (ngữ cảnh 200K).


## ⚠️ Lưu ý quan trọng

- **`google/lyria-3-pro-preview`** và **`google/lyria-3-clip-preview`**: giá input/output = 0 nhưng là model **tạo nhạc** (Lyria 3), được tính phí theo bài hát/đoạn clip ($0.08/bài, $0.04/clip), không dùng chung cho code.
- **`deepseek/deepseek-chat`**: có giá input = 0 nhưng output = $1.0287 — **không hoàn toàn miễn phí**.
