---
id: inbox_3d6c265a
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-medium-tag-llm-transformers-explained-attention-self-at-66e1]]"
title: "Transformers Explained: Attention, Self-Attention and Why Long Contexts Behave Strangely"
url: https://anujaneja.medium.com/transformers-explained-attention-self-attention-and-why-long-contexts-behave-strangely-218dd7debd07?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-09T16:52:42+00:00
fetched_at: 2026-11-10T00:07:33.855748+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "注意力像是總和為 1 的有限預算，這可以解釋長上下文中的異常行為。 **Why** 文章要說明為何長上下文會出現失效現象。 **How** 透過 self-attention、causal mask 與 positional encoding 的機制來說明。 **What** 教學型文章，以「注意力是總和為 1 的預算」作為核心比喻；摘要未提供實驗數據或模型版本。"
key_points:
  - "注意力權重總和為 1，被比喻為有限預算"
  - "涵蓋 self-attention、causal mask、positional encoding 三個機制"
  - "主題為長上下文的異常行為成因"
tags: [attention-mechanism, long-context, positional-encoding, transformers]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Transformers Explained: Attention, Self-Attention and Why Long Contexts Behave Strangely

注意力像是總和為 1 的有限預算，這可以解釋長上下文中的異常行為。

**Why** 文章要說明為何長上下文會出現失效現象。

**How** 透過 self-attention、causal mask 與 positional encoding 的機制來說明。

**What** 教學型文章，以「注意力是總和為 1 的預算」作為核心比喻；摘要未提供實驗數據或模型版本。

### 重點
- 注意力權重總和為 1，被比喻為有限預算
- 涵蓋 self-attention、causal mask、positional encoding 三個機制
- 主題為長上下文的異常行為成因

**原文：** [medium-tag-llm](https://anujaneja.medium.com/transformers-explained-attention-self-attention-and-why-long-contexts-behave-strangely-218dd7debd07?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Attention is a budget that sums to 1: what self-attention, causal masks and positional encodings explain about long-context failures in... Continue reading on Medium »

</details>