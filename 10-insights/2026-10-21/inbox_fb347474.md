---
id: inbox_fb347474
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-5-distill-both-memory-stores-7d0b]]"
title: "v3.59.5 — distill both memory stores"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.5
source: ruflo-releases
published_at: 2026-10-21T04:26:21+00:00
fetched_at: 2026-10-21T23:47:04.681607+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓記憶蒸餾同時處理兩個儲存庫，避免一個庫的資料默默堆積。 **Why** 原本 memory distill 與 daemon 的 consolidate worker 只解析 memory.db，MCP-only 專案常缺少 AgentDB 目標表，每次 tick 都被跳過，實際資料卻累積在 agentdb-memory.db。 **How** 同時解析並蒸餾兩個儲存庫，單一庫失敗不會阻擋另一個；明確指定 --db 時仍只鎖定單一庫。 **What** Ruflo v3.59.5（#4338，修正 #3446），三個 dist-tags 已在 registry 驗證。"
key_points:
  - "memory distill 與 daemon consolidate worker 原本只解析 memory.db"
  - "MCP-only 專案常缺 AgentDB 目標表，每次 tick 被跳過，資料累積在 agentdb-memory.db"
  - "現在兩庫都處理，單庫失敗互不阻擋；明確指定 --db 時仍只鎖定單一庫"
tags: [ruflo, memory-distillation, agentdb, daemon, release-notes]
topics: [agents.frameworks, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.5 — distill both memory stores

讓記憶蒸餾同時處理兩個儲存庫，避免一個庫的資料默默堆積。 **Why** 原本 memory distill 與 daemon 的 consolidate worker 只解析 memory.db，MCP-only 專案常缺少 AgentDB 目標表，每次 tick 都被跳過，實際資料卻累積在 agentdb-memory.db。 **How** 同時解析並蒸餾兩個儲存庫，單一庫失敗不會阻擋另一個；明確指定 --db 時仍只鎖定單一庫。 **What** Ruflo v3.59.5（#4338，修正 #3446），三個 dist-tags 已在 registry 驗證。

### 重點
- memory distill 與 daemon consolidate worker 原本只解析 memory.db
- MCP-only 專案常缺 AgentDB 目標表，每次 tick 被跳過，資料累積在 agentdb-memory.db
- 現在兩庫都處理，單庫失敗互不阻擋；明確指定 --db 時仍只鎖定單一庫

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 Memory distillation now covers both project stores ( #4338 , fixes #3446 ). memory distill run 
and the daemon's consolidate worker previously resolved only memory.db , which in an 
MCP-only project often lacks the AgentDB target tables, so every tick skipped while the actual 
corpus accumulated un-distilled in the sibling agentdb-memory.db . Both stores are now 
resolved and distilled; a per-store failure can't block the other, and an explicit --db still 
pins a single store. 
 
 Published 
 
 @claude-flow/cli@3.59.5 , claude-flow@3.59.5 , ruflo@3.59.5 — latest / alpha / v3alpha 
dist-tags all verified matching on the live registry.

</details>