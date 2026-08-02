---
title: Cline
weight: 3
cascade:
  type: docs
tags:
  - TTS
  - Chatterbox
  - Open Weights
---

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
