---
linkTitle: TTS Open
title: Chuyển Văn bản thành Giọng nói Open
weight: 2
prev: /tts
next: /tts/kokoro
cascade:
  type: docs
tags:
  - TTS
  - Text-to-Speech
  - Open Weights
---

## Bảng xếp hạng

Mô hình AI chuyển Văn bản thành Giọng nói

Bảng xếp hạng các API chuyển văn bản thành giọng nói được so sánh bên dưới bằng cách sử dụng dữ liệu của bên thứ ba từ bảng xếp hạng [Artificial Analysis leaderboard](https://artificialanalysis.ai/text-to-speech/leaderboard) (tính đến tháng 4 năm 2026), các chỉ số độ tin cậy trong sản xuất và tính linh hoạt trong triển khai, bao gồm các tiêu chuẩn về độ trễ, phạm vi ngôn ngữ và các tùy chọn tích hợp.

Inworld AI TTS-1.5 Max xếp hạng #1 với điểm ELO là 1.208 dựa trên hàng nghìn so sánh sở thích của người dùng ẩn danh, với độ trễ P90 dưới 250ms.

| Hạng | Công ty | Model | ELO | Giá API |
| :-- | :-- | :-- | :-- | :-- |
| #1 | Fish Audio | [Fish Audio S2 Pro](https://huggingface.co/fishaudio/s2-pro) | 1,124 | $15 /1M chars |
| #2 | StepFun | [Step Audio EditX](https://huggingface.co/stepfun-ai/Step-Audio-EditX) | 1,098 | N/A |
| #3 | NVIDIA | [Magpie-Multilingual 357M](https://huggingface.co/nvidia/magpie_tts_multilingual_357m) | 1,063 | N/A |
| #4 | Kokoro | [Kokoro 82M v1.0](https://huggingface.co/hexgrad/Kokoro-82M) | 1,055 | $0.7 /1M chars |
| #5 | Mistral | [Voxtral TTS](https://huggingface.co/mistralai/Voxtral-4B-TTS-2603) | 1,053 | $16 /1M chars |
| #6 | Maya Research | [Maya1](https://huggingface.co/maya-research/maya1) | 1,049 | N/A |
| #7 | Fish Audio | [Fish Audio 1.5](https://huggingface.co/fishaudio/fish-speech-1.5) | 1,012 | $15 /1M chars |
| #8 | Resemble AI | [Chatterbox](https://github.com/resemble-ai/chatterbox) | 1,006 | $25 /1M chars |
| #9 | Zyphra | [Zonos-v0.1](https://github.com/Zyphra/Zonos) | 1,000 | $20 /1M chars |
| #10 | Microsoft | [VibeVoice](https://huggingface.co/microsoft/VibeVoice-1.5B) 7B | 957 | N/A |
| #11 | OpenVoice | [OpenVoice v2](https://huggingface.co/myshell-ai/OpenVoiceV2) | 948 | $8.3 /1M chars |
| #12 | Alibaba | [Qwen3 TTS](https://github.com/QwenLM/Qwen3-TTS) | 932 | N/A |
| #13 | Coqui | [XTTS v2](https://huggingface.co/coqui/XTTS-v2) | 885 | $40.4 /1M chars |
| #14 | StyleTTS  | [StyleTTS 2](https://github.com/yl4579/StyleTTS2) | 877 | $2.8 /1M chars |
| #15 | MetaVoice | [MetaVoice v1](https://github.com/metavoiceio/metavoice-src) | 764 | N/A |

Độ trễ dưới 200ms hiện nay đã có thể đạt được nhờ các kiến ​​trúc mạng thần kinh hiện đại, và việc sao chép giọng nói không cần huấn luyện từ đoạn âm thanh dài 3-15 giây đã trở thành tính năng tiêu chuẩn chứ không còn là tính năng cao cấp nữa.

## Top 27 mô hình AI TTS theo xếp hạng theo ELO

{{< youtube D8_wft9Bd84 >}}


## Top 45 mô hình AI TTS trên GitHub

| Model | Languages | Voice Cloning | Streaming | ASR | License |
| :--- | :--- | :---: | :---: | :---: | :--- |
| [Chatterbox](#chatterbox) | 23+ | ✅ | ✅ | ❌ | MIT |
| [Dia](#dia) | En | ✅ | ✅ | ❌ | Apache-2.0 |
| [FireRedTTS2](#fireredtts2) | 7 langs | ✅ | ✅ | ❌ | Apache-2.0 |
| [Fish Audio S2 Pro](#fish-audio-s2-pro) | 80+ | ✅ | ✅ | ❌ | Research License |
| [Fish Speech](#fish-speech) | 8 langs | ✅ | ✅ | ❌ | Apache-2.0 |
| [Fun-CosyVoice 3.0](#fun-cosyvoice-30) | 9 + 18 dialects | ✅ | ✅ | ❌ | Apache-2.0 |
| [GLM-TTS](#glm-tts) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |
| [IndexTTS2](#indextts2) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |
| [Irodori-TTS-500M-v2](#irodori-tts-500m-v2) | Jp | ✅ | ❌ | ❌ | MIT |
| [Kimi-Audio](#kimi-audio) | Multi | ✅ | ✅ | ✅ | MIT/Apache-2.0 |
| [KittenTTS](#kittenTTS) | En+ | ✅ | ✅ | ❌ | Apache-2.0 |
| [Kokoro-82M](#kokoro-82m) | 8 (54 voices) | ✅ | ✅ | ❌ | Apache-2.0 |
| [KokoClone](#kokoclone) | 7 | ✅ | ✅ | ❌ | Apache-2.0 |
| [KugelAudio](#kugelaudio) | 23 EU | ✅ | ✅ | ❌ | MIT |
| [LEMAS-TTS](#lemas-tts) | 10 | ✅ | ❌ | ❌ | Apache-2.0 |
| [LFM2-Audio-1.5B](#lfm2-audio-15b) | En | ✅ | ✅ | ✅ | LFM |
| [LongCat-AudioDiT](#longcat-audiodit) | Zh/En | ✅ | ❌ | ❌ | MIT |
| [LongCat-Next](#longcat-next) | Zh/En | ✅ | ✅ | ✅ | MIT |
| [LuxTTS](#luxtts) | - | ✅ | ✅ | ❌ | Apache-2.0 |
| [Maya1](#maya1) | En | ✅ | ✅ | ❌ | Apache-2.0 |
| [MegaTTS3](#megatts3) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |
| [MiMo-Audio](#mimo-audio) | Multi | ✅ | ✅ | ✅ | Apache-2.0 |
| [MioTTS-2.6B](#miotts-26b) | En/Jp | ✅ | ✅ | ❌ | LFM |
| [MOSS-TTS](#moss-tts) | 20 | ✅ | ✅ | ❌ | Apache-2.0 |
| [MOSS-TTS-Nano](#moss-tts-nano) | 20 | ✅ | ✅ | ❌ | Apache-2.0 |
| [NeuTTS](#neutts) | En/Es/De/Fr | ✅ | ✅ | ❌ | Apache-2.0 |
| [OmniVoice](#omnivoice) | 600+ | ✅ | ❌ | ❌ | Apache-2.0 |
| [Orpheus-TTS](#orpheus-tts) | Multi | ✅ | ✅ | ❌ | Apache-2.0 |
| [Qwen3-TTS](#qwen3-tts) | 10 | ✅ | ✅ | ❌ | Apache-2.0 |
| [Spark-TTS](#spark-tts) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |
| [SoproTTS](#soprotts) | En | ✅ | ✅ | ❌ | Apache-2.0 |
| [SoulX-Podcast](#soulx-podcast) | Zh/En/Canto | ✅ | ✅ | ❌ | Apache-2.0 |
| [SoulX-Singer](#soulx-singer) | Zh/En/Canto | ✅ (Singing) | ✅ | ❌ | Apache-2.0 |
| [Step-Audio](#step-audio) | Zh/En/Jp | ✅ | ✅ | ✅ | Apache-2.0 |
| [Step-Audio-EditX](#step-audio-editx) | Zh/En/Jp/Ko | ✅ | ✅ | ❌ | Apache-2.0 |
| [Supertonic 2](#supertonic-2) | 5 | ❌ | ✅ | ❌ | OpenRAIL-M |
| [T5Gemma-TTS](#t5gemma-tts) | En/Zh/Jp | ✅ | ❌ | ❌ | MIT |
| [TinyTTS](#tinytts) | En | ❌ | ✅ | ❌ | Apache-2.0 |
| [VibeVoice-Realtime](#vibevoice-realtime) | Multi | ✅ | ✅ | ❌ | MIT |
| [VieNeu-TTS](#vieneu-tts) | Vi | ✅ | ✅ | ❌ | Apache-2.0 |
| [VoxCPM](#voxcpm) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |
| [VoxCPM2](#voxcpm2) | 30 | ✅ | ✅ | ❌ | Apache-2.0 |
| [Voxtral-4B-TTS](#voxtral-4b-tts) | 9 | ✅ | ✅ | ❌ | CC BY-NC 4.0 |
| [ZipVoice](#zipvoice) | Zh/En | ✅ | ✅ | ❌ | Apache-2.0 |

<!-- ## 4. Kokoro 82M

**Phù hợp cho**: Các nhóm có ngân sách hạn chế nhưng thoải mái với việc tự lưu trữ, muốn có chất lượng tốt với chi phí tối thiểu, hoặc các nhà phát triển cần toàn quyền kiểm soát mô hình để tinh chỉnh tùy chỉnh và triển khai tại biên.

**Ưu điểm**:
- Mã nguồn mở theo giấy phép Apache 2.0
- Khoảng 0,70 USD/1 triệu ký tự (chi phí tính toán tự lưu trữ), là lựa chọn rẻ nhất hiện nay
- 82 triệu tham số chạy trên CPU tầm trung mà không cần GPU
- Vượt trội hơn OpenAI TTS-1 HD về phân tích giọng nói nhân tạo mặc dù rẻ hơn hơn 100 lần

**Nhược điểm**:
- Chỉ hỗ trợ tự lưu trữ, không có API được quản lý hoặc hỗ trợ doanh nghiệp
- Hiện tại hỗ trợ 6 ngôn ngữ (tiếng Anh, tiếng Pháp, tiếng Hàn, tiếng Nhật, tiếng Quan thoại, tiếng Anh Anh)

- Chất lượng tổng thể thấp hơn so với các tùy chọn thương mại trong top 10

**Giá cả**:
Khoảng 0,70 USD/1 triệu ký tự dựa trên chi phí tính toán tự lưu trữ. Không có phí đăng ký hoặc phí API.


more-->

{{< cards >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
  {{< card link="miniconda" title="Miniconda" icon="book-open" >}}
{{< /cards >}}