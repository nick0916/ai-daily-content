---
id: inbox_b3d73275
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-simon-willison-datasette-llm-0-1a11-dfa3]]"
title: "datasette-llm 0.1a11"
url: https://simonwillison.net/2026/Nov/14/datasette-llm/
source: simon-willison
published_at: 2026-11-14T23:59:28+00:00
fetched_at: 2026-11-15T01:29:18.567253+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Datasette 的 LLM 外掛能連上任何說 OpenAI 協定的模型伺服器，包含本機模型。 **How** 在 datasette-llm 的 default_model 設定中填入 model、model_name 與 api_base，指向 LM Studio、Ollama 或 llama.cpp 等本機端點即可。 **What** datasette-llm 0.1a11 新增 OpenAI-compatible endpoint 支援。文中範例用 uvx 搭配 datasette-agent，接上 LM Studio 的 qwen/qwen3.8-27b（api_base 為 http://localhost:1234/v1），就能在本機跑出由本地模型驅動的 Datasette Agent；文中也提到 llama.cpp 剛發布 v1.0.0。"
key_points:
  - "datasette-llm 0.1a11 新增 OpenAI-compatible endpoint 支援，可接任何相容 OpenAI 協定的 LLM 服務"
  - "設定方式：default_model 內指定 model、model_name、api_base（範例為 LM Studio 的 http://localhost:1234/v1）"
  - "範例以 uvx --with datasette-agent 啟動，搭配本機 qwen/qwen3.8-27b 跑 Datasette Agent"
tags: [datasette, datasette-llm, local-llm, openai-compatible, lm-studio]
topics: [engineering.inference, agents.frameworks]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-llm 0.1a11

讓 Datasette 的 LLM 外掛能連上任何說 OpenAI 協定的模型伺服器，包含本機模型。

**How** 在 datasette-llm 的 default_model 設定中填入 model、model_name 與 api_base，指向 LM Studio、Ollama 或 llama.cpp 等本機端點即可。

**What** datasette-llm 0.1a11 新增 OpenAI-compatible endpoint 支援。文中範例用 uvx 搭配 datasette-agent，接上 LM Studio 的 qwen/qwen3.8-27b（api_base 為 http://localhost:1234/v1），就能在本機跑出由本地模型驅動的 Datasette Agent；文中也提到 llama.cpp 剛發布 v1.0.0。

### 重點
- datasette-llm 0.1a11 新增 OpenAI-compatible endpoint 支援，可接任何相容 OpenAI 協定的 LLM 服務
- 設定方式：default_model 內指定 model、model_name、api_base（範例為 LM Studio 的 http://localhost:1234/v1）
- 範例以 uvx --with datasette-agent 啟動，搭配本機 qwen/qwen3.8-27b 跑 Datasette Agent

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/14/datasette-llm/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-llm 0.1a11 
 datasette-llm is the intermediate plugin for Datasette that supports configuring LLMs for use with other Datasette plugins. 
 This release adds support for OpenAI-compatible endpoints, so you can configure Datasette to use an LLM hosted anywhere that talks the OpenAI pseudo-standard web protocol. 
 This means that if you're running local models with LM Studio or Ollama or llama.cpp (which just hit v1.0.0 ) you can run Datasette via uvx like this: 
 wget https://datasette.io/content.db

uvx --with datasette-agent datasette \
 --root --secret 1 \
 -s plugins.datasette-llm.default_model ' { 
 "model": "lmstudio-qwen", 
 "model_name": "qwen/qwen3.8-27b", 
 "api_base": "http://localhost:1234/v1" 
 } ' content.db 

 And you'll get a local server running a Datasette Agent instance powered by your local model! 
 
 
 
 Tags: uv , datasette-agent , llm , datasette , llms , ai , generative-ai

</details>