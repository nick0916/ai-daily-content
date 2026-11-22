---
id: inbox_b1b11592
date: 2026-11-21
source_ref: "[[00-inbox/2026-11-21/0237-simon-willison-muru-4a5d]]"
title: "Muru"
url: https://simonwillison.net/2026/Nov/21/muru/
source: simon-willison
published_at: 2026-11-21T23:56:28+00:00
fetched_at: 2026-11-22T02:43:02.026217+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者邊開發邊公開記錄的 AI 輔助 Rust 伺服器，用來跑 Python 網頁應用。 **Why** Graham Dumpleton 二十年前創立 mod_wsgi，一直在思考服務 Python web 應用的理想方式。 **How** 以 AI 輔助開發 Rust 伺服器，同時發表詳盡的開發日誌；他表示 AI 做了表面上大部分工作，但判斷「還不夠好」仍由他負責，靠的是 mod_wsgi 二十年的經驗。 **What** Muru 目標是在開發與正式環境中同時支援 ASGI 與 WSGI。自 2026-11-04 起三週內已發表 18 篇文章，主題含 import once fork many、releases not restarts、scaling to zero、工具列追蹤等；其中〈AI as a lifestyle choice〉被 Simon Willison 特別推薦。"
key_points:
  - "Muru 是 Graham Dumpleton（mod_wsgi 作者）以 AI 輔助開發的 Rust 伺服器，支援 ASGI 與 WSGI"
  - "2026-11-04 至 11-21 共發表 18 篇開發日誌，涵蓋 import once fork many、canary、scale to zero、Kubernetes 整合、工具列 tracing"
  - "核心心得：AI 做大部分表面工作，判斷「什麼還不夠好」仍靠人與多年領域經驗"
tags: [muru, graham-dumpleton, mod-wsgi, rust, ai-assisted-programming]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Muru

作者邊開發邊公開記錄的 AI 輔助 Rust 伺服器，用來跑 Python 網頁應用。

**Why** Graham Dumpleton 二十年前創立 mod_wsgi，一直在思考服務 Python web 應用的理想方式。

**How** 以 AI 輔助開發 Rust 伺服器，同時發表詳盡的開發日誌；他表示 AI 做了表面上大部分工作，但判斷「還不夠好」仍由他負責，靠的是 mod_wsgi 二十年的經驗。

**What** Muru 目標是在開發與正式環境中同時支援 ASGI 與 WSGI。自 2026-11-04 起三週內已發表 18 篇文章，主題含 import once fork many、releases not restarts、scaling to zero、工具列追蹤等；其中〈AI as a lifestyle choice〉被 Simon Willison 特別推薦。

### 重點
- Muru 是 Graham Dumpleton（mod_wsgi 作者）以 AI 輔助開發的 Rust 伺服器，支援 ASGI 與 WSGI
- 2026-11-04 至 11-21 共發表 18 篇開發日誌，涵蓋 import once fork many、canary、scale to zero、Kubernetes 整合、工具列 tracing
- 核心心得：AI 做大部分表面工作，判斷「什麼還不夠好」仍靠人與多年領域經驗

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/21/muru/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Muru 
Graham Dumpleton started mod_wsgi 20 years ago, and has been thinking about the ideal way to serve Python web applications in production ever since. 
 Muru is his new, AI-assisted Rust server that aims to provide the best possible tools for running ASGI and WSGI Python apps both in development and production. 
 As he did with wrapture , he's been publishing an extraordinarily detailed account of the project as he works on it - as part of his development process. 
 Here's everything he's published so far, all in the last three weeks: 
 
 2026-11-04 — Twenty years of mod_wsgi, and what comes next 
 2026-11-05 — A first look at Muru 
 2026-11-07 — Muru: looking inside the workers 
 2026-11-08 — Muru: how it fits together 
 2026-11-09 — Muru: import once, fork many 
 2026-11-10 — Muru: HTTPS in development 
 2026-11-11 — Muru: WSGI and ASGI together 
 2026-11-11 — AI as a lifestyle choice 
 2026-11-12 — Muru: releases, not restarts 
 2026-11-13 — Muru: canaries without a service mesh 
 2026-11-14 — Muru: a better tenant in a container 
 2026-11-15 — Muru: working with Kubernetes, not around it 
 2026-11-16 — Muru: scaling from what the workers report 
 2026-11-17 — Muru: scaling to zero 
 2026-11-18 — Muru: overlays on a schedule 
 2026-11-19 — Muru: noticing and responding 
 2026-11-20 — Muru: a toolbar on every page 
 2026-11-21 — Muru: tracing in the toolbar 
 
 That post about AI as a lifestyle choice is particularly worth a read: 
 
 The AI may be doing a lot of the work on the surface, but deciding what isn't good enough yet is still down to me, and twenty years of getting things wrong with mod_wsgi turns out to be useful for that. I am prepared to put in the hard work to keep polishing Muru until it is something I would trust, and something you would too. 
 

 Tags: graham-dumpleton , modwsgi , python , wsgi , ai , rust , asgi , generative-ai , llms , ai-assisted-programming

</details>