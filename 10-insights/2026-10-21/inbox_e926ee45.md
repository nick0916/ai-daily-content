---
id: inbox_e926ee45
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-4-hive-mind-init-persistence-contr-e20e]]"
title: "v3.59.4 — hive-mind_init persistence contract fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.4
source: ruflo-releases
published_at: 2026-10-21T02:30:15+00:00
fetched_at: 2026-10-21T23:47:04.682110+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 hive-mind_init 的實際行為符合它所宣告的持久化設定。 **Why** 先前 persist:false 的回應聲稱已關閉持久化，但 state.json 與 bootstrap secret 仍會被寫入，回應與實際行為不一致。 **How** maxAgents、memoryBackend、persist 在任何檔案寫入前先依 MCP schema 驗證；persist:false 時兩個檔案都不寫。 **What** Ruflo v3.59.4（#4336），legacy status fallback 由 byzantine 改為 raft，與 init 的預設值一致；三個 dist-tags 已在 registry 驗證。"
key_points:
  - "maxAgents、memoryBackend、persist 在寫入檔案前依 MCP schema 驗證"
  - "persist:false 時不再寫入 state.json 與 bootstrap secret，先前回應宣稱關閉但仍寫入"
  - "legacy status fallback 由 byzantine 改為 raft，與 init 預設一致（#4336）"
tags: [ruflo, hive-mind, persistence, mcp-schema, release-notes]
topics: [agents.frameworks, agents.mcp, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.4 — hive-mind_init persistence contract fix

讓 hive-mind_init 的實際行為符合它所宣告的持久化設定。

**Why** 先前 persist:false 的回應聲稱已關閉持久化，但 state.json 與 bootstrap secret 仍會被寫入，回應與實際行為不一致。

**How** maxAgents、memoryBackend、persist 在任何檔案寫入前先依 MCP schema 驗證；persist:false 時兩個檔案都不寫。

**What** Ruflo v3.59.4（#4336），legacy status fallback 由 byzantine 改為 raft，與 init 的預設值一致；三個 dist-tags 已在 registry 驗證。

### 重點
- maxAgents、memoryBackend、persist 在寫入檔案前依 MCP schema 驗證
- persist:false 時不再寫入 state.json 與 bootstrap secret，先前回應宣稱關閉但仍寫入
- legacy status fallback 由 byzantine 改為 raft，與 init 預設一致（#4336）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 hive-mind_init now honors its own advertised persistence contract ( #4336 ). maxAgents , 
 memoryBackend , and persist are declared in the MCP schema and validated before any 
filesystem write. persist:false now genuinely writes neither state.json nor the bootstrap 
secret — previously the response claimed persistence was off while both files were still 
written. The legacy status fallback was also corrected from byzantine to raft , matching 
init's documented default. 
 
 Published 
 
 @claude-flow/cli@3.59.4 , claude-flow@3.59.4 , ruflo@3.59.4 — latest / alpha / v3alpha 
dist-tags all verified matching on the live registry.

</details>