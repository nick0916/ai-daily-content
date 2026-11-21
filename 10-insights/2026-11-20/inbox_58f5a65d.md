---
id: inbox_58f5a65d
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0048-medium-tag-llm-kv-cache-size-how-many-users-fit-on-one-fd0a]]"
title: "KV Cache Size: How Many Users Fit on One GPU?"
url: https://pub.towardsai.net/kv-cache-size-how-many-users-fit-on-one-gpu-76bcd3c02ee9?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-20T19:01:26+00:00
fetched_at: 2026-11-21T00:54:18.733469+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "單張 GPU 能同時服務多少使用者，取決於 KV cache 的大小。 **Why** 原文指出參數量大不代表 KV cache 就大：DeepSeek V3 有 671B 參數，但 KV cache 比 Llama 3 8B 小。 **How** 文章提供計算公式、比較表與可執行的腳本來估算。 **What** 文章以 DeepSeek V3 與 Llama 3 8B 為例比較 KV cache；節錄中未列出具體數值與同時使用者數。"
key_points:
  - "DeepSeek V3（671B 參數）的 KV cache 小於 Llama 3 8B（原文所述）"
  - "文章提供 KV cache 公式、比較表與可執行腳本"
  - "節錄未列出具體 KV cache 數值或可服務使用者數"
tags: [kv-cache, gpu-memory, inference-capacity, deepseek-v3, llama-3]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## KV Cache Size: How Many Users Fit on One GPU?

單張 GPU 能同時服務多少使用者，取決於 KV cache 的大小。

**Why** 原文指出參數量大不代表 KV cache 就大：DeepSeek V3 有 671B 參數，但 KV cache 比 Llama 3 8B 小。

**How** 文章提供計算公式、比較表與可執行的腳本來估算。

**What** 文章以 DeepSeek V3 與 Llama 3 8B 為例比較 KV cache；節錄中未列出具體數值與同時使用者數。

### 重點
- DeepSeek V3（671B 參數）的 KV cache 小於 Llama 3 8B（原文所述）
- 文章提供 KV cache 公式、比較表與可執行腳本
- 節錄未列出具體 KV cache 數值或可服務使用者數

**原文：** [medium-tag-llm](https://pub.towardsai.net/kv-cache-size-how-many-users-fit-on-one-gpu-76bcd3c02ee9?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

DeepSeek V3 has 671B parameters and a smaller KV cache than Llama 3 8B. Here is the formula, a comparison table, and a script you can run... Continue reading on Towards AI »

</details>