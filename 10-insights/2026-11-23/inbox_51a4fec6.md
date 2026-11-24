---
id: inbox_51a4fec6
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-medium-tag-llm-i-built-a-constitutional-ai-pipeline-the-a7fa]]"
title: "I built a Constitutional AI pipeline. Then I tested whether I could trust its judge."
url: https://medium.com/@bainamndidaliwa/i-built-a-constitutional-ai-pipeline-then-i-tested-whether-i-could-trust-its-judge-68a956d69b82?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-23T19:47:28+00:00
fetched_at: 2026-11-24T02:17:05.257022+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者建立 Constitutional AI 流程後檢驗其評審（judge）是否可信，54 個提示中只有 4 個標籤被接受，促使他重新審視原計畫用於訓練的環節。 **Why** 作者原本打算把此評審的判斷用於訓練，因此要先確認可信度。 **How** 以 Constitutional AI 流程中的 judge 為 54 個提示產生標籤並檢驗。 **What** 54 個提示中僅 4 個標籤被接受。"
key_points:
  - "54 個提示中僅 4 個標籤被接受"
  - "作者原計畫以此評審結果用於訓練"
  - "促使作者在使用前重新檢驗評審可靠性"
tags: [constitutional-ai, llm-as-judge, evals, reliability]
topics: [engineering.evals, research.training]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I built a Constitutional AI pipeline. Then I tested whether I could trust its judge.

作者建立 Constitutional AI 流程後檢驗其評審（judge）是否可信，54 個提示中只有 4 個標籤被接受，促使他重新審視原計畫用於訓練的環節。

**Why** 作者原本打算把此評審的判斷用於訓練，因此要先確認可信度。

**How** 以 Constitutional AI 流程中的 judge 為 54 個提示產生標籤並檢驗。

**What** 54 個提示中僅 4 個標籤被接受。

### 重點
- 54 個提示中僅 4 個標籤被接受
- 作者原計畫以此評審結果用於訓練
- 促使作者在使用前重新檢驗評審可靠性

**原文：** [medium-tag-llm](https://medium.com/@bainamndidaliwa/i-built-a-constitutional-ai-pipeline-then-i-tested-whether-i-could-trust-its-judge-68a956d69b82?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Four accepted labels from 54 prompts sent me back to the part of the system I had planned to trust with training. Continue reading on Medium »

</details>