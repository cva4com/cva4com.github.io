---
title: Text-to-Speech
weight: 1
prev: /tts
next: /tts/tts-open-weights
sidebar:
  open: true
---

## Speech Arena Leaderboard

Leaderboard text-to-speech APIs compared below using third-party data from [Artificial Analysis leaderboard](https://artificialanalysis.ai/text-to-speech/leaderboard) rankings (as of April 2026), production reliability metrics, and deployment flexibility, covering latency benchmarks, language coverage, and integration options.

Inworld AI TTS-1.5 Max ranks #1 with an ELO score of 1,208 based on thousands of blind user preference comparisons, with sub-250ms P90 latency.

| Range | Creator | Model | ELO | API Pricing |
| :-- | :-- | :-- | :-- | :-- |
| #1  | Inworld | Inworld TTS 1.5 Max  | 1,208 | $50 /1M chars |
| #2  | Google  | Gemini 3.1 Flash TTS | 1,204 | $36.6 /1M chars |
| #3  | ElevenLabs | Eleven v3 | 1,179 | $100 /1M chars |
| #4  | MiniMax | Speech 2.8 HD | 1,165 | $100 /1M chars |
| #5  | StepFun | Step TTS 2 (Mar 2026) | 1,153 | $50 /1M chars |
| #6  | Fish Audio | Fish Audio S2 Pro (Open Weights) | 1,130 | $15 /1M chars |
| #7  | Microsoft Azure | Azure HD 2.5 | 1,116 | $22 /1M chars |
| #8  | StepFun | Step Audio EditX (Open Weights) | 1,101 | N/A |
| #9  | OpenAI | TTS-1 | 1,101 | $15 /1M chars |
| #10 | Cartesia | Sonic 3 | 1,069 | $39 /1M chars |
| #11 | NVIDIA | Magpie-Multilingual 357M (Open Weights) | 1,063 | N/A |
| #12 | Google | Studio | 1,062 | $160 /1M chars |
| #13 | Speechify | SIMBA 1.6 | 1,058 | $10 /1M chars |
| #14 | Kokoro | Kokoro 82M v1.0 (Open Weights) | 1,056 | $0.7 /1M chars |
| #15 | Amazon | Polly Generative | 1,055 | $30.0 /1M chars |
| #16 | async | AsyncFlow V2, async | 1,051 | $8.3 /1M chars |
| #17 | Maya Research | Maya1 (Open Weights) | 1,051 | N/A |
| #18 | Mistral | Voxtral TTS (Open Weights) | 1,044 | $16 /1M chars |
| #19 | Hume AI | Octave 2 | 1,044 | $87.5 /1M chars |
| #20 | Google | Chirp 3: HD | 1,041 | $30 /1M chars |
| #21 | Resemble AI | Chatterbox HD | 1,036 | $40 /1M chars |
| #22 | Google | Journey | 1,029 | $16 0 /1M chars |
| #23 | Microsoft Azure | MAI-Voice-1 | 1,024 | N/A |
| #24 | Xiaomi | MiMo-V2-TTS | 1,021 | N/A |
| #25 | Smallest.ai | Lightning v3.1 | 1,015 | $25 /1M chars |
| #26 | Resemble AI | Chatterbox (Open Weights) | 1,007 | $25 /1M chars |
| #27 | Zyphra | Zonos-v0.1 (Open Weights) | 1,000 | $20 /1M chars |
| #28 | Rime | Arcana v3 | 975 | $40 /1M chars |
| #29 | LMNT | LMNT | 967 | $49 /1M chars |
| #30 | Murf AI | Murf Speech Gen 2 | 956 | $100 /1M chars |
| #31 | OpenVoice | OpenVoice v2 (Open Weights) | 951 | $8.3 /1M chars |
| #32 | Neuphonic | Neuphonic TTS | 938 | $20.8 /1M chars |
| #33 | Alibaba | Qwen3 TTS | 936 | N/A |
| #34 | Coqui | XTTS v2 (Open Weights) | 885 | $40.4 /1M chars |
| #35 | StyleTTS  | StyleTTS 2 (Open Weights) | 880 | $2.8 /1M chars |
| #36 | MetaVoice | MetaVoice v1 (Open Weights) | 767 | N/A |

Sub-200ms latency is now achievable through modern neural architectures, and zero-shot voice cloning from 3-15 seconds of audio has become a standard feature set rather than premium.

## Top 27 TTS AI Models by ELO

{{< youtube D8_wft9Bd84 >}}


## 1. Inworld AI TTS

### Quick Overview

Inworld holds the #1 position on the Artificial Analysis Speech Arena with its TTS 1.5 Max model (ELO 1,238). On the separate HuggingFace TTS Arena, Inworld TTS sits at #2 (ELO 1,578). The previous-generation TTS-1 Max model also ranks in the top 5.

Voice generation is competitively priced compared to alternatives (see pricing) for the top model. The same volume on the next-highest-ranked competitors runs $6,000-$20,600 depending on provider.

Under the hood, Inworld runs two model sizes: a lighter 1B-parameter model (Mini) optimized for speed, and a larger 8B-parameter model (Max) optimized for quality. Both stream audio over WebSocket or streaming the instant it's synthesized, with no buffering step. In production, that translates to sub-130ms end-to-end latency for Mini and sub-250ms for Max, measured as full-stack P90 including network overhead.

The high quality (ranked 1st on quality), competitive pricing (see pricing), and fast generation speeds (sub-250ms) make Inworld a strong choice for developers building ai voice generation applications.

### Best For

Conversational AI agents requiring natural multi-turn dialogue, language learning platforms needing expressive multilingual speech at consumer scale, and developers requiring top-ranked quality at the lowest cost per character.

### Pros
- #1 on Artificial Analysis (TTS 1.5 Max, ELO 1,238), the highest independent quality rating of any TTS model
- Competitive per-character pricing. Significantly less expensive than alternatives at comparable or higher quality
- Sub-250ms P90 end-to-end latency (Max), sub-130ms (Mini), published as full-stack numbers, not inference-only
- Free zero-shot voice cloning from 5-15 seconds of audio
- Full voice pipeline with the Realtime API, providing built-in LLM orchestration and observability
- Full on-premise deployment for enterprises needing data sovereignty, combined with model-agnostic routing across hundreds of LLMs
- SOC2 Type II, GDPR, HIPAA with BAAs, Zero Data Retention mode
- Audio markup emotion tags ([happy], [sad], [whispering]) and non-verbals ([cough], [sigh], [breathe])

### Cons
- 15 languages supported. If you need broader language coverage today, this is a real gap. The major commercial markets (English, Spanish, French, Korean, Chinese, Japanese, German, and more) are covered, but niche accents and smaller languages aren't available yet.
- TTS product launched June 2025. Less than a year of production track record compared to established providers with multi-year deployment histories.

### Pricing
- See pricing for current TTS rates
- Zero-shot voice cloning: Free
- Free tier: 2M characters for new users
- On-premise: Custom enterprise pricing

### Voice of the User

Talkpal AI, a language learning platform with 5M+ users, integrated Inworld TTS across their entire user base. A/B testing showed 40% cost reduction, 7% increase in feature usage, and 4% lift in retention within four weeks. Bible Chat scaled AI voice features to millions of users while reducing costs by over 90% compared to their previous TTS provider.


## 2. Google Cloud Text-to-Speech

### Best For

Global enterprises requiring extensive language coverage and GCP infrastructure integration.

### Pros
- 380+ voices across 75+ languages provides unmatched global coverage for multilingual applications
- Direct GCP integration with Compute Engine, Cloud Storage, and BigQuery reduces infrastructure complexity
- SSML support enables pauses, pronunciation, and date/time formatting customization
- 1M free characters monthly for standard voices supports development testing
- Gemini 3.1 models with prompt-based control and multi-speaker dialogue capabilities

### Cons
- Limited emotional expressiveness with some voices feeling robotic compared to specialized providers
- Complex GCP setup requires billing enablement, service accounts, and JSON key management
- Catastrophic speed drops reported with Chirp3-HD voices where 5 minutes of audio took over 10 minutes to generate

### Pricing
Gemini 3.1 Flash TTS costs $0.50 per million input tokens and $10.00 per million audio output tokens. Chirp 3 HD costs $30 per million characters after 1 million free. WaveNet costs $4 per million characters after 4 million free.


## 3. ElevenLabs

### Quick Overview

ElevenLabs started in content creation (audiobooks, voiceovers, dubbing) and the product still reflects its content-creation origins. Eleven v3 sits at #2 on Artificial Analysis (ELO 1,179), with four models in the top 12. The platform includes dubbing, voice isolation, and sound effects alongside TTS, which makes it broad but also means the core TTS competes at a significant price premium against more focused providers.

### Best For

Content creators and production teams who need audiobooks, podcast voiceovers, dubbing, and voice isolation in a single platform. Teams requiring 70+ languages with extensive voice variety.

### Pros
- Broadest language support in the category (70+ languages with v3)
- Large community voice library (10,000+) for quick prototyping
- Bundled content creation tools: dubbing, voice isolation, sound effects
- Mature third-party integration ecosystem

### Cons
- $60-120/1M characters puts it at significantly higher cost than Inworld (see pricing) for comparable or lower-ranked quality
- No model-agnostic LLM routing across providers

### Pricing
Subscription tiers with character quotas. Multilingual v2/v3: ~$120/1M chars. Flash/Turbo v2.5: ~$60/1M chars. Free tier with 10,000 characters for testing.


## 4. MiniMax Speech

### Quick Overview

MiniMax has four models in the top 8 on Artificial Analysis, the highest concentration of top-ranked models from any single provider. Speech-02-Turbo sits at #4 (ELO 1,107). Backed by Alibaba and Tencent with a $2B+ valuation, the company is strongest in Asian markets. The long-text mode processes up to 200,000 characters per request, which matters for audiobook-length generation. Pricing runs significantly higher than Inworld for quality that ranks lower on the same leaderboard.

### Best For

Teams needing consistent quality across multiple model variants, strong Asian language support (particularly Cantonese and Mandarin), or bulk long-form audio generation.

### Pros
- Four models in the top 8 on Artificial Analysis, the densest presence of any single provider
- 32 languages with strong CJK coverage
- Long-text mode handles 200K characters per request (entire audiobooks without segmentation)
- 99% voice cloning similarity from 10 seconds of audio

### Cons
- $60-100/1M characters, which is significantly more expensive than Inworld for lower-ranked quality
- Smaller developer ecosystem and documentation in Western markets

### Pricing

Speech-02-Turbo: ~$60/1M characters. Speech-02-HD / Speech 2.6 HD: ~$100/1M characters.


## 9. OpenAI TTS-1

### Quick Overview

OpenAI's TTS-1 ranks #3 on Artificial Analysis (ELO 1,111). The primary value proposition is ecosystem convenience: if you're already on OpenAI's LLMs, adding TTS through the same API and billing avoids another vendor relationship. The gpt-4o-mini-tts model uses natural language prompts for voice styling ("speak calmly," "sound excited") instead of SSML tags, which is a different approach but limits fine-grained control.

### Best For

Teams already deep in the OpenAI ecosystem who want a single-vendor stack with minimal integration overhead. Developers who value prompt-based voice styling over traditional SSML controls.

### Pros
- Prompt-based voice styling via gpt-4o-mini-tts (no SSML required)
- 50+ languages, single billing relationship for teams already on OpenAI
- Realtime API for voice-to-voice applications
- Low integration overhead for existing OpenAI SDK users

### Cons
- No voice cloning capability
- No on-premise deployment option
- Limited customization compared to dedicated TTS providers

### Pricing
TTS-1: $15/1M characters. TTS-1 HD: $30/1M characters. Pay-as-you-go, no free tier for TTS specifically.


## 10. Cartesia Sonic

### Quick Overview

Cartesia optimizes for one thing: latency. Sonic 3 delivers 90ms time-to-first-audio using State Space Models (SSMs) instead of transformers, an architectural choice that prioritizes speed over quality ceiling. The company raised $100M led by Kleiner Perkins, Index Ventures, Lightspeed, and NVIDIA. Whether 90ms vs. 250ms matters depends on your application; for most voice agents, both feel instantaneous to users.

### Best For

Applications where absolute minimum time-to-first-audio is the top priority: telephony systems, live customer service agents, and interactive experiences where 90ms vs. 250ms makes a perceptible difference.

### Pros
- 90ms TTFA, fastest in the market by a significant margin
- 42 languages with emotional range including natural laughter
- Available on AWS SageMaker JumpStart for cloud-native deployment
- SSM architecture enables linear scaling for edge computing use cases

### Cons
- Credit-based pricing makes true per-character cost harder to predict
- Ranked 10 in the Artificial Analysis quality leaderboard

### Pricing
Credit-based plans. Free: 10,000 credits. Pro: $5/mo for 100,000 credits. Startup: $49/mo for 1.25M credits. Scale: $299/mo for 8M credits. Voice agent usage reported at $0.06/min, dropping to ~$0.014/min at higher tiers.


## 14. Kokoro 82M

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