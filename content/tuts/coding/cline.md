---
linkTitle: Cline
title: "Cline: Best Agentic Coding Agent for VS Code"
weight: 3
cascade:
  type: docs
tags:
  - AI
  - Coding
  - Agents
---

Cline is the most autonomous free agent I've used. Install the VS Code extension, configure a BYOK provider, give it a task, and watch it work. It reads files, writes code, runs terminal commands, handles errors, and iterates — often without prompting you between steps.

The tradeoff is cost visibility. Because it's aggressive about tool use, a single Cline session on Claude Sonnet can easily cost $5-10. Pair it with a cheaper model for routine work. Gemini 2.5 Flash and GPT-5 Mini both do surprisingly well at a fraction of the price.

Best for: Developers who want "press go and walk away" behavior without leaving VS Code.


## Key Features

- Plan/Act separation: Cline shows you the plan before executing. You approve, modify, or reject it before any file changes happen.
- Terminal access: Runs npm run test, git commit, build scripts, and arbitrary shell commands as part of task execution
- File creation and editing: Creates new files, modifies existing ones, and removes what's no longer needed
- Browser automation: Controls a headless browser to test web UIs as part of an agentic task
- Multi-model support: Claude Sonnet 4.6, GPT-4o, Gemini 2.5 Pro, or any local model via Ollama
- MCP integration: Marketplace-backed connectors to databases, APIs, design tools, and dev services
- Real-time cost monitoring: Tracks token usage so agentic runs don't generate unexpected bills

**Pros**

- Plan/Act oversight is the right abstraction: AI does the work, you stay in control at each decision point
- MCP ecosystem makes it possible to build agents that understand your actual stack, not just your current file
- The community is large enough that most integration questions are already answered on Discord or GitHub
- Works with local models via Ollama for fully private, offline use

**Cons**

- Best fit is still editor-first workflows. Terminal purists may prefer Aider or OpenCode.
- Agentic runs consume API tokens faster than completion-only tools. Budget accordingly.
- Vague task descriptions produce worse results. Precision in prompts matters more here than with completion tools.
- Not optimized for lightweight inline completions. Pair it with Continue for that.

**License and Hosting**

- License: Apache-2.0. No commercial restrictions.
- Self-hosting: Local models via Ollama run entirely on your machine. Cloud APIs (Anthropic, OpenAI) send code to the provider's servers.
- Install: VS Code Extension Marketplace. Search "Cline".

**Best For**

Developers doing feature-level work in VS Code who want AI that handles the full task, not just the next line. If you currently write a feature from a ticket description, Cline changes that into: describe task, review plan, approve, iterate on review.

Skip Cline if you're outside VS Code, prefer pure autocomplete, or want to delegate tasks entirely without approval at each step.


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
