---
id: inbox_e063b998
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-medium-tag-llm-is-it-really-true-an-llm-confidence-scor-2207]]"
title: "Is It Really True an LLM Confidence Score Means Nothing? I Checked 400 Answers"
url: https://medium.com/@vinay221097/is-it-really-true-an-llm-confidence-score-means-nothing-i-checked-400-answers-86ee25fb9070?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-22T23:32:06+00:00
fetched_at: 2026-10-23T00:58:03.674384+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "模型自報的信心分數不可直接採信，需要獨立的檢查來驗證答案。 **How** 作者檢驗 400 個答案，並用兩種低成本檢查來補足信心分數的不足。 **What** 測試中某小型 AI 對每個答案都回報 100% 確定，包括 100 個錯誤答案；文中稱兩種便宜的檢查抓出了這個數字漏掉的問題，但摘要未列出檢查的具體做法。"
key_points:
  - "測試規模：400 個 LLM 答案"
  - "現象：小模型對所有答案（含 100 個錯誤答案）都報告 100% 確定"
  - "作者以兩種低成本檢查補足信心分數的盲點（摘要未列細節）"
tags: [confidence-calibration, hallucination, llm-evaluation]
topics: [engineering.evals]
importance: 2
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Is It Really True an LLM Confidence Score Means Nothing? I Checked 400 Answers

模型自報的信心分數不可直接採信，需要獨立的檢查來驗證答案。 **How** 作者檢驗 400 個答案，並用兩種低成本檢查來補足信心分數的不足。 **What** 測試中某小型 AI 對每個答案都回報 100% 確定，包括 100 個錯誤答案；文中稱兩種便宜的檢查抓出了這個數字漏掉的問題，但摘要未列出檢查的具體做法。

### 重點
- 測試規模：400 個 LLM 答案
- 現象：小模型對所有答案（含 100 個錯誤答案）都報告 100% 確定
- 作者以兩種低成本檢查補足信心分數的盲點（摘要未列細節）

**原文：** [medium-tag-llm](https://medium.com/@vinay221097/is-it-really-true-an-llm-confidence-score-means-nothing-i-checked-400-answers-86ee25fb9070?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A small AI said &#x201c;100% sure&#x201d; on every answer, including 100 wrong ones. Two cheap checks caught what the number missed. Continue reading on Medium »

</details>