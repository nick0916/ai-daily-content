---
id: inbox_af3076b1
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-ruflo-releases-v3-59-0-real-agentdb-hnsw-search-grok-bu-2e35]]"
title: "v3.59.0 — Real AgentDB HNSW search, Grok Build host, npm README image fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.0
source: ruflo-releases
published_at: 2026-10-20T14:31:12+00:00
fetched_at: 2026-10-21T00:12:51.012433+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 Ruflo 的 AgentDB 向量搜尋，改為直接接上真實的 agentdb.HNSWIndex，原本的路徑長期失敗卻被靜默吞掉。 **Why** getController('hnsw') 路徑在真實 agentdb 套件上必定拋錯，而每次搜尋都被靜默 catch，因此一直沒有被發現。 **How** AgentDBBackend 直接串接 agentdb.HNSWIndex，加上 staleness 拒絕與寫入後的安全重建；遇到原生能力失敗、缺依賴、維度不符或過濾查詢時退回精確 cosine 搜尋。 **What** 同版本另加入 RaBitQ 索引自動建置、Grok Build CLI 作為與 Claude Code、Codex 並列的 init host，以及 memory list/search 的 tag 過濾；三個 CLI 套件發布為 3.59.0，另獨立發布 @claude-flow/memory@3.0.8。"
key_points:
  - "AgentDBBackend 改接 agentdb.HNSWIndex，搜尋失敗時退回精確 cosine（#4249 / #4322）"
  - "RaBitQ 索引改為按需自動建置，失敗時安全退回精確搜尋（#4318 / #4319）"
  - "修正 npm README 圖片破損：移除 ruflo/package.json 中多餘的 repository.directory 欄位"
tags: [agentdb, hnsw, vector-search, silent-failure, grok-build, npm-release]
topics: [engineering.rag, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.0 — Real AgentDB HNSW search, Grok Build host, npm README image fix

修正 Ruflo 的 AgentDB 向量搜尋，改為直接接上真實的 agentdb.HNSWIndex，原本的路徑長期失敗卻被靜默吞掉。 **Why** getController('hnsw') 路徑在真實 agentdb 套件上必定拋錯，而每次搜尋都被靜默 catch，因此一直沒有被發現。 **How** AgentDBBackend 直接串接 agentdb.HNSWIndex，加上 staleness 拒絕與寫入後的安全重建；遇到原生能力失敗、缺依賴、維度不符或過濾查詢時退回精確 cosine 搜尋。 **What** 同版本另加入 RaBitQ 索引自動建置、Grok Build CLI 作為與 Claude Code、Codex 並列的 init host，以及 memory list/search 的 tag 過濾；三個 CLI 套件發布為 3.59.0，另獨立發布 @claude-flow/memory@3.0.8。

### 重點
- AgentDBBackend 改接 agentdb.HNSWIndex，搜尋失敗時退回精確 cosine（#4249 / #4322）
- RaBitQ 索引改為按需自動建置，失敗時安全退回精確搜尋（#4318 / #4319）
- 修正 npm README 圖片破損：移除 ruflo/package.json 中多餘的 repository.directory 欄位

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 
 Real AgentDB HNSW vector search ( #4249 / #4322 ): AgentDBBackend now wires the separately-exported agentdb.HNSWIndex directly, replacing the dead getController('hnsw') path that always threw against the real agentdb package and was silently caught on every search. Native search now has correct staleness rejection, safe rebuilds after writes, and exact-cosine fallback on any native-capability failure, missing dependency, dimension mismatch, or filtered query. Follow-up ( #4319 ) added test coverage for the WASM-missing disable path and concurrent index builds. 
 RaBitQ index now builds automatically ( #4318 / #4319 ): previously required a manual build step; now builds on demand with safe fallback to exact search. 
 New: Grok Build CLI host ( #3512 ): init now supports Grok Build as a first-class agent host alongside Claude Code and Codex. 
 New: memory tag filtering ( #3526 ): memory list / memory search gained a tag filter, explicit-provider precedence, and an Ollama default model. 
 
 Fixes 
 
 Memory delete-sync: AutoMemoryBridge.importFromAutoMemory() now removes entries whose source file/heading was deleted, instead of being additive-only ( #4138 ). 
 Swarm idle-agent heartbeat false positive: healthy idle agents (no in-flight work) were being marked error and dropped from getAvailableAgents() after 3 missed heartbeat intervals, even though they have no heartbeat producer to begin with ( #4320 ). 
 Ephemeral-agent termination idempotency: FederationHub.terminateAgent() / completeAgent() could double-count the same agent's completion/failure on a repeated call (shutdown, unregisterSwarm , TTL cleanup, or a retried request) ( #4323 ). 
 status tasks always printed "No tasks": it sent status: 'all' as a literal filter (matching nothing) and read the wrong field names from task_list 's response ( #4321 ). 
 task_list 's total count was computed after applying limit , so it always equaled the page size instead of the real match count ( #4324 ). 
 metaharness similarity 's cost dimension was inert below $0.999 (an algebraic no-op collapsed the whole realistic cost range to 0), and the minor-drift verdict threshold had two disagreeing encodings ( #3520 ). 
 ruflo-harness now reports the live process instead of just the install ( #3521 ). 
 
 Documentation 
 
 Fixed the actual cause of broken images/links on npmjs.com/package/ruflo: a stray repository.directory: "ruflo" field in ruflo/package.json was adding an extra path layer on top of the README content (which is the repo-root README, copied in verbatim at publish time with repo-root-relative paths already). Removed the field to match claude-flow 's own repository entry. 
 
 Published 
 
 @claude-flow/cli@3.59.0 , claude-flow@3.59.0 , ruflo@3.59.0 — latest / alpha / v3alpha dist-tags all verified on the live registry. 
 @claude-flow/memory@3.0.8 (standalone, the #4249 fix — not bundled into the 3-package train).

</details>