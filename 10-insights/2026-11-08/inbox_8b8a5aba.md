---
id: inbox_8b8a5aba
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2348-lobsters-ai-what-can-i-realistically-do-with-local-a-7c20]]"
title: "What can I realistically do with local AI on a Mac mini M5 Pro (48GB)?"
url: https://lobste.rs/s/umsitb/what_can_i_realistically_do_with_local_ai
source: lobsters-ai
published_at: 2026-11-08T11:07:51-06:00
fetched_at: 2026-11-08T23:55:35.184133+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "有人詢問在 48GB 統一記憶體的 M5 Pro Mac mini 上，本地跑 AI 的實際可行性。 **Why** 提問者想在本機做自動補全、agentic 工作流、影像生成與 RAG，但難以分辨日常可用與 benchmark 炒作。 **What** 提問者想知道 48GB 內哪些模型與量化版本真的好用、該選 MLX、llama.cpp、Ollama、LM Studio 還是 ComfyUI，以及有哪些項目放棄後改回雲端 API；並希望分享實際 tokens/sec 與失敗經驗。原文為提問，尚無回答。"
key_points:
  - "硬體為 Mac mini M5 Pro（基本 CPU 配置）與 48GB 統一記憶體"
  - "提問涵蓋模型與量化選擇、MLX / llama.cpp / Ollama / LM Studio / ComfyUI 等工具選擇"
  - "希望取得實際 tokens/sec 數據與「白忙一場」的經驗，原文尚無回覆"
tags: [local-llm, apple-silicon, mac-mini, inference, rag]
topics: [engineering.inference]
importance: 2
novelty: 2
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## What can I realistically do with local AI on a Mac mini M5 Pro (48GB)?

有人詢問在 48GB 統一記憶體的 M5 Pro Mac mini 上，本地跑 AI 的實際可行性。

**Why** 提問者想在本機做自動補全、agentic 工作流、影像生成與 RAG，但難以分辨日常可用與 benchmark 炒作。

**What** 提問者想知道 48GB 內哪些模型與量化版本真的好用、該選 MLX、llama.cpp、Ollama、LM Studio 還是 ComfyUI，以及有哪些項目放棄後改回雲端 API；並希望分享實際 tokens/sec 與失敗經驗。原文為提問，尚無回答。

### 重點
- 硬體為 Mac mini M5 Pro（基本 CPU 配置）與 48GB 統一記憶體
- 提問涵蓋模型與量化選擇、MLX / llama.cpp / Ollama / LM Studio / ComfyUI 等工具選擇
- 希望取得實際 tokens/sec 數據與「白忙一場」的經驗，原文尚無回覆

**原文：** [lobsters-ai](https://lobste.rs/s/umsitb/what_can_i_realistically_do_with_local_ai)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I just got a Mac mini with an M5 Pro (base CPU config) and 48GB of unified memory. I want to run as much AI locally as makes sense, but it's hard to separate what actually works day to day from benchmark hype. 
 What I'd like to do: 
 
 Coding: autocomplete and agentic workflows with local models 
 Image generation 
 Anything else genuinely useful: transcription, RAG over my notes, etc. 
 
 Questions: 
 
 Which models and quantizations fit comfortably in 48GB and are actually usable, not just "it runs"? 
 Which runtime and tools: MLX, llama.cpp, Ollama, LM Studio, ComfyUI, something else? 
 What's your setup, and what did you give up on and go back to cloud APIs for? 
 
 Real tokens/sec numbers and "this was a waste of time" stories are especially welcome.

</details>