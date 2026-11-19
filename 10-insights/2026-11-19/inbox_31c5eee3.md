---
id: inbox_31c5eee3
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0812-medium-tag-llm-llm-evaluation-105-who-actually-grades-y-c512]]"
title: "LLM Evaluation 105: Who Actually Grades Your LLM? Programmatic, Human, and LLM-as-a-Judge"
url: https://pub.towardsai.net/llm-evaluation-105-who-actually-grades-your-llm-programmatic-human-and-llm-as-a-judge-29adf7c1422b?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-19T00:01:02+00:00
fetched_at: 2026-11-19T08:20:09.439658+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "評估 LLM 輸出時，要決定由誰來評分：程式規則、人工，還是 LLM 當裁判。 **How** 文章比較程式化評估、人工評估與 LLM-as-a-Judge，並區分有參考答案與無參考答案的評估方式。 **What** 這是 LLM Evaluation 系列第 105 篇，以範例說明三種評分者與兩種評估方式；節錄未提供具體數據。"
key_points:
  - "評分者分三類：程式化評估（programmatic）、人工評估（human）、LLM-as-a-Judge"
  - "評估方式區分為 reference-based（有參考答案）與 reference-free（無參考答案）"
  - "文章以範例說明各種方法的使用情境"
tags: [llm-evaluation, llm-as-judge, evals, reference-free, grading]
topics: [engineering.evals]
importance: 3
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## LLM Evaluation 105: Who Actually Grades Your LLM? Programmatic, Human, and LLM-as-a-Judge

評估 LLM 輸出時，要決定由誰來評分：程式規則、人工，還是 LLM 當裁判。

**How** 文章比較程式化評估、人工評估與 LLM-as-a-Judge，並區分有參考答案與無參考答案的評估方式。

**What** 這是 LLM Evaluation 系列第 105 篇，以範例說明三種評分者與兩種評估方式；節錄未提供具體數據。

### 重點
- 評分者分三類：程式化評估（programmatic）、人工評估（human）、LLM-as-a-Judge
- 評估方式區分為 reference-based（有參考答案）與 reference-free（無參考答案）
- 文章以範例說明各種方法的使用情境

**原文：** [medium-tag-llm](https://pub.towardsai.net/llm-evaluation-105-who-actually-grades-your-llm-programmatic-human-and-llm-as-a-judge-29adf7c1422b?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Programmatic, human, and LLM-as-a-Judge evals explained with examples, plus reference-based vs. reference-free evaluation. Continue reading on Towards AI »

</details>