---
id: inbox_ce179215
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-simon-willison-quoting-daniel-stenberg-e7a6]]"
title: "Quoting Daniel Stenberg"
url: https://simonwillison.net/2026/Nov/18/daniel-stenberg/
source: simon-willison
published_at: 2026-11-18T15:58:27+00:00
fetched_at: 2026-11-19T08:18:12.374292+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "curl 作者用數字反駁「用 AI 把 C 改寫成 Rust」：改寫期間真正的 curl 專案持續進步，AI 複製品跟不上。 **Why** 市面上出現多個由 coding agent 把 curl 從 C 改寫成 Rust 的專案，Stenberg 要說明「改寫」不等於「取代」。 **How** 他用同期數字對比：agent 在三週多把 185,000 行 C 轉成 340,000 行 Rust（他自己數的），同一時間 curl 本尊合併了 300 多個 commit。 **What** Daniel Stenberg 指出 curl 在這三週多修了 200 多個 bug 與少數漏洞，這些修正 Rust 改寫版都沒有；他質疑這些複製品能否持續跟上每月約 200 個修正的節奏。"
key_points:
  - "agent 在三週多內把 185,000 行 C 轉成 340,000 行 Rust（Stenberg 親自數過）"
  - "同期 curl 專案合併 300+ commit、修了 200+ bug 並修補數個漏洞"
  - "核心論點：AI 一次性改寫無法承接上游持續維護的修正流（每月約再 200 個）"
tags: [curl, rust, vibe-porting, coding-agents, maintenance]
topics: [agents.coding_agents, security]
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Daniel Stenberg

curl 作者用數字反駁「用 AI 把 C 改寫成 Rust」：改寫期間真正的 curl 專案持續進步，AI 複製品跟不上。

**Why** 市面上出現多個由 coding agent 把 curl 從 C 改寫成 Rust 的專案，Stenberg 要說明「改寫」不等於「取代」。

**How** 他用同期數字對比：agent 在三週多把 185,000 行 C 轉成 340,000 行 Rust（他自己數的），同一時間 curl 本尊合併了 300 多個 commit。

**What** Daniel Stenberg 指出 curl 在這三週多修了 200 多個 bug 與少數漏洞，這些修正 Rust 改寫版都沒有；他質疑這些複製品能否持續跟上每月約 200 個修正的節奏。

### 重點
- agent 在三週多內把 185,000 行 C 轉成 340,000 行 Rust（Stenberg 親自數過）
- 同期 curl 專案合併 300+ commit、修了 200+ bug 並修補數個漏洞
- 核心論點：AI 一次性改寫無法承接上游持續維護的修正流（每月約再 200 個）

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/18/daniel-stenberg/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

During the time these agents converted 185,000 lines of C code into 340,000 lines of Rust code (I counted), we merged over 300 commits in the actual curl project. We actually improved curl during these a little more than three weeks. A little over 200 bugfixes actually. 200 bugfixes that none of those rust rewrites have. We also fixed a few vulnerabilities. In another month we have done another 200 and maybe fixed a few more vulnerabilities. Will these clones keep up? 
 — Daniel Stenberg , Actual curl rewrites in Rust 

 Tags: daniel-stenberg , curl , rust , security , coding-agents , c , ai , llms , generative-ai , vibe-porting

</details>