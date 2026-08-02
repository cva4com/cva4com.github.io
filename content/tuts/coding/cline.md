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

Cline is the most autonomous free agent I've used. Install the VS Code extension, configure a BYOK provider, give it a task, and watch it work. It reads files, writes code, runs terminal commands, handles errors, and iterates — often without prompting you between steps.

The tradeoff is cost visibility. Because it's aggressive about tool use, a single Cline session on Claude Sonnet can easily cost $5-10. Pair it with a cheaper model for routine work. Gemini 2.5 Flash and GPT-5 Mini both do surprisingly well at a fraction of the price.

Best for: Developers who want "press go and walk away" behavior without leaving VS Code.

## List of free AI models supported by Cline

Based on the OpenRouter configuration file stored in Cline
`C:\Users\<username>\AppData\Roaming\Code\User\globalStorage\saoudrizwan.claude-dev\cache\openrouter_models.json`
the following completely free models (input value = 0 and output value = 0) are supported:


## 🤖 Free models (input & output = 0)

| Model ID | Model Name | Context |
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


## 💡 Recommendations for programming

The best free models for coding tasks among those listed above are:

1. **NVIDIA Nemotron 3 Ultra** (free) — 550B, large context, strong reasoning
2. **NVIDIA Nemotron 3 Super** (free) — 120B, optimized for multi-agent programming
3. **Cohere North Mini Code** (free) — specialized for coding agents
4. **Poolside Laguna S 2.1** (free) — coding agent model
5. **OpenAI gpt-oss-20b** (free) — open-weighted OpenAI programming

You can use `openrouter/free` to automatically select the best free model for each task.


## 🌐 Free router

- **`openrouter/free`** — *Free Models Router*: Automatically select a free model randomly from OpenRouter's list of free models (200K context).


## ⚠️ Important Note

- **`google/lyria-3-pro-preview`** và **`google/lyria-3-clip-preview`**: Input/output pricing is 0, but it's a **music creation** model (Lyria 3), charged per song/clip ($0.08/song, $0.04/clip), and not shared across all code.
- **`deepseek/deepseek-chat`**: Input cost = 0 but output = $1.0287 — **not entirely free**.
