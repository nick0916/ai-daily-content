---
id: inbox_46c48c8b
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0812-medium-tag-llm-your-agentic-rag-system-is-not-one-model-8309]]"
title: "️ Your Agentic RAG System Is Not One Model. It’s Six. Here Is How Much GPU They Really Eat"
url: https://medium.com/@zakaria.hamane1/%EF%B8%8F-your-agentic-rag-system-is-not-one-model-its-six-here-is-how-much-gpu-they-really-eat-c657f8909d93?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-19T00:11:44+00:00
fetched_at: 2026-11-19T08:20:09.438627+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "代理式 RAG 系統用到的不只一個模型，GPU 預算要把嵌入、重排與語音等模型一起算。 **Why** 只估算 LLM 的 GPU 需求，會低估整體系統的資源消耗。 **How** 文章逐一列出 embedder、reranker、Whisper、OCR、TTS 等附加模型。 **What** 標題指出代理式 RAG 系統實際包含六個模型，節錄提到的附加元件包括 embedder、reranker、Whisper、OCR 與 TTS。"
key_points:
  - "代理式 RAG 系統包含六個模型，不只是單一 LLM"
  - "附加模型包括 embedder、reranker、Whisper、OCR、TTS"
  - "GPU 採購應依整體 pipeline 估算，而非只看 LLM"
tags: [agentic-rag, gpu-cost, embedding, reranker, inference-cost]
topics: [engineering.rag, engineering.inference]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## ️ Your Agentic RAG System Is Not One Model. It’s Six. Here Is How Much GPU They Really Eat

代理式 RAG 系統用到的不只一個模型，GPU 預算要把嵌入、重排與語音等模型一起算。

**Why** 只估算 LLM 的 GPU 需求，會低估整體系統的資源消耗。

**How** 文章逐一列出 embedder、reranker、Whisper、OCR、TTS 等附加模型。

**What** 標題指出代理式 RAG 系統實際包含六個模型，節錄提到的附加元件包括 embedder、reranker、Whisper、OCR 與 TTS。

### 重點
- 代理式 RAG 系統包含六個模型，不只是單一 LLM
- 附加模型包括 embedder、reranker、Whisper、OCR、TTS
- GPU 採購應依整體 pipeline 估算，而非只看 LLM

**原文：** [medium-tag-llm](https://medium.com/@zakaria.hamane1/%EF%B8%8F-your-agentic-rag-system-is-not-one-model-its-six-here-is-how-much-gpu-they-really-eat-c657f8909d93?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Everyone does the napkin math for the LLM and buys the GPUs. Then the embedder, the reranker, Whisper, the OCR and the TTS show up on the... Continue reading on Medium »

</details>