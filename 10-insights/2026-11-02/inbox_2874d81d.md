---
id: inbox_2874d81d
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-medium-tag-llm-my-model-thought-tamil-was-telugu-part-2-cdf3]]"
title: "My Model Thought Tamil Was Telugu, Part 2: How 51,000 YouTube Comments Fixed It"
url: https://pub.towardsai.net/my-model-thought-tamil-was-telugu-part-2-how-51-000-youtube-comments-fixed-it-85793804d632?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-02T14:31:01+00:00
fetched_at: 2026-11-02T23:33:32.553979+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "模型把泰米爾語誤認為泰盧固語，作者用留言資料把問題修正。 **How** 規則式標註器失敗後，改用開源權重 LLM 當標註器，並檢查測試資料。 **What** 作者使用 51,000 則 YouTube 留言修正模型，過程中發現測試資料有洩漏。"
key_points:
  - "模型把泰米爾語誤判為泰盧固語"
  - "規則式標註器失敗，開源權重 LLM 標註器通過"
  - "作者在測試資料中發現洩漏（leak）"
tags: [language-identification, data-labeling, data-leakage, open-weights]
topics: [engineering.evals, foundation_models.open_weights]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## My Model Thought Tamil Was Telugu, Part 2: How 51,000 YouTube Comments Fixed It

模型把泰米爾語誤認為泰盧固語，作者用留言資料把問題修正。

**How** 規則式標註器失敗後，改用開源權重 LLM 當標註器，並檢查測試資料。

**What** 作者使用 51,000 則 YouTube 留言修正模型，過程中發現測試資料有洩漏。

### 重點
- 模型把泰米爾語誤判為泰盧固語
- 規則式標註器失敗，開源權重 LLM 標註器通過
- 作者在測試資料中發現洩漏（leak）

**原文：** [medium-tag-llm](https://pub.towardsai.net/my-model-thought-tamil-was-telugu-part-2-how-51-000-youtube-comments-fixed-it-85793804d632?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A rule labeller that failed, an open-weights LLM labeller that passed, and a leak I found in my test data Continue reading on Towards AI »

</details>