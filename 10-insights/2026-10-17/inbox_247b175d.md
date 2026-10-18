---
id: inbox_247b175d
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-medium-tag-llm-why-ai-says-wait-how-thinking-models-act-1911]]"
title: "Why AI Says “Wait”: How Thinking Models Actually Work (Every Step Measured)"
url: https://arunp0.medium.com/why-ai-says-wait-how-thinking-models-actually-work-every-step-measured-b1baff6c592d?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-17T21:46:19+00:00
fetched_at: 2026-10-18T03:16:45.767076+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇 Medium 文章解釋「思考模式」的運作原理，並主張切換 Thinking Mode 並不會啟動第二個推理大腦。依摘要，它只是注入 4 個模板 token：<think>\n\n</think>\n\n。作者聲稱對每個步驟都做了量測，但摘要在此處截斷，沒有說明所用的模型、硬體或具體量測結果，這些無法確認。對使用推理模型的開發者來說，這個觀點意味著 thinking 開關在機制上可能只是 prompt 模板差異，而非獨立的模型。"
key_points:
  - "主張：Thinking Mode 不是第二個推理大腦"
  - "機制：僅注入 4 個模板 token（<think>\n\n</think>\n\n）"
  - "使用模型與量測數據摘要未提供"
tags: [thinking-mode, reasoning-models, chat-template, think-tokens, llm-internals]
topics: [engineering.inference, engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Why AI Says “Wait”: How Thinking Models Actually Work (Every Step Measured)

這篇 Medium 文章解釋「思考模式」的運作原理，並主張切換 Thinking Mode 並不會啟動第二個推理大腦。依摘要，它只是注入 4 個模板 token：<think>\n\n</think>\n\n。作者聲稱對每個步驟都做了量測，但摘要在此處截斷，沒有說明所用的模型、硬體或具體量測結果，這些無法確認。對使用推理模型的開發者來說，這個觀點意味著 thinking 開關在機制上可能只是 prompt 模板差異，而非獨立的模型。

### 重點
- 主張：Thinking Mode 不是第二個推理大腦
- 機制：僅注入 4 個模板 token（<think>\n\n</think>\n\n）
- 使用模型與量測數據摘要未提供

**原文：** [medium-tag-llm](https://arunp0.medium.com/why-ai-says-wait-how-thinking-models-actually-work-every-step-measured-b1baff6c592d?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Toggling &#x201c;Thinking Mode&#x201d; doesn&#x2019;t boot up a second reasoning brain &#x2014; it injects just 4 template tokens (&lt;think&gt;\n\n&lt;/think&gt;\n\n). We ran&#x2026; Continue reading on Medium »

</details>