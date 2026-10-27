---
id: inbox_a63788c6
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2337-infoq-main-how-anthropic-redesigned-source-control-f5d3]]"
title: "How Anthropic Redesigned Source Control for AI-Driven Development"
url: https://www.infoq.com/news/2026/10/anthropic-source-control/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-27T11:25:00+00:00
fetched_at: 2026-10-27T23:45:22.390971+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 把程式碼倉庫的操作搬到伺服器端，讓 AI agent 與 CI 不必在本機放完整 Git 資料。 **How** Scion 是新的版本控制系統，把 repository 操作移到伺服器端，採用 content-addressed storage 與分層快取，服務 agent 和 CI 工作流。 **What** Anthropic 將其 monorepo 從 Git 遷移到 Scion。設計上以放棄離線獨立作業為代價，換取本機資料更少與共用基礎設施。"
key_points:
  - "Anthropic 將 monorepo 從 Git 遷移到自建的 Scion"
  - "Scion 把 repository 操作移到伺服器端，使用 content-addressed storage 與分層快取，針對 agent 與 CI 工作流"
  - "取捨：犧牲離線獨立性，換取較少本機資料與共用基礎設施"
tags: [anthropic, source-control, scion, monorepo, ai-agents]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 4
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How Anthropic Redesigned Source Control for AI-Driven Development

Anthropic 把程式碼倉庫的操作搬到伺服器端，讓 AI agent 與 CI 不必在本機放完整 Git 資料。

**How** Scion 是新的版本控制系統，把 repository 操作移到伺服器端，採用 content-addressed storage 與分層快取，服務 agent 和 CI 工作流。

**What** Anthropic 將其 monorepo 從 Git 遷移到 Scion。設計上以放棄離線獨立作業為代價，換取本機資料更少與共用基礎設施。

### 重點
- Anthropic 將 monorepo 從 Git 遷移到自建的 Scion
- Scion 把 repository 操作移到伺服器端，使用 content-addressed storage 與分層快取，針對 agent 與 CI 工作流
- 取捨：犧牲離線獨立性，換取較少本機資料與共用基礎設施

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/anthropic-source-control/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anthropic recently detailed how it migrated its monorepo from Git to Scion. Scion is a source control system that moves repository operations to the server side and uses content-addressed storage and tiered caches for agent and CI workloads. The design sacrifices offline independence for less local data and shared infrastructure. By Eran Stiller

</details>