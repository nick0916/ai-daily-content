---
id: inbox_48f548e4
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-medium-tag-llm-strawberry-has-2-rs-how-chatgpt-actually-34e9]]"
title: "Strawberry Has 2 R’s? How ChatGPT Actually Works Under the Hood (Every Number Measured)"
url: https://arunp0.medium.com/strawberry-has-2-rs-how-chatgpt-actually-works-under-the-hood-every-number-measured-0c6499992573?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-17T21:40:12+00:00
fetched_at: 2026-10-18T03:16:45.768333+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇 Medium 文章以「strawberry 有幾個 r」這類問題為切入點，說明 ChatGPT 類模型在底層如何運作。依摘要，作者在自己的 GPU 上開啟一個 40 億參數的語言模型 Qwen3-4B，追蹤一個問題從按下 Enter 開始的完整流程。標題宣稱每個數字都是實測，但摘要在此處截斷，具體的步驟、延遲或數值無法確認。對想理解 tokenization 到推論流程的讀者來說，這是用小型開源權重模型做的實作式說明。"
key_points:
  - "使用模型：Qwen3-4B（40 億參數），在作者自己的 GPU 上執行"
  - "做法：追蹤單一問題從輸入到輸出的完整流程"
  - "具體量測數值摘要未提供"
tags: [qwen3-4b, llm-internals, inference-pipeline, tokenization, local-gpu]
topics: [foundation_models.open_weights, engineering.inference]
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Strawberry Has 2 R’s? How ChatGPT Actually Works Under the Hood (Every Number Measured)

這篇 Medium 文章以「strawberry 有幾個 r」這類問題為切入點，說明 ChatGPT 類模型在底層如何運作。依摘要，作者在自己的 GPU 上開啟一個 40 億參數的語言模型 Qwen3-4B，追蹤一個問題從按下 Enter 開始的完整流程。標題宣稱每個數字都是實測，但摘要在此處截斷，具體的步驟、延遲或數值無法確認。對想理解 tokenization 到推論流程的讀者來說，這是用小型開源權重模型做的實作式說明。

### 重點
- 使用模型：Qwen3-4B（40 億參數），在作者自己的 GPU 上執行
- 做法：追蹤單一問題從輸入到輸出的完整流程
- 具體量測數值摘要未提供

**原文：** [medium-tag-llm](https://arunp0.medium.com/strawberry-has-2-rs-how-chatgpt-actually-works-under-the-hood-every-number-measured-0c6499992573?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

We opened up a 4-billion-parameter language model (Qwen3&#x2013;4B) on our own GPU and followed a single question from the moment you hit Enter &#x2014;&#x2026; Continue reading on Medium »

</details>