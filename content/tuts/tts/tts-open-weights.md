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
| #12 | Coqui | [XTTS v2](https://huggingface.co/coqui/XTTS-v2) | 885 | $40.4 /1M chars |
| #13 | StyleTTS  | [StyleTTS 2](https://github.com/yl4579/StyleTTS2) | 877 | $2.8 /1M chars |
| #14 | MetaVoice | [MetaVoice v1](https://github.com/metavoiceio/metavoice-src) | 764 | N/A |

Sub-200ms latency is now achievable through modern neural architectures, and zero-shot voice cloning from 3-15 seconds of audio has become a standard feature set rather than premium.

## Top 27 TTS AI Models by ELO

{{< youtube D8_wft9Bd84 >}}


## 4. Kokoro 82M

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

<!--more-->

{{< cards >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
  {{< card link="miniconda" title="Miniconda" icon="book-open" >}}
{{< /cards >}}