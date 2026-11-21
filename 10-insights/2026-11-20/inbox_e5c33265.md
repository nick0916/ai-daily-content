---
id: inbox_e5c33265
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0048-claude-mem-releases-v16-0-2-44b0]]"
title: "v16.0.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.0.2
source: claude-mem-releases
published_at: 2026-11-20T18:53:48+00:00
fetched_at: 2026-11-21T00:55:33.990554+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正自動更新誤刪執行中 Claude Code 外掛版本的問題，並新增 Codex 作為 observer 配額備援。 **Why** 清理舊版快取時，macOS 與 BSD 上啟動時間的微小差異被誤判為 PID 重用，導致執行中的 session 所有 hook 失效。 **How** 啟動時間不符但該 PID 仍是 Claude Code 時，不再刪除版本資料夾；每次清理也會記錄移除原因與被拒絕的 .in_use 紀錄。 **What** v16.0.2 另修正 Team 與 Enterprise 帳號的啟動卡片、OpenCode 2.x 連線偵測、Chroma 刪除重建、CLAUDE.md 路徑解析等項目，並新增 Codex CLI 作為配額守門時的 fallback 與 WorldRouter preset。"
key_points:
  - "自動更新不再刪除執行中 Claude Code session 所載入的外掛版本（#6352，closes #6349）"
  - "每次快取清理都會為每個被移除的版本寫入 log，註明原因（orphaned 或 superseded）與被拒絕的 .in_use 紀錄（process exited 或 start-time mismatch）"
  - "新增 Codex 作為 Claude 配額守門時的 observer fallback，透過已以 ChatGPT 登入的本地 Codex CLI 運作（#6326）"
tags: [claude-mem, plugin-cache, auto-update, codex, observer]
topics: [agents.coding_agents, product_and_org.product]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.0.2

修正自動更新誤刪執行中 Claude Code 外掛版本的問題，並新增 Codex 作為 observer 配額備援。

**Why** 清理舊版快取時，macOS 與 BSD 上啟動時間的微小差異被誤判為 PID 重用，導致執行中的 session 所有 hook 失效。

**How** 啟動時間不符但該 PID 仍是 Claude Code 時，不再刪除版本資料夾；每次清理也會記錄移除原因與被拒絕的 .in_use 紀錄。

**What** v16.0.2 另修正 Team 與 Enterprise 帳號的啟動卡片、OpenCode 2.x 連線偵測、Chroma 刪除重建、CLAUDE.md 路徑解析等項目，並新增 Codex CLI 作為配額守門時的 fallback 與 WorldRouter preset。

### 重點
- 自動更新不再刪除執行中 Claude Code session 所載入的外掛版本（#6352，closes #6349）
- 每次快取清理都會為每個被移除的版本寫入 log，註明原因（orphaned 或 superseded）與被拒絕的 .in_use 紀錄（process exited 或 start-time mismatch）
- 新增 Codex 作為 Claude 配額守門時的 observer fallback，透過已以 ChatGPT 登入的本地 Codex CLI 運作（#6326）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.0.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fix 
 
 An auto-update no longer deletes the plugin version a running Claude Code session was loaded from ( #6352 , thanks @0xABCD01 , closes #6349 reported by @justindrp ). The cache sweep keeps a version folder while the Claude Code process recorded in its .in_use file is alive. On macOS and BSD, a few seconds of difference between the start time Claude Code recorded and the one ps reports was read as PID reuse, so the sweep deleted the folder from under a live session and every hook failed for the rest of that session. A start-time mismatch no longer removes the folder while the process at that PID is still Claude Code. A PID that now belongs to another program is still pruned as before. 
 Every cache prune now logs why and who. The worker writes one log line per removed version with its reason (orphaned or superseded) and the .in_use records it rejected and why (process exited or start-time mismatch), so any removal can be traced from the log alone. 
 
 Fixes 
 
 The session-start card is drawn on Team and Enterprise accounts ( #6353 , thanks @KeithMoc , closes #6314 reported by @TimoWestland ). When an organization plugin runs first and the card's usual hooks never fire, the card now asks for itself from the session.start hook and the context hook answers it. 
 My Work detects OpenCode 2.x connections ( #6340 , thanks @ZedingZhang , closes #6339 reported by @Realauster ). The login probe reads OpenCode's JSON output, so a connected provider is no longer reported as logged out on OpenCode 2.3.2. 
 My Work refresh prefers MXC for isolated Codex launches on Windows ( #6348 , thanks @QuantScorpus , refs #5163 ). The refresh no longer picks the unelevated sandbox and fails before the agent starts. 
 Both host-observer probes give a slow observer the same 1 s ( #6359 , thanks @rtmalikian , closes #6358 ). The async probe used 400 ms and the install-time probe 1 s, so one called a valid observer "occupied" and the other did not. 
 Chroma collection deletes that lose their reply are checked before a rebuild ( #6338 , thanks @POWDER-RANGER ). The worker lists collections once instead of replaying the delete, and only rebuilds once the delete is confirmed. 
 chroma-mcp restarts after a cancelled read once in-flight writes settle ( #6337 , thanks @MaxWang007 ). The next call no longer goes to a server that can no longer read its input. 
 Worker errors and unknown paths answer in JSON ( #6341 , thanks @DeryFerd ). The worker now installs its 404 and error handlers, so it no longer returns Express's HTML error page with local file paths in the stack trace. 
 CLAUDE.md placement resolves absolute paths before the project check ( #6336 , thanks @LeviReisJs ). Forward-slash paths on Windows are no longer dropped, and paths that climb out of the project with .. are refused. 
 npx claude-mem doctor reads the worker's doctor endpoint once ( #6344 , thanks @DeryFerd ), so a slow worker costs one timeout instead of two. 
 The Agent Cost Report skill uses a spec-compliant name ( #6356 , thanks @LuckVd , refs #6355 ), so agents that check skill names load it. 
 
 New 
 
 Codex as an observer quota fallback ( #6326 , thanks @QuantScorpus ). When Claude hits its quota guard, the observer can use the local Codex CLI signed in with ChatGPT and return to Claude through the existing recovery path. 
 WorldRouter preset for the OpenAI-compatible provider ( #6357 , thanks @Opgeek-1 ). 
 The startup card shows the Claude-Mem mark in a right column when the terminal is wide enough ( #6333 ). 
 
 Tests, CI and docs 
 
 A DNS-rebinding test pins the worker's Host guard ahead of CORS ( #6345 , thanks @DeryFerd ). 
 The Windows build runs the postinstall allowlist guard ( #6343 , thanks @DeryFerd ). 
 Devin cloud needs one org secret to connect CMEM Pro ( #6335 ). 
 The Docker pinning example says to build from the repository root ( #6346 , thanks @DeryFerd ). 
 
 Full changelog : v16.0.1...v16.0.2

</details>