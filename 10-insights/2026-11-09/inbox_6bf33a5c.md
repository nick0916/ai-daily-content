---
id: inbox_6bf33a5c
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2342-tomasz-tunguz-when-does-the-us-become-a-net-importer-o-a743]]"
title: "When Does the US Become a Net Importer of Tokens?"
url: https://tomtunguz.com/when-does-the-us-become-a-net-importer-of-tokens/
source: tomasz-tunguz
published_at: 2026-11-09T00:00:00+00:00
fetched_at: 2026-11-10T00:04:44.627804+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 需求成長快過美國自己的供電與機房建設速度，美國很可能在 2028–2030 年變成 token 淨進口國。 **Why** AI 需求超過供給，且美國國內資料中心建設放緩。 **How** 用簡單模型推算：所需功率（GW）= token 需求 ÷ 每瓦 token 數；晶片與模型效率提升只能抵銷約 2.5 倍的年成長，超過就會出現缺口。 **What** 若規劃中的專案有 45% 無法併網，2028 年起進口；取消率降到 20% 則延到 2029；即使全部如期完工，2030 年缺口仍會出現。短期 GPU 租價近兩季由 $5 漲到逾 $13/小時，需求幾乎沒有退縮；作者並指出 GPU 小時成本中電力僅佔 5%，資本回收佔 64%。"
key_points:
  - "現有系統加新機房可承受約 2.5 倍年 token 成長；每瓦 token 數約年增 2.9 倍，只有 55% 的排定美國容量準時上線"
  - "規劃專案 45% 失敗→2028 開始進口；20% 失敗→2029；全部如期完成→2030 仍出現缺口"
  - "短期 GPU 租價近兩季由 $5 升至逾 $13/小時，Anthropic 簽下數十億美元溢價 burst 算力，需求價格彈性極低"
tags: [compute-supply, data-center, token-economics, gpu-pricing, power]
topics: [engineering.inference, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## When Does the US Become a Net Importer of Tokens?

AI 需求成長快過美國自己的供電與機房建設速度，美國很可能在 2028–2030 年變成 token 淨進口國。

**Why** AI 需求超過供給，且美國國內資料中心建設放緩。

**How** 用簡單模型推算：所需功率（GW）= token 需求 ÷ 每瓦 token 數；晶片與模型效率提升只能抵銷約 2.5 倍的年成長，超過就會出現缺口。

**What** 若規劃中的專案有 45% 無法併網，2028 年起進口；取消率降到 20% 則延到 2029；即使全部如期完工，2030 年缺口仍會出現。短期 GPU 租價近兩季由 $5 漲到逾 $13/小時，需求幾乎沒有退縮；作者並指出 GPU 小時成本中電力僅佔 5%，資本回收佔 64%。

### 重點
- 現有系統加新機房可承受約 2.5 倍年 token 成長；每瓦 token 數約年增 2.9 倍，只有 55% 的排定美國容量準時上線
- 規劃專案 45% 失敗→2028 開始進口；20% 失敗→2029；全部如期完成→2030 仍出現缺口
- 短期 GPU 租價近兩季由 $5 升至逾 $13/小時，Anthropic 簽下數十億美元溢價 burst 算力，需求價格彈性極低

**原文：** [tomasz-tunguz](https://tomtunguz.com/when-does-the-us-become-a-net-importer-of-tokens/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → With AI demand outpacing supply, & domestic data center construction slowing, soon the US will consume more tokens than it produces. 
 At that point, the US will become a net importer of tokens, just like it is a net importer of rare earth metals. A basic model estimates this switch between 2028 & 2030, depending on how many planned facilities get cancelled. 
 Very roughly, the current systems, with new data centers coming online, can manage 2.5x annual token growth 1 . Above that rate, chip & model efficiency gains can no longer offset domestic demand growth : power required in gigawatts equals tokens demanded divided by tokens per watt. 
 

 If 45% of planned projects fail to connect, imports start by 2028. Cut cancellations to 20%, & the deadline slips to 2029. Even if every proposed facility gets built on time, the gap still opens by 2030 2 . 
 

 Every physical model assumes the price of compute stays constant. In reality, when supply chokes, prices spike. So far, demand has proven remarkably price-inelastic. Over the past two quarters, short-term GPU rental prices surged from $5 to more than $13 per hour 3 , Anthropic signed billions in burst compute at premium rates, & overall demand barely blinked. Buyers simply paid the toll. 
 At what price do people balk? Is it the model labs burning through capital to pre-train the next frontier? The enterprises financing vibe-coding teams that burn hundreds of millions of tokens a week building custom apps? Or consumers asked to pay $40 a month for an autonomous agent subscription? 
 Surely there is some price at which demand will slow & current data center capacity will suffice. But throttling demand through scarcity pricing denies the basic market reality : at a lower cost of production, demand would be orders of magnitude higher. If we do not build the domestic power and facilities to satisfy that demand, tokens will simply be produced elsewhere & imported. 
 The uninhibited growth since GPT 3.5 will be modulated not by lack of access to data, nor algorithmic limits, nor GPU manufacturing speed, but by the broader values of the country. The forthcoming limits on the quantity, size, electrical consumption, & location of data centers will reshape Startupland. 
 
 
 
 
 Demand grows from a 66gw base in 2027, up 61% from 41gw (Goldman Sachs Commodities Research, Wei, Struyven & Dart, May 20, 2026. US data center power 31gw / 41gw / 66gw for 2025 / 2026 / 2027). Efficiency is the counterweight. Tokens per watt compounds about 2.9x a year, blending NVIDIA’s Vera Rubin at 5.4x over GB300, Google’s Ironwood at 2x Trillium & AWS’s Trainium3 at 4x Trainium2 (SemiAnalysis InferenceX, 2026 : Vera Rubin 5.4x GB300 on tokens per watt. NVIDIA claims up to 10x on agentic workloads. Google TPU Ironwood 2x Trillium. AWS Trainium3 4x Trainium2). Supply is the third input, & only 55% of scheduled US capacity lands on time. ↩︎ 
 
 
 The chart is a capacity date, not an economic one. Power is only 5% of the cost of a GPU-hour ; capital recovery is 64%. A $40/mwh spread is worth $0.35b per gigawatt per year, while a 6%-to-9% cost of capital spread is worth $0.84b. Capital wins. Latency finishes the argument : New York to Frankfurt round-trips in 88ms. Behind-the-meter generation covers much of the shortfall, so the real constraint becomes gas turbines, sold out into 2030 (SemiAnalysis, June 25, 2026 ; GE Vernova, July 22, 2026). ↩︎ 
 
 
 Tomasz Tunguz, The Financial Engineering Essential for AI in 2027 , November 3, 2026, analyzing Anthropic’s Form S-1/A disclosures on short-term burst compute surges to $12–$13/GPU-hour (up from $3–$5 six months earlier) and long-term compute commitments. The Ornn Compute Index settled at $12.29/GPU-hour in October 2026. ↩︎

</details>