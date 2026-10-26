---
id: inbox_769d403c
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-medium-towards-data-science-your-six-ai-models-are-really-two-the-ma-d320]]"
title: "Your Six AI Models Are Really Two: The Math of Correlated Mistakes"
url: https://towardsdatascience.com/your-six-ai-models-are-really-two-the-math-of-correlated-mistakes/
source: medium-towards-data-science
published_at: 2026-10-23T11:00:00+00:00
fetched_at: 2026-10-24T03:53:40.117954+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "六個模型的多數決，獨立意見可能只有兩個，因為它們的錯誤高度相關。 **Why** 多模型投票假設各模型意見獨立，但原文指出相關錯誤會讓獨立意見遠少於模型數量。 **How** 作者提出一個公式估算獨立意見數，並在六個開源模型、1,500 題考題上驗證。 **What** 標題結論為六個模型實際相當於兩個獨立意見；原文說明用多模型投票時，獨立意見數少於所用模型數。"
key_points:
  - "多模型投票的獨立意見數可能遠低於模型數量"
  - "作者提出一個公式估算獨立意見數"
  - "在 6 個開源模型、1,500 題考題上驗證（原文）"
tags: [ensemble, correlated-errors, model-voting, evaluation]
topics: [engineering.evals]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Your Six AI Models Are Really Two: The Math of Correlated Mistakes

六個模型的多數決，獨立意見可能只有兩個，因為它們的錯誤高度相關。

**Why** 多模型投票假設各模型意見獨立，但原文指出相關錯誤會讓獨立意見遠少於模型數量。

**How** 作者提出一個公式估算獨立意見數，並在六個開源模型、1,500 題考題上驗證。

**What** 標題結論為六個模型實際相當於兩個獨立意見；原文說明用多模型投票時，獨立意見數少於所用模型數。

### 重點
- 多模型投票的獨立意見數可能遠低於模型數量
- 作者提出一個公式估算獨立意見數
- 在 6 個開源模型、1,500 題考題上驗證（原文）

**原文：** [medium-towards-data-science](https://towardsdatascience.com/your-six-ai-models-are-really-two-the-math-of-correlated-mistakes/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ask several models the same question, take a vote, and you get fewer independent opinions than you paid for. One formula says how many, and I checked it on six open models and 1,500 exam questions. 
 The post Your Six AI Models Are Really Two: The Math of Correlated Mistakes appeared first on Towards Data Science .

</details>