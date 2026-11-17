---
id: inbox_a608b0c8
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-substack-lennys-newsletter-how-i-fight-token-fraud-as-a-solo-founde-7c64]]"
title: "How I fight token fraud as a solo founder"
url: https://www.lennysnewsletter.com/p/how-i-fight-token-fraud-as-a-solo
source: substack-lennys-newsletter
published_at: 2026-11-16T13:04:09+00:00
fetched_at: 2026-11-17T23:23:57.992508+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 產品的每次模型呼叫都花真錢，所以被盜刷算力就等於直接燒錢。 **Why** 這位 ChatPRD 的獨立創辦人過去一年因 token 詐欺損失數萬美元，並耗掉幾乎所有工程精力。 **How** 她結合商業控制與技術防禦，並用 Jev loop 即時分類詐欺行為。 **What** Claire Vo 的 How I AI 單人集數，整理她在 ChatPRD 遇到的六種濫用模式（刷免費試用、轉售 promo code、產品中繼、24/7 運行的自訂 MCP 等）與四類濫用者。她最終永久關閉免費試用，並提醒 AI 客服也可能成為攻擊入口；核心結論是「賣 AI 就是賣算力」。（內文僅為節目大綱，細節有限）"
key_points:
  - "六種攻擊模式含刷免費試用、轉售 promo code、產品中繼、自訂 MCP 當 24/7 運算工人，結果讓她永久關閉免費試用"
  - "防禦面向包含商業控制、技術防禦，以及用 Jev 即時分類詐欺；提到的工具有 Stripe Radar、Vercel AI Gateway、Vercel BotID、Vercel Firewall、Clerk"
  - "AI 客服可能變成攻擊向量；核心原則為「If you sell AI, you sell compute」"
tags: [token-fraud, ai-abuse, free-trial, chatprd, mcp-abuse]
topics: [security, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How I fight token fraud as a solo founder

AI 產品的每次模型呼叫都花真錢，所以被盜刷算力就等於直接燒錢。

**Why** 這位 ChatPRD 的獨立創辦人過去一年因 token 詐欺損失數萬美元，並耗掉幾乎所有工程精力。

**How** 她結合商業控制與技術防禦，並用 Jev loop 即時分類詐欺行為。

**What** Claire Vo 的 How I AI 單人集數，整理她在 ChatPRD 遇到的六種濫用模式（刷免費試用、轉售 promo code、產品中繼、24/7 運行的自訂 MCP 等）與四類濫用者。她最終永久關閉免費試用，並提醒 AI 客服也可能成為攻擊入口；核心結論是「賣 AI 就是賣算力」。（內文僅為節目大綱，細節有限）

### 重點
- 六種攻擊模式含刷免費試用、轉售 promo code、產品中繼、自訂 MCP 當 24/7 運算工人，結果讓她永久關閉免費試用
- 防禦面向包含商業控制、技術防禦，以及用 Jev 即時分類詐欺；提到的工具有 Stripe Radar、Vercel AI Gateway、Vercel BotID、Vercel Firewall、Clerk
- AI 客服可能變成攻擊向量；核心原則為「If you sell AI, you sell compute」

**原文：** [substack-lennys-newsletter](https://www.lennysnewsletter.com/p/how-i-fight-token-fraud-as-a-solo)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Today I’m walking you through a problem that has cost me tens of thousands of dollars over the past year and eaten almost all of my engineering energy: token fraud. I’m the solo founder of ChatPRD, a bootstrapped AI platform for product managers, and fraudsters have been farming our free trials, reselling promo codes, wrapping the product in relays, and installing a custom MCP that ran as a 24/7 compute worker. I’ll walk through the six abuse patterns I’ve seen, the business and technical controls I put in place, the Jev loop that classifies fraud in real time, and why I finally killed free trials for good. If you sell AI, you sell compute. Listen or watch on YouTube , Spotify , or Apple Podcasts What you’ll learn: What token fraud is and why AI SaaS is uniquely exposed The six attack patterns I’ve seen at ChatPRD Why I finally turned off free trials for good The Roblox and Fortnite maps I accidentally funded Business controls that actually slow fraud down How I use Jev to classify fraud in real time Why your AI support desk can become an attack vector What “if you sell AI, you sell compute” actually means Brought to you by: WorkOS —Make your app enterprise-ready, with SSO, SCIM, RBAC, and more Auros —The human network behind AI In this episode, we cover: ( 00:00 ) Token fraud and what it cost me ( 05:25 ) Six abuse patterns ( 11:24 ) Four kinds of abusers ( 13:45 ) Business controls ( 21:27 ) Technical defenses ( 30:25 ) Bots that watch the bots ( 35:30 ) Final takeaways Tools referenced: • Stripe Radar: https://stripe.com/radar • Vercel AI Gateway: https://vercel.com/docs/ai-gateway • Vercel Bot ID: https://vercel.com/docs/botid • Vercel Firewall: https://vercel.com/docs/vercel-firewall • Clerk: https://clerk.com/ • Codex: https://openai.com/codex • Jev (TypeSafe AI): https://docs.typesafe.ai/introduction/quickstart Other references: • Claire Vo on token fraud at ChatPRD: https://x.com/clairevo/status/2119985786045227197 • Gareth Wham (Atlassian) on fighting AI abuse: https://x.com/gareth_w/status/2120226872177095114 • FBI Internet Crime Complaint Center (IC3): https://www.ic3.gov • Simon Willison’s pelican riding a bicycle: https://simonwillison.net/tags/pelican-riding-a-bicycle/ • How I AI: I’m using Jev more than Opus 5.5 or GPT-6: https://www.youtube.com/watch?v=-KIBgpGA_XI Where to find Claire Vo: ChatPRD: https://www.chatprd.ai/ Website: https://clairevo.com/ LinkedIn: https://www.linkedin.com/in/clairevo/ X: https://x.com/clairevo Production and marketing by https://penname.co/ . For inquiries about sponsoring the podcast, email jordan@penname.co.

</details>