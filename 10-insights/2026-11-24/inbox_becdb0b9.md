---
id: inbox_becdb0b9
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0052-tomasz-tunguz-will-ai-deflate-like-lightbulbs-or-compo-c940]]"
title: "Will AI Deflate Like Lightbulbs or Compound Like Copper?"
url: https://tomtunguz.com/jevons-works-on-tokens-not-on-dollars/
source: tomasz-tunguz
published_at: 2026-11-24T00:00:00+00:00
fetched_at: 2026-11-27T01:00:17.398734+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 用量會隨價格下降而暴增，但總營收是像電燈泡一樣持平，還是像銅一樣成長，取決於價格彈性。 **Why** 大家常引用傑文斯悖論（越便宜用越多），但用量增加後的營收會怎樣，才決定 AI 市場能不能撐住龐大的算力支出。 **How** 用價格需求彈性衡量：彈性 1 代表降價後花費持平，彈性 0.5 代表花費縮水；作者拿 Ramp 與 OpenRouter 的 token 用量與支出資料，以及 Anthropic S-1 來估算。 **What** Ramp 上價格降 1% 帶動 token 用量增加 4.3%（用量 11.1 倍、支出 4.7 倍），OpenRouter 為 6.8%（用量 50 倍、支出 21 倍）；neocloud GPU 租金一年漲 48%，CoreWeave 續約重新定價 30% 至 50%。Anthropic S-1 顯示 2026 上半年營收成長 13.6 倍至 163 億美元，Opus 4.5 於 2025 年 11 月降低每任務成本後，季營收成長由 48% 升至 132%，隱含彈性遠大於 1。"
key_points:
  - "價格彈性：Ramp 降價 1% → token 用量 +4.3%、OpenRouter +6.8%；用量與支出差距約 2.4 倍（11.1x vs 4.7x、50x vs 21x）"
  - "GPU 目前像銅而非電燈泡：neocloud GPU 租金一年漲 48%，CoreWeave 續約重訂價 30–50%"
  - "Anthropic S-1：2026 上半年營收 13.6 倍至 163 億美元、淨營收留存 900%；Opus 4.5 降低每任務成本後季成長由 48% 升至 132%"
  - "2027 觀察指標：支出與用量差距是否收斂、GPU 租金對 token 均價、前沿實驗室毛利是否維持 40% 以上、毛利能否覆蓋已簽的算力帳單"
tags: [ai-economics, jevons-paradox, price-elasticity, gpu-rents, token-pricing]
topics: [product_and_org.adoption, engineering.inference, foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Will AI Deflate Like Lightbulbs or Compound Like Copper?

AI 用量會隨價格下降而暴增，但總營收是像電燈泡一樣持平，還是像銅一樣成長，取決於價格彈性。

**Why** 大家常引用傑文斯悖論（越便宜用越多），但用量增加後的營收會怎樣，才決定 AI 市場能不能撐住龐大的算力支出。

**How** 用價格需求彈性衡量：彈性 1 代表降價後花費持平，彈性 0.5 代表花費縮水；作者拿 Ramp 與 OpenRouter 的 token 用量與支出資料，以及 Anthropic S-1 來估算。

**What** Ramp 上價格降 1% 帶動 token 用量增加 4.3%（用量 11.1 倍、支出 4.7 倍），OpenRouter 為 6.8%（用量 50 倍、支出 21 倍）；neocloud GPU 租金一年漲 48%，CoreWeave 續約重新定價 30% 至 50%。Anthropic S-1 顯示 2026 上半年營收成長 13.6 倍至 163 億美元，Opus 4.5 於 2025 年 11 月降低每任務成本後，季營收成長由 48% 升至 132%，隱含彈性遠大於 1。

### 重點
- 價格彈性：Ramp 降價 1% → token 用量 +4.3%、OpenRouter +6.8%；用量與支出差距約 2.4 倍（11.1x vs 4.7x、50x vs 21x）
- GPU 目前像銅而非電燈泡：neocloud GPU 租金一年漲 48%，CoreWeave 續約重訂價 30–50%
- Anthropic S-1：2026 上半年營收 13.6 倍至 163 億美元、淨營收留存 900%；Opus 4.5 降低每任務成本後季成長由 48% 升至 132%
- 2027 觀察指標：支出與用量差距是否收斂、GPU 租金對 token 均價、前沿實驗室毛利是否維持 40% 以上、毛利能否覆蓋已簽的算力帳單

**原文：** [tomasz-tunguz](https://tomtunguz.com/jevons-works-on-tokens-not-on-dollars/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → The mantra of the era is Jevons Paradox. 1 The cheaper a commodity is, the more we use of it. 
 But what happened to the revenue from that higher use? Mass production can crush costs like lightbulbs, keeping revenue flat as a % of GDP while volume rises 25,000x. Or total dollars can grow, like copper. 
 What is the price elasticity of demand for AI? 
 Let’s go to the grocery store : if a 50% cut on the price of bread gets you to buy twice as many loaves, your grocery bill stays flat, an elasticity of 1 ; if you only buy 25% more, your bill shrinks, an elasticity of 0.5. 
 

 So far, GPUs look more like copper than lightbulbs : neocloud GPU rents rose 48% over the past year, & CoreWeave repriced 30% to 50% when leases renew. 2 
 

 Both Ramp & OpenRouter show high price elasticity of demand : a 1% price drop drives 4.3% more tokens on Ramp & 6.8% on OpenRouter, as volume ran 11.1x against 4.7x spending on Ramp & 50x against 21x on OpenRouter. 3 , 4 , 5 
 Anthropic’s S-1 is the counterpoint : revenue grew 13.6x to $16.3b in the first half of 2026 on 900% net revenue retention, & when Opus 4.5 cut cost per task in November 2025, quarterly sales growth jumped from 48% to 132%, implying a price elasticity of demand well above 1.0. 6 
 

 More efficient inference cuts the bill inside the lab : shrinking models, reusing past answers & sending easy questions to smaller models. Each trick lowers the cost of a token faster than GPU rents rise. 
 We’re watching these numbers in 2027 : 
 
 Spending against volume : does the 2.4x wedge narrow toward parity like oil & copper, or widen toward lighting? 
 GPU rents against blended token prices : do the two meet as new clusters come online, or keep squeezing lab margins? 7 
 Frontier gross margins : does cheaper serving hold labs above 40% while token prices keep falling? 
 Gross profit against signed compute bills : do dollars compound fast enough to cover them? 
 
 Consumption looks unbounded. How much deflation hits commodity AI tokens is still up for debate. So far, the closest parallel is CPUs : commodity chips deflated while each new frontier generation expanded the dollar market. 
 
 
 
 
 Veblen & Jevon Walk Into a Data Center , Tomasz Tunguz, March 30, 2026. ↩︎ 
 
 
 Silicon Data, Hopper & Ampere GPU rents vs CoreWeave repricing , 16 November 2026, including CoreWeave repricing of 30% to 50% when leases renew. ↩︎ 
 
 
 Ramp, The Ramp AI Index , token volume, token spend & blended price per million tokens, 97 observed weeks, week ending 12 January 2025 through 15 November 2026, plus the October 2026 adoption & spend-per-employee tables. Retrieved 24 November 2026. ↩︎ 
 
 
 OpenRouter API Tracker , data through 23 November 2026. ↩︎ 
 
 
 Both panels have biases : corporate cards miss direct enterprise deals & cloud marketplaces, where nearly half of Anthropic’s revenue lands ; blended prices mix list cuts with routing to cheaper models ; & cached tokens cost up to 90% less. ↩︎ 
 
 
 Anthropic S-1 Analysis: How 7 Key Metrics Stack Up , Tomasz Tunguz, 26 October 2026, including the 11,900+ customers over $100k. ↩︎ 
 
 
 Who Captures the Most Margin in AI? , Tomasz Tunguz. ↩︎

</details>