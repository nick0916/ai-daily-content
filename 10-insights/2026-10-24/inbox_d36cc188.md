---
id: inbox_d36cc188
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-infoq-main-googles-data-agent-kit-hits-ga-splitting-f01e]]"
title: "Google’s Data Agent Kit Hits GA, Splitting Agent Guardrails Between Skills and IAM"
url: https://www.infoq.com/news/2026/10/data-agent-kit-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-24T08:34:00+00:00
fetched_at: 2026-10-25T01:09:02.668542+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 把程式 agent 連到資料雲的工具包正式上線，並區分「請 agent 停手」與「系統直接拒絕」兩種護欄。 **Why** 讓 agent 操作資料服務時，必須分清哪些限制只是建議、哪些是真正強制。 **How** 一種護欄是 skill 內要求 agent 停止，另一種是 IAM deny policy，直接拒絕該次呼叫。 **What** Google Data Agent Kit 正式 GA，免費，內含 MCP 工具與 37 個開源 skills，可將 coding agent 連接到 15 個以上的 Google Data Cloud 服務。"
key_points:
  - "Data Agent Kit GA：免費的 MCP 工具加 37 個開源 skills，連接 15+ Google Data Cloud 服務"
  - "護欄分兩類：skill 層是請 agent 停止，IAM deny policy 則是系統層直接拒絕呼叫"
  - "實務上需分辨兩者：前者依賴 agent 遵從，後者由 IAM 強制執行"
tags: [google-data-agent-kit, mcp, iam, agent-guardrails, agent-skills]
topics: [agents.mcp, security, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Google’s Data Agent Kit Hits GA, Splitting Agent Guardrails Between Skills and IAM

Google 把程式 agent 連到資料雲的工具包正式上線，並區分「請 agent 停手」與「系統直接拒絕」兩種護欄。

**Why** 讓 agent 操作資料服務時，必須分清哪些限制只是建議、哪些是真正強制。

**How** 一種護欄是 skill 內要求 agent 停止，另一種是 IAM deny policy，直接拒絕該次呼叫。

**What** Google Data Agent Kit 正式 GA，免費，內含 MCP 工具與 37 個開源 skills，可將 coding agent 連接到 15 個以上的 Google Data Cloud 服務。

### 重點
- Data Agent Kit GA：免費的 MCP 工具加 37 個開源 skills，連接 15+ Google Data Cloud 服務
- 護欄分兩類：skill 層是請 agent 停止，IAM deny policy 則是系統層直接拒絕呼叫
- 實務上需分辨兩者：前者依賴 agent 遵從，後者由 IAM 強制執行

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/data-agent-kit-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google has made Data Agent Kit generally available, a free set of MCP tools and 37 open-source skills that connect coding agents to more than fifteen Google Data Cloud services. Two kinds of guardrail ship with it, and practitioners need to tell them apart: one is a skill asking the agent to stop, the other an IAM deny policy that refuses the call. By Steef-Jan Wiggers

</details>