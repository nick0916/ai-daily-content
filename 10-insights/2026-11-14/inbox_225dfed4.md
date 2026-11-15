---
id: inbox_225dfed4
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-medium-tag-llm-serving-a-local-llm-from-my-mac-studio-w-6f73]]"
title: "Serving a Local LLM from My Mac Studio with Cloudflare Tunnel"
url: https://medium.com/@rohithkankipati4743/serving-a-local-llm-from-my-mac-studio-with-cloudflare-tunnel-24f101d8a0f8?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-14T22:52:07+00:00
fetched_at: 2026-11-15T01:30:41.292692+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Mac Studio 上的本地 LLM 透過 Cloudflare Tunnel 以認證 HTTPS API 對外提供。 **How** 以 OrbStack 承載原生 Ollama，搭配 LiteLLM，再經 Cloudflare 對外暴露。 **What** 為逐步教學文章，涵蓋 Ollama、OrbStack、LiteLLM、Cloudflare 四者的串接設定。"
key_points:
  - "以 OrbStack 承載原生 Ollama 服務"
  - "流程組合：OrbStack、LiteLLM、Cloudflare，對外提供認證 HTTPS API"
  - "全文為逐步教學（step-by-step guide）"
tags: [ollama, cloudflare-tunnel, local-llm, litellm, orbstack]
topics: [engineering.inference, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Serving a Local LLM from My Mac Studio with Cloudflare Tunnel

把 Mac Studio 上的本地 LLM 透過 Cloudflare Tunnel 以認證 HTTPS API 對外提供。

**How** 以 OrbStack 承載原生 Ollama，搭配 LiteLLM，再經 Cloudflare 對外暴露。

**What** 為逐步教學文章，涵蓋 Ollama、OrbStack、LiteLLM、Cloudflare 四者的串接設定。

### 重點
- 以 OrbStack 承載原生 Ollama 服務
- 流程組合：OrbStack、LiteLLM、Cloudflare，對外提供認證 HTTPS API
- 全文為逐步教學（step-by-step guide）

**原文：** [medium-tag-llm](https://medium.com/@rohithkankipati4743/serving-a-local-llm-from-my-mac-studio-with-cloudflare-tunnel-24f101d8a0f8?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A step-by-step guide to exposing native Ollama through an authenticated HTTPS API using OrbStack, LiteLLM, and Cloudflare. Continue reading on Medium »

</details>