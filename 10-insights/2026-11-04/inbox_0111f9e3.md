---
id: inbox_0111f9e3
date: 2026-11-04
source_ref: "[[00-inbox/2026-11-04/0002-interconnects-how-big-is-the-open-model-economy-today-4675]]"
title: "How big is the open model economy today?"
url: https://www.interconnects.ai/p/how-well-can-we-measure-open-model
source: interconnects
published_at: 2026-11-04T16:35:44+00:00
fetched_at: 2026-11-06T00:08:18.226023+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 Baseten、Fireworks、Together 等推論新創的 token 量，估算開放模型推論市場有多大。 **Why** 開放模型採用度的所有量測都不精確（平台指標雜訊大、新創數字帶行銷成分、公開評測不完美），需要有人整理出最佳近似，回答它是在成長還是只是 OpenAI/Anthropic 的零頭。 **How** 以三家開放模型推論新創的公開 token 量（log 尺度）與 OpenRouter 開放模型佔比為代理指標，並與 Google 財報公布的全平台 token 量疊圖比較。 **What** 作者的 Interconnects Dashboard 彙整這些數據；數據顯示近乎指數成長，且在 GLM 5.2 帶動開放 agent 躍進之前；Fireworks 稱每日為客戶客製化模型服務逾 40T tokens，較夏季成長逾 2 倍，預期整體秋季數字將遠高於 100T。"
key_points:
  - "代理指標：Baseten、Fireworks、Together AI 公開 token 量加上 OpenRouter 的開放模型佔比；超大雲端（Bedrock、Azure）未拆分開放模型用量"
  - "Fireworks 稱每日為客製化模型服務逾 40T tokens，該垂直領域較夏季成長逾 2 倍，預期總量遠高於 100T"
  - "與 Google 財報公布的 token 量疊圖比較（內文被截斷，未見結論數字）"
tags: [open-models, inference-market, token-volume, interconnects, fireworks]
topics: [foundation_models.open_weights, engineering.inference, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## How big is the open model economy today?

用 Baseten、Fireworks、Together 等推論新創的 token 量，估算開放模型推論市場有多大。

**Why** 開放模型採用度的所有量測都不精確（平台指標雜訊大、新創數字帶行銷成分、公開評測不完美），需要有人整理出最佳近似，回答它是在成長還是只是 OpenAI/Anthropic 的零頭。

**How** 以三家開放模型推論新創的公開 token 量（log 尺度）與 OpenRouter 開放模型佔比為代理指標，並與 Google 財報公布的全平台 token 量疊圖比較。

**What** 作者的 Interconnects Dashboard 彙整這些數據；數據顯示近乎指數成長，且在 GLM 5.2 帶動開放 agent 躍進之前；Fireworks 稱每日為客戶客製化模型服務逾 40T tokens，較夏季成長逾 2 倍，預期整體秋季數字將遠高於 100T。

### 重點
- 代理指標：Baseten、Fireworks、Together AI 公開 token 量加上 OpenRouter 的開放模型佔比；超大雲端（Bedrock、Azure）未拆分開放模型用量
- Fireworks 稱每日為客製化模型服務逾 40T tokens，該垂直領域較夏季成長逾 2 倍，預期總量遠高於 100T
- 與 Google 財報公布的 token 量疊圖比較（內文被截斷，未見結論數字）

**原文：** [interconnects](https://www.interconnects.ai/p/how-well-can-we-measure-open-model)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My longest running agent testbed has been building the Interconnects Dashboard — an aggregator of all of the best data on open model adoption and performance from across the web. This dashboard is freely available and becoming quite useful. Still, all the measurements we have on open model adoption are incredibly imprecise. We have noisy platform metrics, marketing-related metrics from startups, and imperfect public evaluations. It takes an informed eye to figure out where things are going. These research notes are my current best approximations of where we stand. As with most things on Interconnects, our goal is to build well more value than we capture, so the data on the dashboard will remain free for the foreseeable future. These notes will be more raw than many of my articles, a place for sharing what I’m mulling over but don’t have complete evidence for (yet). They will be primarily paid, enabling me to speak more freely. If you work in AI policy or policy-facing research, please reach out to us and we can likely get discounted or free access. The primary question I wanted to address today is: What is the market for open model inference? Is it growing? Is it a rounding error relative to OpenAI/Anthropic? Share I’ve been building the best measurements I can here, primarily using the open model inference startups Baseten, Fireworks, and Together AI as the bellwethers here (along with the open model share of OpenRouter’s token volume, which they thankfully report in their API). The hyperscalers also likely have a major footprint here, e.g. Amazon Bedrock and Azure’s model garden, but I haven’t seen them break down usage by model category. The startups’ fates are much more directly correlated with the success of open model inference as a category. For the latest data, we can start with a slide from my talk on the open model economy (recording here ). These are the public disclosures from the open model startups on their token volume, over time, log-scale. This shows near-exponential growth, before the uptick that would follow GLM 5.2’s step change in open agents . For example, Fireworks announced at their first company conference this week that they’re serving more than 40T tokens per day to customers’ customized models. This is just one slice of their inference, a vertical that they said grew over 2x from this summer, so I would expect their total number this fall to be well above 100T tokens when we get the next update. My first instinct with these numbers has been to ground them versus any closed model or hyperscale company we can, at least in terms of token volume. Thankfully, Google releases token volumes for the entire platform and API usage in their earnings reports. We can overlay those two numbers on top of the open model inference platforms, with the resulting plot below: 
 
 
 Read more

</details>