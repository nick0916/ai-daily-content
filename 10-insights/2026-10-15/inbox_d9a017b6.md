---
id: inbox_d9a017b6
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-medium-towards-data-science-how-many-guesses-does-it-take-to-crack-a-220f]]"
title: "How Many Guesses Does It Take to Crack an AI&#39;s \&#34;Random\&#34; Number?"
url: https://towardsdatascience.com/how-many-guesses-does-it-take-to-crack-an-ais-random-number/
source: medium-towards-data-science
published_at: 2026-10-15T12:30:00+00:00
fetched_at: 2026-10-18T03:15:53.726588+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者從開放模型的 logits 直接讀出模型回答的完整機率分布，用來檢驗 AI 所謂的「隨機」數字有多隨機。分析對象包含 base 模型與 instruction-tuned 模型。作者把分布換算成 bits（熵）以及破解所需的猜測次數（guesses-to-crack）。這個做法不靠重複取樣，而是直接用精確分布量化可預測性。原文摘要沒有給出具體數字或模型名稱。實務意義是：若把 LLM 當作隨機數來源（例如用於密碼或抽樣），其輸出可能高度可預測。"
key_points:
  - "直接從開放模型的 logits 讀取精確答案分布，而非靠重複取樣估計"
  - "將分布換算為 bits 與 guesses-to-crack，並比較 base 與 instruction-tuned 模型"
tags: [logits, randomness, entropy, base-vs-instruct, open-models]
topics: [foundation_models.open_weights, research.training]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How Many Guesses Does It Take to Crack an AI's \"Random\" Number?

作者從開放模型的 logits 直接讀出模型回答的完整機率分布，用來檢驗 AI 所謂的「隨機」數字有多隨機。分析對象包含 base 模型與 instruction-tuned 模型。作者把分布換算成 bits（熵）以及破解所需的猜測次數（guesses-to-crack）。這個做法不靠重複取樣，而是直接用精確分布量化可預測性。原文摘要沒有給出具體數字或模型名稱。實務意義是：若把 LLM 當作隨機數來源（例如用於密碼或抽樣），其輸出可能高度可預測。

### 重點
- 直接從開放模型的 logits 讀取精確答案分布，而非靠重複取樣估計
- 將分布換算為 bits 與 guesses-to-crack，並比較 base 與 instruction-tuned 模型

**原文：** [medium-towards-data-science](https://towardsdatascience.com/how-many-guesses-does-it-take-to-crack-an-ais-random-number/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I read the exact answer distribution from the logits of open models, base and instruction-tuned, and turned it into bits and guesses-to-crack. 
 The post How Many Guesses Does It Take to Crack an AI's &quot;Random&quot; Number? appeared first on Towards Data Science .

</details>