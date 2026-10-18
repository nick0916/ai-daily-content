---
id: inbox_ce1daea1
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-ruflo-releases-v3-57-0-community-pr-batch-policy-ledger-7462]]"
title: "v3.57.0 — community PR batch + policy-ledger integrity fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.57.0
source: ruflo-releases
published_at: 2026-10-17T22:38:55+00:00
fetched_at: 2026-10-18T03:19:47.138596+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo（ruvnet/ruflo；套件 @claude-flow/cli、claude-flow、ruflo）於 2026-10-17 發布 3.57.0 minor 版本，含社群 PR 批次（#4210–#4252）與 policy-ledger 完整性修正（#3892）。安全面有三項：ruflo init / init --dual / @claude-flow/codex init 預設不再寫入寬鬆的 .codex/config.toml，改為 sandbox_mode=\"workspace-write\"、approval_policy=\"on-request\"、web_search=\"cached\"，舊的 danger-full-access / never / live 需明確加 --codex-trust full（或 RUFLO_CODEX_TRUST=full），且既有檔案即使 --force 也不會被覆寫；loopback 上的 MCP bridge 在未設 MCP_AUTH_TOKEN 時，現在要求 Host 為 loopback（防 DNS rebinding）且 Origin 為 loopback 或在允許清單，避免任意網頁呼叫 tool-call；policy ledger 改以獨立的磁碟 archive anchor 驗證已修剪的 ledger，而非只信任可變的 state.json，修復已 prune 安裝上的 policy-ledger-verification-failed。新增 ruflo doctor 偵測 Node 24.19–24.21 上以 24.19+ headers 編譯的 better-sqlite3 可能 abort（nodejs/node#65446），以及版本化 JSON 健康檢查輸出。修正涵蓋 swarm（取消、per-recipient ack、緊急訊息在佇列溢出時保留、worker slot 釋放）、跨程序序列化 learning stats 寫入、Stop hook 佔用去重 key 導致後續 hook 不執行、daemon status 顯示實際 TTL 等。#4220 因需動到簽章 helper manifest、須用私鑰重簽而延到後續版本。使用 Ruflo 搭配 Codex 或 MCP 的團隊建議盡快升級。"
key_points:
  - "init 預設改為 workspace-write / on-request / web_search=cached，要放寬需 --codex-trust full 或 RUFLO_CODEX_TRUST=full；既有 .codex/config.toml 即使 --force 也不覆寫"
  - "本機 MCP bridge 無 MCP_AUTH_TOKEN 時要求 Host 為 loopback（擋 DNS rebinding）且 Origin 為 loopback 或在允許清單（#4226、#4243）"
  - "policy ledger 改以獨立 on-disk archive anchor 驗證已 prune 的 ledger，修復 policy-ledger-verification-failed（#3892、#4216）"
tags: [ruflo, claude-flow, mcp-security, dns-rebinding, codex-config, swarm]
topics: [security, agents.mcp, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.57.0 — community PR batch + policy-ledger integrity fix

Ruflo（ruvnet/ruflo；套件 @claude-flow/cli、claude-flow、ruflo）於 2026-10-17 發布 3.57.0 minor 版本，含社群 PR 批次（#4210–#4252）與 policy-ledger 完整性修正（#3892）。安全面有三項：ruflo init / init --dual / @claude-flow/codex init 預設不再寫入寬鬆的 .codex/config.toml，改為 sandbox_mode="workspace-write"、approval_policy="on-request"、web_search="cached"，舊的 danger-full-access / never / live 需明確加 --codex-trust full（或 RUFLO_CODEX_TRUST=full），且既有檔案即使 --force 也不會被覆寫；loopback 上的 MCP bridge 在未設 MCP_AUTH_TOKEN 時，現在要求 Host 為 loopback（防 DNS rebinding）且 Origin 為 loopback 或在允許清單，避免任意網頁呼叫 tool-call；policy ledger 改以獨立的磁碟 archive anchor 驗證已修剪的 ledger，而非只信任可變的 state.json，修復已 prune 安裝上的 policy-ledger-verification-failed。新增 ruflo doctor 偵測 Node 24.19–24.21 上以 24.19+ headers 編譯的 better-sqlite3 可能 abort（nodejs/node#65446），以及版本化 JSON 健康檢查輸出。修正涵蓋 swarm（取消、per-recipient ack、緊急訊息在佇列溢出時保留、worker slot 釋放）、跨程序序列化 learning stats 寫入、Stop hook 佔用去重 key 導致後續 hook 不執行、daemon status 顯示實際 TTL 等。#4220 因需動到簽章 helper manifest、須用私鑰重簽而延到後續版本。使用 Ruflo 搭配 Codex 或 MCP 的團隊建議盡快升級。

### 重點
- init 預設改為 workspace-write / on-request / web_search=cached，要放寬需 --codex-trust full 或 RUFLO_CODEX_TRUST=full；既有 .codex/config.toml 即使 --force 也不覆寫
- 本機 MCP bridge 無 MCP_AUTH_TOKEN 時要求 Host 為 loopback（擋 DNS rebinding）且 Origin 為 loopback 或在允許清單（#4226、#4243）
- policy ledger 改以獨立 on-disk archive anchor 驗證已 prune 的 ledger，修復 policy-ledger-verification-failed（#3892、#4216）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.57.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Minor release: @claude-flow/cli , claude-flow , ruflo 3.57.0. A batch of community and dream-cycle fixes ( #4210 - #4252 ) plus a policy-ledger integrity fix ( #3892 ). No standalone leaf republish needed this round. 
 Security 
 
 ruflo init / init --dual / @claude-flow/codex init no longer write a permissive .codex/config.toml by default. The generated file now uses sandbox_mode = "workspace-write" , approval_policy = "on-request" and web_search = "cached" ( standard trust); the old danger-full-access / never / live file needs an explicit --codex-trust full (or RUFLO_CODEX_TRUST=full ). init prints which level was written, an existing .codex/config.toml is never rewritten (not even with --force ), and a kept permissive file is flagged with how to tighten it. Found by the three-host e2e run (ADR-490). @claude-flow/codex 3.0.4 (bundled, ships with the next train). 
 The MCP bridge on loopback no longer accepts tool-call requests from an arbitrary web page: local-only mode now requires the Host to be loopback (blocks DNS rebinding) and the Origin to be loopback-or-allowlisted when no MCP_AUTH_TOKEN is set ( #4226 , #4243 , @kevin9327 ). 
 The policy ledger now authenticates a retained/pruned ledger against its independent on-disk archive anchor instead of trusting the mutable state.json alone, and streams full audits through fenced writers. Fixes policy-ledger-verification-failed on any install whose ledger has already been pruned ( #3892 , #4216 , @proffesor-for-testing ). 
 
 Added 
 
 ruflo doctor reports better-sqlite3 copies compiled against Node 24.19+ headers when running Node 24.19–24.21, where they can abort the process ( Assertion failed: (env) != nullptr , nodejs/node#65446 ), with the documented workarounds. doctor --component native-addon runs it alone ( #4055 , reported by @ronmikailov ). 
 ruflo doctor reports health checks as versioned JSON output ( #4228 , @bryanbans ). 
 
 Fixed 
 
 @metaharness/darwin pin bumped from ~0.10.2 to ~0.12.0 , unblocking the metaharness-pin-drift CI gate repo-wide ( #3219 , #4252 ). 
 Swarm: subscriber delivery is cancelled cleanly at shutdown, acknowledgements are tracked per recipient, urgent messages survive queue overflow, and failed/cancelled task workers release their slot ( #4233 , #4234 , #4235 , #4236 , @rudycelekli ). Coordinator cancellation stays terminal ( #4244 , @rudycelekli ); domain pools stop creating unregistered agents and release agents after terminal tasks ( #4246 , #4247 , @Tong-bit-art ); shared worker reservations are honored across agent pools, fixing a case where that bookkeeping change would have silently defeated the domain-pool-release fix above ( #4245 , @rudycelekli ). 
 Learning stats read-merge-write transactions are serialized across processes, fixing lost concurrent increments ( #4217 , #4240 , @rudycelekli ). 
 Claude memories refresh across project and worktree roots ( #4210 , @rudycelekli ); the secret screen no longer treats a hyphen-named memory key as a credential field ( #4202 , #4211 , @akushonkamen ). 
 Hook lifecycle events are distinguished during deduplication, fixing the Stop hook claiming the session-end de-dup key so later hooks never ran ( #4206 , #4212 , @dajiaohuang ); init omits unimplemented generated hooks ( #4200 , #4213 , @dajiaohuang ) and stops granting blanket execution of project helpers ( #4221 , @xiajiahang ). 
 Intelligence: trajectories are forwarded using the ruvllm contract ( #4222 , @xiajiahang ); neural quantization reports unchanged persisted storage instead of a false delta ( #4224 , @dajiaohuang ). 
 Console: Mission Control's prose wraps at 80 columns ( #3899 , #4225 , console 0.44.3, @korjavin ); the mission ledger is keyed per project instead of leaking one project's active mission into every other ( #4237 , #4242 , @kevin9327 ). 
 daemon status reports the running daemon's actual TTL instead of a stale --ttl 0 default ( #4238 , #4241 , @kevin9327 ). 
 CLI: --no-color is honored for help and version output, and --no-update is honored before the startup update check runs ( #4248 , #4251 , @shuaiyafei ). 
 dream(performance) : RaftConsensus.awaitConsensus() is event-driven instead of busy-polling ( #4214 , #4215 ). 
 Docs: 25 user guide links repaired to v3 packages ( #4223 , @ketpatil77 ); ABP-governed SGit memory checkpoints and Ruflo CLI recovery validation documented ( #4239 , @mondweep ). 
 
 Not included: #4220 (helper-execution-permission fix) touches a signed helper manifest and needs a re-sign with the private key before merge, held for a follow-up release. #4216 's own large diff (ledger integrity) was reviewed in depth separately before merging, given it gates MCP tool-call authorization.

</details>