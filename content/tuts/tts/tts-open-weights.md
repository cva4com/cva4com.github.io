---
linkTitle: TTS Open
title: Text-to-Speech Open Weights
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

## Speech Arena Leaderboard

Leaderboard text-to-speech APIs compared below using third-party data from [Artificial Analysis leaderboard](https://artificialanalysis.ai/text-to-speech/leaderboard) rankings (as of April 2026), production reliability metrics, and deployment flexibility, covering latency benchmarks, language coverage, and integration options.

Inworld AI TTS-1.5 Max ranks #1 with an ELO score of 1,208 based on thousands of blind user preference comparisons, with sub-250ms P90 latency.

| Range | Creator | Model | ELO | API Pricing |
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

Sub-200ms latency is now achievable through modern neural architectures, and zero-shot voice cloning from 3-15 seconds of audio has become a standard feature set rather than premium.

## Top 27 TTS AI Models by ELO

{{< youtube D8_wft9Bd84 >}}


## Top 45 TTS & Voice Generation Models from GitHub

| Model | Languages | Voice Cloning | Streaming | ASR | License |
| :--- | :--- | :---: | :---: | :---: | :--- |
| [Chatterbox](#chatterbox) | 23+ | ✅ | ✅ | ❌ | MIT |
| [Dia](#dia) | En | ✅ | ✅ | ❌ | Apache |
| [FireRedTTS2](#fireredtts2) | 7 langs | ✅ | ✅ | ❌ | Apache |
| [Fish Audio S2 Pro](#fish-audio-s2-pro) | 80+ | ✅ | ✅ | ❌ | Research License |
| [Fish Speech](#fish-speech) | 8 langs | ✅ | ✅ | ❌ | Apache |
| [Fun-CosyVoice 3.0](#fun-cosyvoice-30) | 9 + 18 dialects | ✅ | ✅ | ❌ | Apache |
| [GLM-TTS](#glm-tts) | Zh/En | ✅ | ✅ | ❌ | Apache |
| [IndexTTS2](#indextts2) | Zh/En | ✅ | ✅ | ❌ | Apache |
| [Irodori-TTS-500M-v2](#irodori-tts-500m-v2) | Jp | ✅ | ❌ | ❌ | MIT |
| [Kimi-Audio](#kimi-audio) | Multi | ✅ | ✅ | ✅ | MIT/Apache |
| [KittenTTS](#kittenTTS) | En+ | ✅ | ✅ | ❌ | Apache |
| [Kokoro-82M](#kokoro-82m) | 8 (54 voices) | ✅ | ✅ | ❌ | Apache |
| [KokoClone](#kokoclone) | 7 | ✅ | ✅ | ❌ | Apache |
| [KugelAudio](#kugelaudio) | 23 EU | ✅ | ✅ | ❌ | MIT |
| [LEMAS-TTS](#lemas-tts) | 10 | ✅ | ❌ | ❌ | Apache |
| [LFM2-Audio-1.5B](#lfm2-audio-15b) | En | ✅ | ✅ | ✅ | LFM |
| [LongCat-AudioDiT](#longcat-audiodit) | Zh/En | ✅ | ❌ | ❌ | MIT |
| [LongCat-Next](#longcat-next) | Zh/En | ✅ | ✅ | ✅ | MIT |
| [LuxTTS](#luxtts) | - | ✅ | ✅ | ❌ | Apache |
| [Maya1](#maya1) | En | ✅ | ✅ | ❌ | Apache |
| [MegaTTS3](#megatts3) | Zh/En | ✅ | ✅ | ❌ | Apache |
| [MiMo-Audio](#mimo-audio) | Multi | ✅ | ✅ | ✅ | Apache |
| [MioTTS-2.6B](#miotts-26b) | En/Jp | ✅ | ✅ | ❌ | LFM |
| [MOSS-TTS](#moss-tts) | 20 | ✅ | ✅ | ❌ | Apache |
| [MOSS-TTS-Nano](#moss-tts-nano) | 20 | ✅ | ✅ | ❌ | Apache |
| [NeuTTS](#neutts) | En/Es/De/Fr | ✅ | ✅ | ❌ | Apache |
| [OmniVoice](#omnivoice) | 600+ | ✅ | ❌ | ❌ | Apache |
| [Orpheus-TTS](#orpheus-tts) | Multi | ✅ | ✅ | ❌ | Apache |
| [Qwen3-TTS](#qwen3-tts) | 10 | ✅ | ✅ | ❌ | Apache |
| [Spark-TTS](#spark-tts) | Zh/En | ✅ | ✅ | ❌ | Apache |
| [SoproTTS](#soprotts) | En | ✅ | ✅ | ❌ | Apache |
| [SoulX-Podcast](#soulx-podcast) | Zh/En/Canto | ✅ | ✅ | ❌ | Apache |
| [SoulX-Singer](#soulx-singer) | Zh/En/Canto | ✅ (Singing) | ✅ | ❌ | Apache |
| [Step-Audio](#step-audio) | Zh/En/Jp | ✅ | ✅ | ✅ | Apache |
| [Step-Audio-EditX](#step-audio-editx) | Zh/En/Jp/Ko | ✅ | ✅ | ❌ | Apache |
| [Supertonic 2](#supertonic-2) | 5 | ❌ | ✅ | ❌ | OpenRAIL-M |
| [T5Gemma-TTS](#t5gemma-tts) | En/Zh/Jp | ✅ | ❌ | ❌ | MIT |
| [TinyTTS](#tinytts) | En | ❌ | ✅ | ❌ | Apache |
| [VibeVoice-Realtime](#vibevoice-realtime) | Multi | ✅ | ✅ | ❌ | MIT |
| [VieNeu-TTS](#vieneu-tts) | Vi | ✅ | ✅ | ❌ | Apache |
| [VoxCPM](#voxcpm) | Zh/En | ✅ | ✅ | ❌ | Apache |
| [VoxCPM2](#voxcpm2) | 30 | ✅ | ✅ | ❌ | Apache |
| [Voxtral-4B-TTS](#voxtral-4b-tts) | 9 | ✅ | ✅ | ❌ | CC BY-NC 4.0 |
| [ZipVoice](#zipvoice) | Zh/En | ✅ | ✅ | ❌ | Apache |



<!-- ## 4. Kokoro 82M

### Quick Overview

Kokoro is the open-source option. At 82 million parameters, it runs on mid-tier CPUs without a GPU and scores ELO 1,060 on Artificial Analysis (#16, ahead of OpenAI's TTS-1 HD). The tradeoff is that you host and maintain it yourself, there's no managed API, and the language and voice selection is limited. Good for prototyping or cost-constrained teams with DevOps capacity.

### Best For

Budget-constrained teams comfortable with self-hosting who want decent quality at minimal cost, or developers who need full control over the model for custom fine-tuning and edge deployment.

### Pros

- Open-source under Apache 2.0 license
- ~$0.70/1M characters (self-hosted compute cost), making it the cheapest option by far
- 82M parameters runs on mid-tier CPUs with no GPU requirement
- Outranks OpenAI TTS-1 HD on Artificial Analysis despite being 100x+ cheaper

### Cons

- Self-hosted only with no managed API or enterprise support
- 6 languages currently (English, French, Korean, Japanese, Mandarin, British English)
- Lower overall quality than commercial options in the top 10

### Pricing

~$0.70/1M characters based on self-hosted compute costs. No subscription or API fees.

more-->

{{< cards >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
  {{< card link="miniconda" title="Miniconda" icon="book-open" >}}
{{< /cards >}}