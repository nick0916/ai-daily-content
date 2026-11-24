---
id: inbox_d10bfcfd
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-infoq-main-netflix-at-qconsf-2026-retrofitting-the-2e75]]"
title: "Netflix at QConSF 2026: Retrofitting the SDLC for AI Coding Agents"
url: https://www.infoq.com/news/2026/11/netflix-sdlc-ai-coding-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-23T14:58:00+00:00
fetched_at: 2026-11-24T02:15:52.713910+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "改造軟體開發流程，讓 AI 寫程式 agent 和工程師能一起交付。 **Why** AI coding agent 加入後，原有 SDLC 需要調整，才能讓人與 agent 協同出貨。 **How** 撰寫同時給人與 agent 讀的架構決策紀錄，加入只回報已驗證阻塞問題的 review agent，並透過單一 MCP tool 提供各領域的 GraphRAG context。 **What** Netflix Commerce 團隊的 Mark Khuzam 在 QCon San Francisco 2026 分享：寫了 45 份 ADR、review agent 只張貼經驗證的 blocker、以單一 MCP tool 提供 per-domain GraphRAG。"
key_points:
  - "寫了 45 份同時供人與 agent 閱讀的 architecture decision records"
  - "review agent 只張貼已驗證的 blocker，降低雜訊"
  - "以單一 MCP tool 提供 per-domain GraphRAG context"
tags: [netflix, sdlc, coding-agents, graphrag, mcp]
topics: [agents.coding_agents, agents.mcp, engineering.rag]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Netflix at QConSF 2026: Retrofitting the SDLC for AI Coding Agents

改造軟體開發流程，讓 AI 寫程式 agent 和工程師能一起交付。

**Why** AI coding agent 加入後，原有 SDLC 需要調整，才能讓人與 agent 協同出貨。

**How** 撰寫同時給人與 agent 讀的架構決策紀錄，加入只回報已驗證阻塞問題的 review agent，並透過單一 MCP tool 提供各領域的 GraphRAG context。

**What** Netflix Commerce 團隊的 Mark Khuzam 在 QCon San Francisco 2026 分享：寫了 45 份 ADR、review agent 只張貼經驗證的 blocker、以單一 MCP tool 提供 per-domain GraphRAG。

### 重點
- 寫了 45 份同時供人與 agent 閱讀的 architecture decision records
- review agent 只張貼已驗證的 blocker，降低雜訊
- 以單一 MCP tool 提供 per-domain GraphRAG context

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/netflix-sdlc-ai-coding-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

At QCon San Francisco 2026, Mark Khuzam of Netflix explained how the Commerce team retrofitted its SDLC so AI coding agents and engineers could ship together. The team wrote 45 architecture decision records for people and agents, added a review agent that posts only verified blockers, and serves per-domain GraphRAG context through a single MCP tool. By Andrew Hoblitzell

</details>