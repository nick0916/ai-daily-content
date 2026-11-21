---
id: inbox_984ca7c1
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-simon-willison-token-fraud-is-here-and-its-bad-youtube-8f3c]]"
title: "Token fraud is here and it’s BAD (YouTube)"
url: https://simonwillison.net/2026/Nov/20/token-fraud-is-here-and-its-bad/
source: simon-willison
published_at: 2026-11-20T02:49:57+00:00
fetched_at: 2026-11-21T00:53:03.126879+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 產品的免費試用被人拿來薅 token，轉賣或拿去做生意。 **Why** ChatPRD 創辦人 Claire Vo 發現有團體濫用免費試用，不只自己用，還轉賣 token 或在她的 agent 上跑商業營運。 **How** 濫用者輪流用免費試用與優惠碼，再透過通道接到她的 agent；Simon Willison 推測常見的「鵜鶘騎腳踏車 SVG」prompt 是用來探測底層模型，因為不同模型家族有可辨識的特徵。 **What** ChatPRD 是幫 PM 把想法變成 spec 的 AI 平台；Claire 在 YouTube 影片中描述此事，其中一個案例是國際 Roblox / Fortnite 地圖工作室用這個 agent 建地圖。她最後決定完全取消免費試用。"
key_points:
  - "濫用手法：輪流使用免費試用與優惠碼，再通道接入 ChatPRD agent，用來轉賣 token 或建構 Roblox、Fortnite 地圖等商業用途"
  - "常見 prompt 是鵜鶘騎腳踏車 SVG，Simon 推測用來辨識底層模型（類似他在 OpenRouter 上猜測 stealth 預覽模型的做法）"
  - "Claire Vo 的因應：完全終止免費試用"
tags: [token-fraud, free-trial-abuse, ai-misuse, chatprd, pelican-riding-a-bicycle]
topics: [security, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Token fraud is here and it’s BAD (YouTube)

AI 產品的免費試用被人拿來薅 token，轉賣或拿去做生意。

**Why** ChatPRD 創辦人 Claire Vo 發現有團體濫用免費試用，不只自己用，還轉賣 token 或在她的 agent 上跑商業營運。

**How** 濫用者輪流用免費試用與優惠碼，再透過通道接到她的 agent；Simon Willison 推測常見的「鵜鶘騎腳踏車 SVG」prompt 是用來探測底層模型，因為不同模型家族有可辨識的特徵。

**What** ChatPRD 是幫 PM 把想法變成 spec 的 AI 平台；Claire 在 YouTube 影片中描述此事，其中一個案例是國際 Roblox / Fortnite 地圖工作室用這個 agent 建地圖。她最後決定完全取消免費試用。

### 重點
- 濫用手法：輪流使用免費試用與優惠碼，再通道接入 ChatPRD agent，用來轉賣 token 或建構 Roblox、Fortnite 地圖等商業用途
- 常見 prompt 是鵜鶘騎腳踏車 SVG，Simon 推測用來辨識底層模型（類似他在 OpenRouter 上猜測 stealth 預覽模型的做法）
- Claire Vo 的因應：完全終止免費試用

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/20/token-fraud-is-here-and-its-bad/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Token fraud is here and it’s BAD (YouTube) 
Claire Vo runs ChatPRD , an AI platform that helps product managers "turn an idea into a spec". The product has been live since the GPT-4 era, and Claire has been building it in public for much of that time. 
 In this YouTube video (see also the accompanying Twitter post ) Claire describes the flood of token fraud she has seen from groups abusing the product's free trial, sometimes just to get free AI usage but often to resell tokens or run other commercial enterprises on top of the ChatPRD agent. 
 
 I am funding a international Roblox and Fortnite map studio. They run a loop of free trials and promo codes and then tunnel to my agent and use it to build Roblox and Fortnite maps. 
 
 Apparently one of the common prompts Claire saw running through her agent involved SVGs of pelicans riding bicycles! Presumably the token scammers are using that to help sniff the underlying models - different model families have a definite signature, and I've used it like this in the past to try and guess the identity of stealth preview models on platforms like OpenRouter. 
 Claire is winding down her free trials entirely, which sadly looks like the right decision in the face of this abuse.

 Tags: youtube , ai , generative-ai , llms , pelican-riding-a-bicycle , ai-misuse

</details>