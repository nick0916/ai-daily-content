---
id: inbox_ab139b4a
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2252-medium-tag-llm-prompt-caching-same-agent-same-rules-abo-a19e]]"
title: "Prompt caching: same agent, same rules, about a quarter of the bill"
url: https://medium.com/@baigorria/prompt-caching-same-agent-same-rules-about-a-quarter-of-the-bill-22494c6803fa?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-30T20:33:26+00:00
fetched_at: 2026-10-30T22:58:05.477610+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "同一個 agent 與規則下，靠 prompt caching 可把帳單降到約四分之一。 **What** 原文為 Medium 付費牆前導，作者表示測試 agent 的 prompt 原本完全沒有命中快取，經過四個步驟後快取讀取比例最高達 94%；前導中未列出這四個步驟的具體內容。"
key_points:
  - "作者的測試 agent 原本 prompt 看似正常，但完全沒有讀取快取"
  - "依作者所述，經過四個調整步驟後，快取讀取比例最高達 94%"
  - "標題估計帳單約降至四分之一，但四個步驟的具體內容在前導中未見"
tags: [prompt-caching, cost-optimization, agents, llm-billing]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Prompt caching: same agent, same rules, about a quarter of the bill

同一個 agent 與規則下，靠 prompt caching 可把帳單降到約四分之一。

**What** 原文為 Medium 付費牆前導，作者表示測試 agent 的 prompt 原本完全沒有命中快取，經過四個步驟後快取讀取比例最高達 94%；前導中未列出這四個步驟的具體內容。

### 重點
- 作者的測試 agent 原本 prompt 看似正常，但完全沒有讀取快取
- 依作者所述，經過四個調整步驟後，快取讀取比例最高達 94%
- 標題估計帳單約降至四分之一，但四個步驟的具體內容在前導中未見

**原文：** [medium-tag-llm](https://medium.com/@baigorria/prompt-caching-same-agent-same-rules-about-a-quarter-of-the-bill-22494c6803fa?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Our test agent’s prompt looked fine and read nothing from the cache. Four moves later, it read up to 94%. Continue reading on Medium »

</details>