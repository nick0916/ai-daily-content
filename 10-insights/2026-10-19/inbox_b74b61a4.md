---
id: inbox_b74b61a4
date: 2026-10-19
source_ref: "[[00-inbox/2026-10-19/0206-ruflo-releases-v3-57-2-graph-backup-ttl-correctness-fix-43f8]]"
title: "v3.57.2 — graph/backup/ttl correctness fixes + large community PR batch"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.57.2
source: ruflo-releases
published_at: 2026-10-19T23:44:17+00:00
fetched_at: 2026-10-20T02:13:25.145003+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 Ruflo CLI 多項正確性錯誤，包括備份假成功與索引孤兒問題。 **Why** 這些錯誤會讓使用者誤以為操作成功，或讀到錯誤的資料庫，例如備份失敗仍回報成功、ttl: 0 的資料不過期。 **How** 備份只在已確認加密且無 WAL 的來源才 fallback，並記錄實際完成的方法；ReasoningBank.consolidate() 補上 hnswIndex.removePoint(id)；memory export/import 改為回傳真實錯誤或遷移筆數。 **What** 版本 3.57.2（@claude-flow/cli、claude-flow、ruflo），cli-core 3.7.5 獨立發布並鎖定版本，另含大量社群 PR 修正。"
key_points:
  - "backupMemoryDb() 原先在任何原生備份失敗（含 SQLITE_BUSY）後都做原始檔案複製，且無論結果都回報 backedUp: true；現改為只在加密且無 WAL 的來源才 fallback"
  - "JsonMemoryBackend.isExpired() 用 falsy 檢查 ttlSeconds，導致明確設定 ttl: 0 的資料永不過期；cli-core 3.7.5 已修正"
  - "ReasoningBank.consolidate() 刪除 pattern 時未呼叫 hnswIndex.removePoint(id)，HNSW 索引累積孤兒，直到 storePattern() 永久報錯"
tags: [ruflo, claude-flow, memory-backend, error-handling, patch-release]
topics: [agents.frameworks, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.57.2 — graph/backup/ttl correctness fixes + large community PR batch

修正 Ruflo CLI 多項正確性錯誤，包括備份假成功與索引孤兒問題。

**Why** 這些錯誤會讓使用者誤以為操作成功，或讀到錯誤的資料庫，例如備份失敗仍回報成功、ttl: 0 的資料不過期。

**How** 備份只在已確認加密且無 WAL 的來源才 fallback，並記錄實際完成的方法；ReasoningBank.consolidate() 補上 hnswIndex.removePoint(id)；memory export/import 改為回傳真實錯誤或遷移筆數。

**What** 版本 3.57.2（@claude-flow/cli、claude-flow、ruflo），cli-core 3.7.5 獨立發布並鎖定版本，另含大量社群 PR 修正。

### 重點
- backupMemoryDb() 原先在任何原生備份失敗（含 SQLITE_BUSY）後都做原始檔案複製，且無論結果都回報 backedUp: true；現改為只在加密且無 WAL 的來源才 fallback
- JsonMemoryBackend.isExpired() 用 falsy 檢查 ttlSeconds，導致明確設定 ttl: 0 的資料永不過期；cli-core 3.7.5 已修正
- ReasoningBank.consolidate() 刪除 pattern 時未呼叫 hnswIndex.removePoint(id)，HNSW 索引累積孤兒，直到 storePattern() 永久報錯

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.57.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.57.2. @claude-flow/cli-core 3.7.5 ( #4295 , #4296 ) published standalone and pinned exactly. A large community PR batch — mostly correctness fixes to error reporting, memory/graph boundary handling, and CLI diagnostics. 
 Fixed 
 
 agentdb_graph-query / agentdb_graph-pathfinder resolved the memory DB path ad hoc instead of through the shared resolveDbPath() priority order, so an explicit CLAUDE_FLOW_DB_PATH binding could silently read a different store than the one selected ( #4291 , #4298 ). 
 backupMemoryDb() fell back to a raw file copy after any native online-backup failure — including ordinary SQLITE_BUSY /disk errors on an unencrypted source — and reported backedUp: true regardless; the fallback is now gated on a confirmed-encrypted source with no active WAL, and the result records which method actually completed ( #4287 , #4297 ). 
 JsonMemoryBackend.isExpired() used a falsy check on ttlSeconds , so an explicit ttl: 0 never expired ( cli-core 3.7.5, #4295 , #4296 ). 
 RvfBackend 's native @ruvector/rvf branch could never succeed (wrong open() call) and silently fell back to the pure-TS path; the dead native branch is removed rather than half-wired ( #4278 , #4279 , #4280 ). 
 ReasoningBank.consolidate() deleted pruned/deduplicated patterns from storage but never called hnswIndex.removePoint(id) , so the HNSW index filled with orphans until storePattern() started throwing permanently ( #4270 , #4271 ). 
 TopologyManager 's queen/coordinator failover never promoted a replacement after death despite failoverEnabled: true , silently falling through to generic mesh-style ranking ( #4285 , #4286 ). 
 memory export , memory import , and memory_migrate reported fabricated success text instead of the tool's real error or migrated count ( #4204 / #4207 , #4194 / #4209 , and the memory-import tool failure fix). 
 hooks worker dispatch printed Status: completed even when no daemon ran anything ( #4196 / #4208 ). 
 hooks_intelligence_attention accepted unimplemented modes instead of rejecting them ( #4193 ). 
 init upgrade now refreshes intelligence.cjs /session companions instead of leaving stale copies behind ( #4198 / #4220 ). 
 SmartRetrieval collapsed multi-result searches down to one ( #4192 ); the ReasoningBank embedder used a hash fallback instead of the real embedder ( #4191 ); @claude-flow/cli 's own package.json wasn't exported for consumers resolving it directly ( #4190 ). 
 ruvocal 's MCP server merge dropped a base server's credentials when the browser echoed the server back without headers ( #4281 ). 
 ruflo-x-gateway now advertises offline_access so OAuth clients can refresh silently instead of re-authenticating on every access-token expiry ( #4256 ). 
 workflow list/status/stop/run now read the actual shape and errors the workflow tools return ( #4268 ); stale task owners are released on terminal states ( #4272 ); unregistering a swarm agent now removes its domain-pool membership ( #4269 ); orphaned atomic-write temp files under the policy lock are reaped ( #3164 / #4273 ); one-shot CLI runs now flush learned patterns before process.exit(0) instead of losing them while stats.json keeps counting ( #4283 / #4284 ). 
 ruflo-console 's mission ledger no longer leaks a mission from one project into every other project's cockpit ( #4254 / #4276 ). 
 Command examples in the user guide that failed when copied are fixed ( #4275 ); a stray npx invocation referencing a nonexistent unscoped package is corrected to @claude-flow/codex ( #4265 ). 
 scripts/build-codex-mod-hooks.mjs now rebuilds the codex-mod bundle the same way on every OS ( #4292 ).

</details>