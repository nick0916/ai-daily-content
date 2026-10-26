---
id: inbox_d2d8423b
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-ruflo-releases-v3-59-15-agntcy-musl-pin-fix-encryption-7874]]"
title: "v3.59.15 — AGNTCY musl-pin fix, encryption/daemon-config error-message fixes, terminal_history total"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.15
source: ruflo-releases
published_at: 2026-10-22T08:05:19+00:00
fetched_at: 2026-10-23T01:01:19.148341+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 RuFlo 的安裝相容性、加密錯誤訊息、daemon 設定讀取與 terminal_history 計數問題。 **Why** @agntcy/slim-bindings 2.0.0-alpha.5 的 optionalDependencies 宣告了從未發布的 linux-arm64-musl 平台套件；寬鬆解析器會忽略此問題，但嚴格解析器（mise 的 aube 後端）會讓整個安裝失敗。 **How** 把 @agntcy/slim-bindings 固定在 2.1.1，這是所有平台 optional 套件都實際存在的最早版本；另修正加密儲存的錯誤訊息、config_set values envelope 的讀取，以及 terminal_history 的 total 計算。 **What** 對應 PR #4371、#4377、#3212、#4378、#3192、#4379、#4380；terminal_history 的 total 原本只回報分頁大小，原文將此列為「total 在分頁切片後計算」bug 類別的第 6 次出現，6 個測試檔共 133/133 通過。"
key_points:
  - "@agntcy/slim-bindings 固定到 2.1.1（#4371、#4377），因 2.0.0-alpha.5 宣告的 linux-arm64-musl 套件從未發布，嚴格解析器會令安裝失敗"
  - "config_set 的 values envelope 現在被正確讀取，daemon.idleSecs 0 能實際生效（#3192、#4379）"
  - "terminal_history 的 total 改為計算所有儲存項目，不再只是分頁大小（#4380）"
tags: [npm-optional-dependencies, dependency-pinning, pagination-bug, encryption-at-rest, daemon-config]
topics: [engineering.architecture, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.15 — AGNTCY musl-pin fix, encryption/daemon-config error-message fixes, terminal_history total

修正 RuFlo 的安裝相容性、加密錯誤訊息、daemon 設定讀取與 terminal_history 計數問題。

**Why** @agntcy/slim-bindings 2.0.0-alpha.5 的 optionalDependencies 宣告了從未發布的 linux-arm64-musl 平台套件；寬鬆解析器會忽略此問題，但嚴格解析器（mise 的 aube 後端）會讓整個安裝失敗。

**How** 把 @agntcy/slim-bindings 固定在 2.1.1，這是所有平台 optional 套件都實際存在的最早版本；另修正加密儲存的錯誤訊息、config_set values envelope 的讀取，以及 terminal_history 的 total 計算。

**What** 對應 PR #4371、#4377、#3212、#4378、#3192、#4379、#4380；terminal_history 的 total 原本只回報分頁大小，原文將此列為「total 在分頁切片後計算」bug 類別的第 6 次出現，6 個測試檔共 133/133 通過。

### 重點
- @agntcy/slim-bindings 固定到 2.1.1（#4371、#4377），因 2.0.0-alpha.5 宣告的 linux-arm64-musl 套件從未發布，嚴格解析器會令安裝失敗
- config_set 的 values envelope 現在被正確讀取，daemon.idleSecs 0 能實際生效（#3192、#4379）
- terminal_history 的 total 改為計算所有儲存項目，不再只是分頁大小（#4380）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.15)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 
 fix(cli): pin @agntcy/slim-bindings to 2.1.1 ( #4371 , #4377 ) — 2.0.0-alpha.5 's own optionalDependencies claimed a linux-arm64-musl platform package that was never published upstream (confirmed true of every 2.0.0-alpha.* / 2.0.0 / 2.1.0 release). npm silently tolerated this; strict resolvers ( mise 's aube backend) failed the whole install. 2.1.1 is the earliest release where every platform's optional package actually exists. 
 fix(cli): report actual flag state when decrypting an encrypted store without a key ( #3212 , #4378 ) — the decrypt-path error message now reports the real CLAUDE_FLOW_ENCRYPT_AT_REST value and the on-disk RFE1-encrypted state, instead of always claiming the enable flag is set. 
 fix(daemon): read config_set 's values envelope in the config.json reader ( #3192 , #4379 ) — each config key now resolves independently through scopes.project -&gt; values -&gt; root , so a default-scope config_set daemon.idleSecs 0 call actually takes effect on the running daemon. 
 fix(mcp): report every stored entry in terminal_history 's total ( #4380 ) — the combined (no sessionId ) history view now reports the real count instead of just the returned page size. 6th instance of the "total computed after pagination slice" bug class. 
 
 Verification 
 
 audit-umbrella-version-lockstep.mjs , leaf-drift check, audit-leaf-versions-published.mjs : all clean. 
 mcp-memory-explicit-dbpath-3196.test.ts , workflow-list-total.test.ts , encryption-vault.test.ts , worker-daemon-resource-thresholds.test.ts , terminal-history-total.test.ts , agntcy-commands.test.ts : 133/133 passing against the built package. 
 All four source PRs went fully green independently before merge; the release PR itself needed one legitimate retry on Supply-chain audit after a transient npm-registry outage on the bulk security-advisories endpoint (confirmed external — main 's own CI hit the identical failure at the identical time). 
 
 🤖 Generated with RuFlo

</details>