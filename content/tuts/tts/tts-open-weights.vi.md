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
| #4 | [Kokoro](https://youtu.be/-VLmk9PqOYo) | [Kokoro 82M v1.0](https://huggingface.co/hexgrad/Kokoro-82M) | 1,055 | $0.7 /1M chars |
| #5 | Mistral | [Voxtral TTS](https://huggingface.co/mistralai/Voxtral-4B-TTS-2603) | 1,053 | $16 /1M chars |
| #6 | Maya Research | [Maya1](https://huggingface.co/maya-research/maya1) | 1,049 | N/A |
| #7 | Fish Audio | [Fish Audio 1.5](https://huggingface.co/fishaudio/fish-speech-1.5) | 1,012 | $15 /1M chars |
| #8 | Resemble AI | [Chatterbox](https://github.com/resemble-ai/chatterbox) | 1,006 | $25 /1M chars |
| #9 | Zyphra | [Zonos-v0.1](https://github.com/Zyphra/Zonos) | 1,000 | $20 /1M chars |
| #10 | Microsoft | [VibeVoice](https://huggingface.co/microsoft/VibeVoice-1.5B) 7B | 957 | N/A |
| #11 | OpenVoice | [OpenVoice v2](https://huggingface.co/myshell-ai/OpenVoiceV2) | 948 | $8.3 /1M chars |
| #12 | [Alibaba](https://youtu.be/a00--jPR9Ns) | [Qwen3 TTS](https://github.com/QwenLM/Qwen3-TTS) | 932 | N/A |
| #13 | Coqui | [XTTS v2](https://huggingface.co/coqui/XTTS-v2) | 885 | $40.4 /1M chars |
| #14 | StyleTTS  | [StyleTTS 2](https://github.com/yl4579/StyleTTS2) | 877 | $2.8 /1M chars |
| #15 | MetaVoice | [MetaVoice v1](https://github.com/metavoiceio/metavoice-src) | 764 | N/A |

Độ trễ dưới 200ms hiện nay đã có thể đạt được nhờ các kiến ​​trúc mạng thần kinh hiện đại, và việc sao chép giọng nói không cần huấn luyện từ đoạn âm thanh dài 3-15 giây đã trở thành tính năng tiêu chuẩn chứ không còn là tính năng cao cấp nữa.

## Top 27 mô hình AI TTS theo xếp hạng theo ELO

{{< youtube D8_wft9Bd84 >}}


## Top 45 mô hình AI TTS trên GitHub

| Model | Parameters | Languages | Voice Cloning | Streaming | [Pronounce](## "Pronunciation Control") | [Emotion](## "Emotion Control") | ASR | Other | License |
| :--- | :--- | :---: | :---: | :---: | :--- | :--- | :--- | :--- | :--- |
| [Audio Flamingo](https://github.com/NVIDIA/audio-flamingo) | [7B](https://huggingface.co/nvidia/audio-flamingo-3) - [Website](https://afnext-umd-nvidia.github.io) | Multi-lingual | ❌ | ✅ | N/A | ✅ | ✅ | Context Up to 30 minutes | [Apache](https://github.com/NVIDIA/audio-flamingo "Apache License Version 2.0") |
| [Chatterbox](https://github.com/resemble-ai/chatterbox) | [350M-500M](https://www.resemble.ai) | 23+ | ✅ | ✅ | ✅ | [✅](## "✅ (Tags)") | ❌ |  | [MIT](https://github.com/resemble-ai/chatterbox "MIT License") |
| [Dia](https://github.com/nari-labs/dia) | [1.6B](https://huggingface.co/nari-labs/Dia-1.6B-0626) | English | ✅ | ✅ | ✅ | ✅ | ❌ | | [Apache](https://github.com/nari-labs/dia) |
| [FireRedTTS-2](https://github.com/FireRedTeam/FireRedTTS2) | [Hugging Face](https://huggingface.co/FireRedTeam/FireRedTTS2) - [arXiv](https://arxiv.org/abs/2509.02020) | 7 (En, Zh, Jp, Ko, Fr, De, Ru) | ✅ | ✅ (140ms) | ✅ | ✅ | ✅ | 4 speakers; 3 minutes | [Apache](https://github.com/FireRedTeam/FireRedTTS2) |
| [Fish Audio S2 Pro](https://github.com/fishaudio/fish-speech) | [5B](https://huggingface.co/fishaudio/s2-pro "5B (4B Slow AR + 400M Fast AR)") | 80+ (Tier 1: En, Zh, Jp) | ✅ | [✅](## "✅ (RTF 0.195, 100ms TTFA)") | [✅](## "✅ (15,000+ tags)") | [✅](## "✅ (fine-grained inline control)") | ❌ | ~10 GB (BF16) | [License](https://github.com/fishaudio/fish-speech/blob/main/LICENSE "Fish Audio Research License") |
| [Fish Speech](https://github.com/fishaudio/fish-speech) | [4B](https://fish.audio) | 8 (En, Jp, Ko, Zh, Fr, De, Ar, Es) | ✅ | ✅ | ✅ | ✅ | ❌ | RTF ~1:7 | [Apache](https://github.com/fishaudio/fish-speech) |
| [Fun-CosyVoice 3.0](https://github.com/FunAudioLLM/CosyVoice) | [0.5B](https://huggingface.co/FunAudioLLM/Fun-CosyVoice3-0.5B-2512) - [arXiv](https://arxiv.org/abs/2505.17589) | 9 + 18+ Chinese dialects | [✅](## "✅ (Multi-lingual/Cross-lingual)") | [✅](## "✅ (150ms)") | [✅](## "✅ (Pinyin/CMU)") | ✅ | ❌ |  | [Apache](https://github.com/FunAudioLLM/CosyVoice) |
| [GLM-TTS](https://github.com/zai-org/GLM-TTS) | [Hugging Face](https://huggingface.co/zai-org/GLM-TTS) - [arXiv](https://arxiv.org/abs/2512.14291) | Chinese, English | [✅](## "✅ (3-10s)") | ✅ | [✅](## "✅ (Phoneme-level)") | [✅](## "✅ (RL-enhanced)") | ❌ | | [Apache](https://github.com/zai-org/GLM-TTS) |
| [IndexTTS2](https://github.com/xuchenxu168/Comfyui-Index-TTS2) | [_](https://huggingface.co/IndexTeam/IndexTTS-2) | Chinese, English | ✅ | ✅ | ✅ | [✅](## "✅ 5 emotions") | ❌ | 1–4 speakers | [Apache](https://github.com/xuchenxu168/Comfyui-Index-TTS2) |
| [Irodori-TTS-500M-v2](https://github.com/Aratako/Irodori-TTS) | [500M](https://huggingface.co/Aratako/Irodori-TTS-500M-v2) | Japanese | ✅ | ❌ | ❌ | [✅](## "✅ emoji-based") | ❌ | 48kHz waveform | [MIT](https://github.com/Aratako/Irodori-TTS) |
| [Kimi-Audio](https://github.com/MoonshotAI/Kimi-Audio) | [7B](https://huggingface.co/moonshotai/Kimi-Audio-7B) | Multiple | ✅ | ✅ | N/A | ✅ | ✅ | | [MIT & Apache](https://github.com/MoonshotAI/Kimi-Audio) |
| [KittenTTS](https://github.com/KittenML/KittenTTS) | [15M int8](https://huggingface.co/KittenML/kitten-tts-nano-0.8-int8) [15M](https://huggingface.co/KittenML/kitten-tts-nano-0.8-fp32) [40M](https://huggingface.co/KittenML/kitten-tts-micro-0.8) [80M](https://huggingface.co/KittenML/kitten-tts-mini-0.8) | English, Multiple | ✅ | ✅ | ❌ | ✅ | ❌ | <25MB, no GPU | [Apache](https://github.com/KittenML/KittenTTS) |
| [Kokoro-82M](https://youtu.be/-VLmk9PqOYo) | [82M](https://huggingface.co/hexgrad/Kokoro-82M) | 8 langs, [54 voices](https://huggingface.co/spaces/hexgrad/Kokoro-TTS) | ✅ | [✅](## "✅ (generator pattern))") | [✅](## "✅ (via misaki G2P)") | [✅](## "✅ (voice styles)") | ❌ | <$0.06/hr audio | [Apache](https://github.com/hexgrad/kokoro) |
| [KokoClone](https://github.com/Ashish-Patnaik/kokoclone) | [Base: Kokoro-ONNX](https://huggingface.co/PatnaikAshish/kokoclone) | 7 (En, Hi, Fr, Ja, Zh, It, Pt, Es) | [✅](## "✅ (3-10s reference)") | [✅](## "✅ (CPU real-time)") | ❌ | ✅ | ❌ | | [Apache](https://github.com/Ashish-Patnaik/kokoclone) |
| [KugelAudio](https://github.com/Kugelaudio/kugelaudio-open) | [7B](https://huggingface.co/kugelaudio/kugelaudio-0-open) | 23 EU langs | ✅ | ✅ | ✅ | [✅](## "✅ (Speaking styles)") | ❌ | [Website](https://kugelaudio.com) | [MIT](https://github.com/Kugelaudio/kugelaudio-open) |
| [LEMAS-TTS](https://github.com/LEMAS-Project/LEMAS-TTS) | [0.3B](https://huggingface.co/LEMAS-Project/LEMAS-TTS) [Website](https://lemas-project.github.io/LEMAS-Project/) | 10 (Zh, En, Es, Ru, Fr, De, It, Pt, Id, Vi) | ✅ | ❌ | ✅ | ✅ | ❌ | Word-level editing (LEMAS-Edit) | [Apache](https://github.com/LEMAS-Project/LEMAS-TTS) |
| [LFM2-Audio-1.5B](https://github.com/Liquid4All/liquid-audio) | [1.5B](https://huggingface.co/LiquidAI/LFM2-Audio-1.5B) | English | ✅ | ✅ | N/A | ✅ | [✅](## "✅ (Integrated)") | [Website](https://docs.liquid.ai/lfm) | [LFM Open](https://github.com/Liquid4All/liquid-audio "LFM Open License v1.0") |
| [LongCat-AudioDiT](https://github.com/meituan-longcat/LongCat-AudioDiT) | [1B](https://huggingface.co/meituan-longcat/LongCat-AudioDiT-1B) / [3.5B](https://huggingface.co/meituan-longcat/LongCat-AudioDiT-3.5B) | Chinese, English | ✅ | ❌ | ❌ | ❌ | ❌ | Rate 24000 Hz | [MIT](https://github.com/meituan-longcat/LongCat-AudioDiT) |
| [LuxTTS](https://github.com/ysharma3501/LuxTTS) | [_](https://huggingface.co/YatharthS/LuxTTS) | — | ✅ | ✅ | ❌ | ❌ | ❌ | RTF 150×, 1GB VRAM | [Apache](https://github.com/ysharma3501/LuxTTS) |
| [Maya1](https://www.mayaresearch.ai) | [3B](https://huggingface.co/maya-research/maya1) | En (multi-accent) | ✅ | [✅](## "✅ (<100ms)") | ✅ | [✅](## "✅ (Tags)") | ❌ | [Website](https://www.mayaresearch.ai) | [Apache](https://huggingface.co/maya-research/maya1) |
| [MegaTTS3](https://github.com/bytedance/MegaTTS3) | [0.45B](https://huggingface.co/ByteDance/MegaTTS3) | Chinese, English | ✅ | ✅ | ✅ | ✅ | ❌ | [arXiv](https://arxiv.org/abs/2502.18924) | [Apache](https://github.com/bytedance/MegaTTS3) |
| [MiMo-Audio](https://github.com/XiaomiMiMo/MiMo-Audio) | [7B](https://huggingface.co/collections/XiaomiMiMo/mimo-audio) | Multi-lingual | ✅ | ✅ | N/A | ✅ | ✅ | Few-shot learner | [Apache](https://github.com/XiaomiMiMo/MiMo-Audio) |
| [MioTTS-2.6B](https://github.com/Aratako/MioTTS-Inference) | [2.6B](https://huggingface.co/Aratako/MioTTS-2.6B) | English, Japanese | ✅ | ✅ | ❌ | ❌ | ❌ | RTF 0.135–0.145 | [LFM Open](https://github.com/Aratako/MioTTS-Inference) |
| [MOSS-TTS](https://github.com/OpenMOSS/MOSS-TTS) | [8B Delay, 1.7B Local](https://huggingface.co/OpenMOSS-Team/MOSS-TTS) | 20 langs | ✅ | ✅ | [✅](## "✅ (Pinyin/Phoneme-level)") | ✅ | ❌ | Max 1 hour | [Apache](https://github.com/OpenMOSS/MOSS-TTS) |
| [MOSS-TTS-Nano](https://github.com/OpenMOSS/MOSS-TTS-Nano) | [0.1B](https://huggingface.co/OpenMOSS-Team/MOSS-TTS-Nano-100M) | 20 langs | ✅ | [✅](## "✅ (CPU-friendly)") | ❌ | ❌ | ❌ | 48 kHz Stereo | [Apache](https://github.com/OpenMOSS/MOSS-TTS-Nano) |
| [NeuTTS](https://github.com/neuphonic/neutts) | [360M Air](https://huggingface.co/neuphonic/neutts-air) / [120M Nano](https://huggingface.co/neuphonic/neutts-nano) | En/Es/De/Fr | [✅](## "✅ (3-second)") | ✅ | ❌ | ❌ | ❌ | GGUF on-device | [Apache](https://github.com/neuphonic/neutts "for NeuTTS Air") / [NeuTTS](https://github.com/neuphonic/neutts "NeuTTS Open License for NeuTTS Nano") |
| [OmniVoice](https://github.com/k2-fsa/OmniVoice) | [_](https://huggingface.co/k2-fsa/OmniVoice) | 600+ langs | ✅ | ❌ | [✅](## "✅ (Pinyin/CMU)") | [✅](## "✅ (Voice Design)") | ❌ | 581k hours | [Apache](https://github.com/k2-fsa/OmniVoice) |
| [Orpheus-TTS](https://github.com/canopyai/Orpheus-TTS) | [3B](https://huggingface.co/canopylabs/orpheus-3b-0.1-ft) | Multilingual | ✅ | [✅](## "✅ (200ms)") | ✅ | ✅ | ❌ | Llama-3b backbone | [Apache](https://github.com/canopyai/Orpheus-TTS) |
| [Qwen3-TTS](https://youtu.be/a00--jPR9Ns) | [0.6B–1.7B](https://huggingface.co/collections/Qwen/qwen3-tts) | 10 (Zh, En, Ja, Ko, De, Fr, Ru, Pt, Es, It) | [✅](## "✅ (3-second)") | [✅](## "✅ (97ms latency)") | ✅ | ✅ | ❌ | [arXiv](https://arxiv.org/abs/2601.15621) | [Apache](https://github.com/QwenLM/Qwen3-TTS) |
| [SoproTTS](https://github.com/samuel-vitorino/sopro) | [135M](https://huggingface.co/samuel-vitorino/sopro) | English | [✅](## "✅ (3-12s)") | [✅](## "✅ (250ms TTFA)") | ❌ | [✅](## "✅ (style_strength)") | ❌ | RTF 0.05 CPU M3 | [Apache](https://github.com/samuel-vitorino/sopro) |
| [SoulX](https://github.com/Soul-AILab)-[Podcast](https://github.com/Soul-AILab/SoulX-Podcast) | [Hugging Face](https://huggingface.co/collections/Soul-AILab/soulx-podcast), [arXiv](https://arxiv.org/abs/2510.23541) | Mandarin, English, Cantonese, Sichuanese, Henanese | ✅ | ✅ | ✅ | ✅ | ❌ | Max 90+ min | [Apache](https://github.com/Soul-AILab/SoulX-Podcast) |
| [SoulX-Singer](https://github.com/Soul-AILab/SoulX-Singer) | [Hugging Face](https://huggingface.co/spaces/Soul-AILab/SoulX-Singer), [arXiv](https://arxiv.org/abs/2602.07803) | Mandarin, English, Cantonese | [✅](## "✅ (Singing)") | ✅ | [✅](## "✅ (MIDI/F0)") | ✅ | ❌ | Singing synthesis | [Apache](https://github.com/Soul-AILab/SoulX-Singer) |
| [Spark-TTS](https://github.com/SparkAudio/Spark-TTS) | [0.5B](https://huggingface.co/SparkAudio/Spark-TTS-0.5B) | Chinese, English | ✅ | ✅ | ✅ | ✅ | ❌ | [Qwen2.5 backbone](https://arxiv.org/abs/2503.01710) | [Apache](https://github.com/SparkAudio/Spark-TTS) |
| [Step-Audio](https://github.com/stepfun-ai/Step-Audio2) | [130B Chat](https://huggingface.co/stepfun-ai/Step-Audio-Chat) / [3B TTS](https://huggingface.co/stepfun-ai/Step-Audio-TTS-3B) | Zh, En, Jp | ✅ | ✅ | ✅ | ✅ | ✅ | [arXiv](https://arxiv.org/abs/2502.11946) | [Apache](https://github.com/stepfun-ai/Step-Audio2) |
| [Step-Audio-EditX](https://github.com/stepfun-ai/Step-Audio-EditX) | [3B (4B BF16)](https://huggingface.co/stepfun-ai/Step-Audio-EditX) | Mandarin, English, Sichuanese, Cantonese, Japanese, Korean | ✅ | ✅ | [✅](## "✅ (Polyphone)") | [✅](## "✅ (14 emotions)") | ❌ | [Audio editing](https://arxiv.org/abs/2511.03601) | [Apache](https://github.com/stepfun-ai/Step-Audio-EditX) |
| [Supertonic 3](https://youtu.be/hA6G0L_ebYs) | [66M](https://huggingface.co/Supertone/supertonic-2) | 31 (Ar, Bg, Hr, Cs, Da, Nl, En, Et, Fi, Fr, De, El, Hi, Hu, Id, It, Ja, Ko, Lv, Lt, Pl, Pt, Ro, Ru, Sk, Sl, Es, Sv, Tr, Uk, Vi) | ❌ | ✅ | ❌ | ❌ | ❌ | RTF 0.001, ONNX | [OpenRAIL-M](https://github.com/supertone-inc/supertonic) |
| [T5Gemma-TTS](https://github.com/Aratako/T5Gemma-TTS) | [2B-2B](https://huggingface.co/Aratako/T5Gemma-TTS-2b-2b) | English, Chinese, Japanese | ✅ | ❌ | ✅ | ❌ | ❌ | 7.6-10.6 GB VRAM | [MIT](https://github.com/Aratako/T5Gemma-TTS) |
| [TinyTTS](https://github.com/tronghieuit/tiny-tts) | [1.6M](https://huggingface.co/backtracking/tiny-tts) | English | ❌ | [✅](## "✅ (~53x RTF)") | ✅ | ❌ | ❌ | ~3.4 MB (ONNX FP16) | [Apache](https://github.com/tronghieuit/tiny-tts) |
| [VibeVoice-Realtime](https://github.com/microsoft/VibeVoice) | [0.5B](https://huggingface.co/microsoft/VibeVoice-Realtime-0.5B) | 50+ langs | ✅ | [✅](## "✅ (300ms)") | ✅ | ✅ | ❌ | Max ~10 min | [MIT](https://github.com/microsoft/VibeVoice) |
| [VieNeu-TTS](https://github.com/pnnbao97/VieNeu-TTS) | [0.3B–0.6B](https://huggingface.co/pnnbao-ump/VieNeu-TTS) | Vietnamese, English | [✅](## "✅ (3-5s)") | [✅](## "✅ (On-device)") | ✅ | ❌ | ❌ | | [Apache](https://github.com/pnnbao97/VieNeu-TTS) |
| [VoxCPM](https://github.com/OpenBMB/VoxCPM) | [640M](https://huggingface.co/openbmb/VoxCPM-0.5B)–[800M](https://huggingface.co/openbmb/VoxCPM1.5) | 30 (Ar, My, Zh, Da, Nl, En, Fi, Fr, De, El, He, Hi, Id, It, Ja, Km, Ko, Lo, Ms, No, Pl, Pt, Ru, Es, Sw, Sv, Tl, Th, Tr, Vi, 四川话, 粤语, 吴语, 东北话, 河南话, 陕西话, 山东话, 天津话, 闽南话) | ✅ | [✅](## "✅ (RTF 0.17)") | ✅ | ✅ | ❌ | [Tokenizer-free](https://arxiv.org/abs/2509.24650) | [Apache](https://github.com/OpenBMB/VoxCPM) |
| [VoxCPM2](https://github.com/OpenBMB/VoxCPM) | [2B](https://huggingface.co/openbmb/VoxCPM2) | 30 (Ar, My, Zh, Da, Nl, En, Fi, Fr, De, El, He, Hi, Id, It, Ja, Km, Ko, Lo, Ms, No, Pl, Pt, Ru, Es, Sw, Sv, Tl, Th, Tr, Vi, 四川话, 粤语, 吴语, 东北话, 河南话, 陕西话, 山东话, 天津话, 闽南话) | ✅ | [✅](## "✅ (RTF ~0.3)") | ✅ | [✅](## "✅ (Voice Design)") | ❌ | 48 kHz | [Apache](https://github.com/OpenBMB/VoxCPM) |
| Voxtral-4B-TTS | [4B](https://huggingface.co/mistralai/Voxtral-4B-TTS-2603) | 9 (En, Fr, Es, De, It, Pt, Nl, Ar, Hi) | ✅ | [✅](## "✅ (RTF 0.103 at concurrency 1)") | ❌ | [✅](## "✅ (expressive speech)") | ❌ | 24 kHz | [CC BY-NC 4.0](https://huggingface.co/mistralai/Voxtral-4B-TTS-2603) |
| [ZipVoice](https://github.com/k2-fsa/ZipVoice) | [123M](https://arxiv.org/abs/2506.13053) | Chinese, English | ✅ | ✅ | ❌ | ❌ | ❌ | [Dialogue support](https://zipvoice.github.io) | [Apache](https://github.com/k2-fsa/ZipVoice) |



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