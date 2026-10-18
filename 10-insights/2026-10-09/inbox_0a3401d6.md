---
id: inbox_0a3401d6
date: 2026-10-09
source_ref: "[[00-inbox/2026-10-09/0256-simon-willison-deno-is-joining-cloudflare-3a8d]]"
title: "Deno is joining Cloudflare"
url: https://simonwillison.net/2026/Oct/9/deno-is-joining-cloudflare/
source: simon-willison
published_at: 2026-10-09T22:48:37+00:00
fetched_at: 2026-10-18T03:05:17.820537+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 宣布直接收購 Deno。Deno 團隊在 8 月釋出 celld 初版，這是 Cloudflare Workers 中 Durable Objects 模式的開源實作；Cloudflare 計畫以 celld 為基礎，讓 workerd 自行託管成為使用 Workers 程式模型建置與執行應用的一等公民方式。壞消息是 Cloudflare 只會再支援 Deno runtime 一年，提供每月釋出的 bug 修復與安全更新，之後終止開發，但 Deno 仍會保持開源，歡迎他人接手。Deno 與 Node.js 創作者 Ryan Dahl 在 Hacker News 回應表示這是共同決定，他認為 Deno 被 Node 相容性的引力捲入、被迫完全比照 Node 行為，而邊際的效能、UX 或安全優勢不夠，他更想建構新的抽象，celld 只靠物件儲存做協調與持久化，是全新的伺服器開發模型。Simon 個人最喜歡 Deno 的權限系統；Node.js 在 v20.0.0（2023 年 4 月）加入類似模型、v22.13.0（2025 年 1 月）宣告穩定，但尚不支援對特定網路主機做允許清單，網路只有開或關。"
key_points:
  - "Cloudflare 收購 Deno，Deno runtime 僅再支援一年（每月釋出 bug 修復與安全更新），之後停止開發但維持開源"
  - "收購目標是以 celld（Durable Objects 模式的開源實作）讓 workerd 自行託管成為一等公民"
  - "Node.js 權限模型 v20.0.0 加入、v22.13.0 穩定，但仍無法對特定網路主機設定允許清單"
tags: [deno, cloudflare, acquisition, celld, sandboxing]
topics: [product_and_org.leadership, security]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Deno is joining Cloudflare

Cloudflare 宣布直接收購 Deno。Deno 團隊在 8 月釋出 celld 初版，這是 Cloudflare Workers 中 Durable Objects 模式的開源實作；Cloudflare 計畫以 celld 為基礎，讓 workerd 自行託管成為使用 Workers 程式模型建置與執行應用的一等公民方式。壞消息是 Cloudflare 只會再支援 Deno runtime 一年，提供每月釋出的 bug 修復與安全更新，之後終止開發，但 Deno 仍會保持開源，歡迎他人接手。Deno 與 Node.js 創作者 Ryan Dahl 在 Hacker News 回應表示這是共同決定，他認為 Deno 被 Node 相容性的引力捲入、被迫完全比照 Node 行為，而邊際的效能、UX 或安全優勢不夠，他更想建構新的抽象，celld 只靠物件儲存做協調與持久化，是全新的伺服器開發模型。Simon 個人最喜歡 Deno 的權限系統；Node.js 在 v20.0.0（2023 年 4 月）加入類似模型、v22.13.0（2025 年 1 月）宣告穩定，但尚不支援對特定網路主機做允許清單，網路只有開或關。

### 重點
- Cloudflare 收購 Deno，Deno runtime 僅再支援一年（每月釋出 bug 修復與安全更新），之後停止開發但維持開源
- 收購目標是以 celld（Durable Objects 模式的開源實作）讓 workerd 自行託管成為一等公民
- Node.js 權限模型 v20.0.0 加入、v22.13.0 穩定，但仍無法對特定網路主機設定允許清單

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/9/deno-is-joining-cloudflare/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Deno is joining Cloudflare 
The Deno team released the first version of celld back in August - their open source implementation of the Durable Objects pattern from Cloudflare Workers. 
 Today, Cloudflare are acquiring Deno outright, with the goal of building on celld to "make workerd self-hosting a first-class supported way to build and run apps using the Workers programming model" (see the Cloudflare blog .) 
 The bad news is that Deno itself will not be maintained by Cloudflare beyond the next year: 
 
 We will support the Deno runtime for another year with monthly releases containing bug fixes and security updates. After that year we will end our development of the Deno runtime. Deno will remain open source, and we welcome others who want to continue its development. 
 
 Deno (and Node.js) creator Ryan Dahl explained that decision in a comment on Hacker News: 
 
 It's a joint decision and I agree with it. I'm most invested in its success and have put the most work into it - and I no longer think it's where I can do the most important work. There are some good ideas in Deno and it's well engineered - but it ultimately is not solving big problems. It has been sucked into the gravity well of node compatibility, which forces it to behave exactly as Node does. Why reimplement Node? It works. Marginal performance or UX or security benefits are not enough. 
 I'm interested in building powerful new abstractions. celld has been working remarkably well, depending only on object storage for coordination and persistence. It is not just a slightly different API to interact with the file system or network - it's an entirely new model for server development. 
 
 My favorite feature of Deno has long been the permissions system, where you can run a Deno script and specify exactly which files and folders it can read and write to, and which network hosts it can access. 
 Node.js has a similar permissions model these days, added in Node v20.0.0 in April 2023 and declared stable in Node v22.13.0 in January 2025. They don't yet support allow-listing specific network hosts though - networking is either on or off.

 Via Hacker News 

 Tags: cloudfront , javascript , nodejs , ryan-dahl , sandboxing , deno

</details>