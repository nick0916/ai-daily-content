---
id: inbox_402b450c
date: 2026-11-27
source_ref: "[[00-inbox/2026-11-27/0144-hackernews-show-hn-bouncemarket-a-live-prediction-m-665a]]"
title: "Show HN: bouncemarket – a live prediction market game for a bouncing ball"
url: https://bouncemarket.minhanhday.com/
source: hackernews
published_at: 2026-11-27T15:01:50+00:00
fetched_at: 2026-11-28T01:51:16.549819+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個讓人對彈跳球落點下注的即時預測市場小遊戲。 **How** 球的整個下落過程在伺服器端模擬，再透過 server-sent events 搭配小緩衝串流給各客戶端；每次下落由起始位置決定性（deterministic）地決定，可精確重播，但起始位置的微小差異會改變結果。 **What** Show HN 作品 bouncemarket，市場中有作者以簡單規則寫的 AI 交易者，當單一回合超過五人時就退場；作者徵求對機制是否一看就懂的回饋。"
key_points:
  - "伺服器端模擬球的下落，以 server-sent events 串流到客戶端"
  - "每次下落由起始位置決定，可完整重播供事後分析"
  - "AI 交易者採作者自訂的簡單規則，回合超過五人即退出"
tags: [show-hn, prediction-market, server-sent-events, game]
topics: [product_and_org.product]
importance: 1
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: bouncemarket – a live prediction market game for a bouncing ball

一個讓人對彈跳球落點下注的即時預測市場小遊戲。

**How** 球的整個下落過程在伺服器端模擬，再透過 server-sent events 搭配小緩衝串流給各客戶端；每次下落由起始位置決定性（deterministic）地決定，可精確重播，但起始位置的微小差異會改變結果。

**What** Show HN 作品 bouncemarket，市場中有作者以簡單規則寫的 AI 交易者，當單一回合超過五人時就退場；作者徵求對機制是否一看就懂的回饋。

### 重點
- 伺服器端模擬球的下落，以 server-sent events 串流到客戶端
- 每次下落由起始位置決定，可完整重播供事後分析
- AI 交易者採作者自訂的簡單規則，回合超過五人即退出

**原文：** [hackernews](https://bouncemarket.minhanhday.com/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

a ball will fall. trade on where it lands. I made this game! Some technical details: The entire drop of the ball is simulated server-side, then streamed to each client as server-sent events with a small buffer. Every drop is deterministic from its starting position, so rounds can be replayed exactly for later analysis, but tiny variations in starting position can change the ultimate outcome. There's some AI traders to keep the market moving, but they drop out in any round that has more than five people. They operate using a naive set of rules that I wrote for them, so they're not too hard to beat -- it's when the market is full of real people that it gets tricky. Curious to get feedback on anything you would change, and especially whether the mechanics were clear right away or not.

</details>