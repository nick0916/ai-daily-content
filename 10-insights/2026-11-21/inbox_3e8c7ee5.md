---
id: inbox_3e8c7ee5
date: 2026-11-21
source_ref: "[[00-inbox/2026-11-21/0238-medium-tag-claude-rag-vs-long-context-the-cheap-context-wi-c0ac]]"
title: "RAG vs Long Context: The Cheap Context Window Sees 0.17% of Your Corpus"
url: https://medium.com/@brian-curry-research/rag-vs-long-context-the-cheap-context-window-sees-0-17-of-your-corpus-79b20689c0a1?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-11-21T22:43:08+00:00
fetched_at: 2026-11-22T02:45:33.936768+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把大型語料全塞進上下文成本高，便宜的 1M 視窗只能覆蓋約 0.17%。 **Why** 大型語料要回答問題時，需比較全量讀取、快取上下文與搜尋迴圈的成本。 **How** 原文以 6 億 token 語料為例，比較三種做法的每題成本。 **What** 全量讀取每題 $1,204.80；快取 1M-token 視窗 $0.108；agent 搜尋迴圈 $0.162；1M 視窗約覆蓋 0.17%（1M ÷ 600M）。"
key_points:
  - "600M token 語料全量讀取每題 $1,204.80"
  - "快取 1M-token 視窗每題 $0.108，agent 搜尋迴圈 $0.162"
  - "1M 視窗約覆蓋語料的 0.17%（1M ÷ 600M ≈ 0.17%）"
tags: [rag, long-context, prompt-caching, cost-analysis]
topics: [engineering.rag, engineering.inference]
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## RAG vs Long Context: The Cheap Context Window Sees 0.17% of Your Corpus

把大型語料全塞進上下文成本高，便宜的 1M 視窗只能覆蓋約 0.17%。

**Why** 大型語料要回答問題時，需比較全量讀取、快取上下文與搜尋迴圈的成本。

**How** 原文以 6 億 token 語料為例，比較三種做法的每題成本。

**What** 全量讀取每題 $1,204.80；快取 1M-token 視窗 $0.108；agent 搜尋迴圈 $0.162；1M 視窗約覆蓋 0.17%（1M ÷ 600M）。

### 重點
- 600M token 語料全量讀取每題 $1,204.80
- 快取 1M-token 視窗每題 $0.108，agent 搜尋迴圈 $0.162
- 1M 視窗約覆蓋語料的 0.17%（1M ÷ 600M ≈ 0.17%）

**原文：** [medium-tag-claude](https://medium.com/@brian-curry-research/rag-vs-long-context-the-cheap-context-window-sees-0-17-of-your-corpus-79b20689c0a1?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Reading a 600M-token corpus costs $1,204.80 per question. A cached 1M-token window costs $0.108 and an agent search loop $0.162. What the... Continue reading on Medium »

</details>