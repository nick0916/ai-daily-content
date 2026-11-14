---
id: inbox_ea1ae0ee
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-infoq-main-google-open-sources-ambient-quality-agen-6393]]"
title: "Google Open Sources Ambient Quality Agent (AQuA) to Diagnose Production AI Agent Failures"
url: https://www.infoq.com/news/2026/11/google-ambient-agent-prod/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-13T13:53:00+00:00
fetched_at: 2026-11-14T01:52:25.625298+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 開源一套工具，從 AI agent 上線後的真實對話中找出重複出現的錯誤並追查原因。 **Why** AI agent 上線後的失敗常藏在大量對話中，很難靠人工找出重複模式與根因。 **How** AQuA 分析 production 的 agent session，驗證重複出現的失敗模式，並對照已部署的原始碼快照調查根本原因。 **What** Google 開源的參考實作 AQuA（Ambient Quality Agent）。在 32 個 session 的重播中，開發者調整 prompt 後，略過座位選擇的 session 從 15 降到 2，遺漏飲食偏好從 7 降到 0。"
key_points:
  - "AQuA 是 Google 開源的 reference implementation，分析 production agent session 並驗證重複失敗模式"
  - "根因調查會對照已部署的原始碼快照"
  - "32 個 session 重播：座位選擇被略過 15→2，飲食偏好遺漏 7→0（修改 prompt 後）"
tags: [google, aqua, agent-observability, failure-analysis, open-source]
topics: [engineering.evals, agents.frameworks]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Open Sources Ambient Quality Agent (AQuA) to Diagnose Production AI Agent Failures

Google 開源一套工具，從 AI agent 上線後的真實對話中找出重複出現的錯誤並追查原因。

**Why** AI agent 上線後的失敗常藏在大量對話中，很難靠人工找出重複模式與根因。

**How** AQuA 分析 production 的 agent session，驗證重複出現的失敗模式，並對照已部署的原始碼快照調查根本原因。

**What** Google 開源的參考實作 AQuA（Ambient Quality Agent）。在 32 個 session 的重播中，開發者調整 prompt 後，略過座位選擇的 session 從 15 降到 2，遺漏飲食偏好從 7 降到 0。

### 重點
- AQuA 是 Google 開源的 reference implementation，分析 production agent session 並驗證重複失敗模式
- 根因調查會對照已部署的原始碼快照
- 32 個 session 重播：座位選擇被略過 15→2，飲食偏好遺漏 7→0（修改 prompt 後）

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/google-ambient-agent-prod/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google has open-sourced AQuA, a reference implementation that analyzes production AI agent sessions, verifies recurring failure patterns, and investigates root causes against deployed source snapshots. In a 32-session replay, developers reduced seat selection bypasses from 15 sessions to two and dietary preference omissions from seven to zero after prompt changes. By Leela Kumili

</details>