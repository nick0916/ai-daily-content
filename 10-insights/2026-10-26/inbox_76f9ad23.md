---
id: inbox_76f9ad23
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-infoq-main-cloudflares-auto-router-rates-each-reque-5b3f]]"
title: "Cloudflare’s Auto Router Rates Each Request for Stakes, from the Most Recent Turns"
url: https://www.infoq.com/news/2026/10/cloudflare-auto-router/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-26T10:20:00+00:00
fetched_at: 2026-10-27T01:32:50.644676+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓系統依每個請求的難度與風險自動挑模型，簡單的用便宜模型、重要的用強模型。 **Why** 所有請求都用最強模型成本太高，但用弱模型處理高風險請求又有風險。 **How** 以分類器對每個請求的複雜度、模糊度、風險（stakes）與上下文依賴度評分，再選擇模型，且風險評估著重最近幾輪對話。 **What** Cloudflare 在 AI Gateway 推出 Auto Router 公開測試版。Cloudflare 自家 benchmark 顯示成功率比 Claude Opus 5.5 低十個百分點，成本為三分之一；實務工作者質疑長 agent session 中風險資訊如何被保留。"
key_points:
  - "分類器依複雜度、模糊度、stakes、context dependence 四個維度評分選模型"
  - "自家 benchmark：成功率比 Claude Opus 5.5 低 10 點，成本約三分之一"
  - "疑慮：長 agent session 中 stakes 如何延續，因評分看最近幾輪"
tags: [model-routing, cloudflare, ai-gateway, cost-optimization, auto-router]
topics: [engineering.inference, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare’s Auto Router Rates Each Request for Stakes, from the Most Recent Turns

讓系統依每個請求的難度與風險自動挑模型，簡單的用便宜模型、重要的用強模型。

**Why** 所有請求都用最強模型成本太高，但用弱模型處理高風險請求又有風險。

**How** 以分類器對每個請求的複雜度、模糊度、風險（stakes）與上下文依賴度評分，再選擇模型，且風險評估著重最近幾輪對話。

**What** Cloudflare 在 AI Gateway 推出 Auto Router 公開測試版。Cloudflare 自家 benchmark 顯示成功率比 Claude Opus 5.5 低十個百分點，成本為三分之一；實務工作者質疑長 agent session 中風險資訊如何被保留。

### 重點
- 分類器依複雜度、模糊度、stakes、context dependence 四個維度評分選模型
- 自家 benchmark：成功率比 Claude Opus 5.5 低 10 點，成本約三分之一
- 疑慮：長 agent session 中 stakes 如何延續，因評分看最近幾輪

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/cloudflare-auto-router/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare has released Auto Router in public beta through AI Gateway, picking a model per request from a classifier that scores complexity, ambiguity, stakes and context dependence. Cloudflare’s own benchmark puts it ten points below Claude Opus 5.5 on success rate at a third of the cost, and practitioners have questioned how stakes survive a long agent session. By Steef-Jan Wiggers

</details>