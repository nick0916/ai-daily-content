---
id: inbox_e4c468c5
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-medium-towards-data-science-i-built-a-trap-for-ai-image-judges-they-405b]]"
title: "I Built a Trap for AI Image Judges. They Walked Into a Different One."
url: https://towardsdatascience.com/i-built-a-trap-for-ai-image-judges-they-walked-into-a-different-one/
source: medium-towards-data-science
published_at: 2026-10-12T11:00:00+00:00
fetched_at: 2026-10-18T03:16:45.765984+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者設計了一個針對「AI 圖像評審」的陷阱實驗，測試三個視覺 AI 模型。依摘要，三個模型都忽略了那張吸引人的圖片，但結果仍出現其他問題：GPT-4o 會捏造答案，而 Claude 則一直回答 B。摘要沒有說明三個模型分別是誰（除 GPT-4o 與 Claude 外）、Claude 的具體版本、實驗題數或比例，這些無法確認。對使用 VLM 當 judge 的人來說，這顯示評審模型可能有位置偏誤或編造答案的失敗模式，使用時需要另外驗證。"
key_points:
  - "實驗：三個視覺模型當圖像評審，皆忽略了誘餌圖片"
  - "GPT-4o 的失敗模式：捏造答案"
  - "Claude 的失敗模式：持續回答 B（疑似選項偏誤，為推論）"
tags: [vlm-as-judge, evaluation, hallucination, position-bias, gpt-4o]
topics: [engineering.evals, foundation_models.gpt, foundation_models.claude]
importance: 2
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I Built a Trap for AI Image Judges. They Walked Into a Different One.

作者設計了一個針對「AI 圖像評審」的陷阱實驗，測試三個視覺 AI 模型。依摘要，三個模型都忽略了那張吸引人的圖片，但結果仍出現其他問題：GPT-4o 會捏造答案，而 Claude 則一直回答 B。摘要沒有說明三個模型分別是誰（除 GPT-4o 與 Claude 外）、Claude 的具體版本、實驗題數或比例，這些無法確認。對使用 VLM 當 judge 的人來說，這顯示評審模型可能有位置偏誤或編造答案的失敗模式，使用時需要另外驗證。

### 重點
- 實驗：三個視覺模型當圖像評審，皆忽略了誘餌圖片
- GPT-4o 的失敗模式：捏造答案
- Claude 的失敗模式：持續回答 B（疑似選項偏誤，為推論）

**原文：** [medium-towards-data-science](https://towardsdatascience.com/i-built-a-trap-for-ai-image-judges-they-walked-into-a-different-one/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Three vision AI models ignored the pretty image, yet GPT-4o invented answers and Claude kept answering B. 
 The post I Built a Trap for AI Image Judges. They Walked Into a Different One. appeared first on Towards Data Science .

</details>