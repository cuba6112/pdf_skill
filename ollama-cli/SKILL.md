---
name: ollama-cli
description: Use the 'ask' CLI to query local and cloud LLMs via Ollama. Includes model list and recommendations.
usage: ask [prompt] [flags]
---

# Ollama CLI (`ask`)

A powerful command-line interface for interacting with your local and cloud-based LLMs through Ollama.

## 🚀 Quick Start

```bash
# Interactive Chat Mode (Default)
ask

# One-Shot Question
ask "Explain quantum entanglement"

# Using a Specific Model
ask -m nemotron-3-nano:30b-cloud "Summarize this text"

# Piping Input (RAG-lite)
cat README.md | ask "What does this project do?"

# JSON Output (for scripts)
ask --json "Extract name and email from: John Doe <john@example.com>"
```

## 🧠 Available Models & Use Cases

### ☁️ Cloud Models (Fastest ⚡)
These models run on the cloud cluster and are significantly faster than local execution. **Use these for speed.**

| Model | ID | Best For |
|-------|----|----------|
| **Gemini 3 Flash** | `gemini-3-flash-preview:cloud` | ⚡ **Fastest**. General purpose, reasoning, huge context. |
| **GPT-OSS 120B** | `gpt-oss:120b-cloud` | 🧠 **High Intelligence**. Complex reasoning, creative writing. |
| **Kimi K2.5** | `kimi-k2.5:cloud` | 🇨🇳 **Chinese/English**. Great for cross-lingual tasks. |
| **Nemotron 3** | `nemotron-3-nano:30b-cloud` | 🎮 **Roleplay/Chat**. Good conversationalist. |
| **GLM 4.7** | `glm-4.7:cloud` | 📚 **Academic/Logical**. Strong performance on benchmarks. |

### 🏠 Local Models (Privacy 🔒)
Run entirely on your Mac Studio. Slower but data never leaves the machine.

| Model | ID | Best For |
|-------|----|----------|
| **Qwen 2.5 Coder** | `qwen3-coder-next:latest` | 💻 **Coding Specialist**. The best local coding model (80B MoE). |
| **Llama 3.1 8B** | `llama3.1:8b` | 🏃 **Speed/Quality Balance**. Good for quick local tasks. |
| **Llama 3.2** | `llama3.2:latest` | 🪶 **Lightweight**. Very fast, lower resource usage. |
| **GLM 4.7 Flash** | `glm-4.7-flash:bf16` | ⚖️ **Balanced**. Local version of GLM-4. |
| **GPT-OSS 120B** | `gpt-oss:120b` | 🏋️ **Heavy Reasoning**. Use only if you need 120B locally. |

### 🛠️ Utility Models

| Model | ID | Purpose |
|-------|----|---------|
| **Nomic Embed** | `nomic-embed-text:latest` | 🔍 **Embeddings**. Used for RAG/Memory search. |
| **Flux 2 Klein** | `x/flux2-klein:latest` | 🎨 **Image Gen**. High quality image generation. |
| **Z-Image Turbo** | `x/z-image-turbo:latest` | 🖼️ **Fast Images**. Turbo speed image generation. |

## ⚙️ Advanced Usage

### System Prompts (Personas)
Set the behavior of the model using `-s`.

```bash
# Coding Expert
ask -s "You are a senior Python architect. Be concise." "Refactor this code"

# Security Auditor
ask -s "You are a red team security analyst." "Find vulnerabilities in this function"
```

### Scripting with JSON
Use `--json` to integrate with other tools like `jq`.

```bash
# Extract data and parse
echo "Server 1: 192.168.1.10 (Active)" | \
ask --json "Extract IP and status" | \
jq .ip
```

### Context Window
If dealing with massive files, increase the context window (default varies by model).

```bash
# 32k context for large logs
ask --ctx 32768 "Analyze these logs" < huge_log.txt
```
