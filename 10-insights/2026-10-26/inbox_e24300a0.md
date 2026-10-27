---
id: inbox_e24300a0
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-simon-willison-gpt-6-1-terra-b0ea]]"
title: "GPT-6.1 Terra"
url: https://simonwillison.net/2026/Oct/26/gpt-61-terra/
source: simon-willison
published_at: 2026-10-26T23:53:07+00:00
fetched_at: 2026-10-27T01:31:24.031862+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 推出中階、快速的 GPT-6.1 Terra，主打看圖理解與操作電腦。 **Why** 電腦操作這類重複性自動化任務，用不太貴又夠快的模型比較划算。 **How** 根據 OpenAI 的 Ted Sanders 說明，Terra 在技術寫作上優於 Astra 與 Sol，視覺與電腦操作與其相近但快很多，其他多數任務略遜。 **What** GPT-6.1 Terra 定價每百萬 token 輸入 $1、輸出 $5，約為 GPT-5.6 Terra 與 GPT-6.1 Sol 的一半，約為 GPT-6 Luna 的 10 倍。Simon Willison 指出其定位類似 Anthropic 的 Sonnet；其 pelican 測試 max 推理等級花費 11.3161 美分、耗時 4 分 11 秒。"
key_points:
  - "定價 $1/百萬輸入、$5/百萬輸出，約為 GPT-5.6 Terra 與 GPT-6.1 Sol 的一半，約為 GPT-6 Luna 的 10 倍"
  - "Ted Sanders：視覺/電腦操作與 Astra、Sol 相近但快很多，技術溝通較佳，其他多數任務略遜"
  - "pelican 測試 max 推理等級花費 11.3161 美分、耗時 4 分 11 秒"
tags: [gpt-6-1-terra, openai, llm-pricing, computer-use, visual-reasoning]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## GPT-6.1 Terra

OpenAI 推出中階、快速的 GPT-6.1 Terra，主打看圖理解與操作電腦。

**Why** 電腦操作這類重複性自動化任務，用不太貴又夠快的模型比較划算。

**How** 根據 OpenAI 的 Ted Sanders 說明，Terra 在技術寫作上優於 Astra 與 Sol，視覺與電腦操作與其相近但快很多，其他多數任務略遜。

**What** GPT-6.1 Terra 定價每百萬 token 輸入 $1、輸出 $5，約為 GPT-5.6 Terra 與 GPT-6.1 Sol 的一半，約為 GPT-6 Luna 的 10 倍。Simon Willison 指出其定位類似 Anthropic 的 Sonnet；其 pelican 測試 max 推理等級花費 11.3161 美分、耗時 4 分 11 秒。

### 重點
- 定價 $1/百萬輸入、$5/百萬輸出，約為 GPT-5.6 Terra 與 GPT-6.1 Sol 的一半，約為 GPT-6 Luna 的 10 倍
- Ted Sanders：視覺/電腦操作與 Astra、Sol 相近但快很多，技術溝通較佳，其他多數任務略遜
- pelican 測試 max 推理等級花費 11.3161 美分、耗時 4 分 11 秒

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/26/gpt-61-terra/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GPT-6.1 Terra 
It's always interesting to note which aspects of a new model are emphasized in the release announcement. 
 In the case of GPT-6.1 Terra, OpenAI went with visual reasoning and computer use: 
 
 We’re introducing GPT-6.1 Terra , a fast, efficient model that combines detailed visual reasoning and precise computer use alongside clearer, more natural writing. A significant step up from GPT‐5.6 Terra, it excels at the communication and computer-based tasks that fill the workday, from drafting proposals and interpreting technical drawings to filling out forms and editing videos. 
 
 Terra sits in the same position as Sonnet in the Anthropic model collection - not the cheapest or the most expensive, making it harder to decide when to use it. 
 Computer use is a good example of a task that benefits from a less expensive model, since you might put it to work on automated, repetitive tasks. 
 OpenAI's Ted Sanders provided some useful advice in a comment on Hacker News: 
 
 In the case of GPT-6.1 Terra, I'd say Terra is probably better than Astra and Sol at technical communication, similar on vision and computer use (but much faster!), and a bit worse on most other things. For API developers, it's a nice midrange option if you want something cheaper than Sol but a lot smarter than Luna (especially for vision / computer use / communication). For subscribers, it's not a bombshell release - if you're hitting usage limits, maybe it helps you go a bit further, and if you want clearer communication or faster computer use, it can be a nice option to select. 
 
 Here are the pelicans for the different reasoning levels. This pelican for "max" cost 11.3161 cents and took 4 minutes and 11 seconds: 
 
 Here's a new comparison grid showing pelicans for every reasoning level of OpenAI's current frontier lineup: GPT-6 Astra, GPT-6.1 Sol, GPT-6.1 Terra, and GPT-6 Luna. 
 GPT-6.1 Terra is priced at $1/million input tokens and $5/million output - almost half the price of GPT-5.6 Terra and GPT-6.1 Sol, and around 10x the price of GPT-6 Luna.

 Via Hacker News 

 Tags: ai , openai , generative-ai , llms , llm-pricing , pelican-riding-a-bicycle , llm-release , gpt

</details>