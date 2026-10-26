---
id: inbox_b5d96d66
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-12-restored-pair-command-082e]]"
title: "v3.59.12 — restored pair command"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.12
source: ruflo-releases
published_at: 2026-10-21T20:50:18+00:00
fetched_at: 2026-10-21T23:46:35.268844+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Ruflo 的 pair 指令回來，修好依賴它的 pair-programming skill。 **Why** v3 CLI 重寫時整個移除了 pair 指令，使用該 skill 的專案會出現 Unknown command 錯誤。 **How** 恢復為非互動式指令，session 狀態以原子寫入存於 .claude-flow/sessions/pair/current.json。 **What** 支援 start、status、switch、mode、end、history 子命令，並保留 v2 的 --start、--status、--end、--history 頂層旗標別名；另修正一個依賴 umask 的測試（#4365）。"
key_points:
  - "pair 指令恢復為非互動式，session 狀態存於 .claude-flow/sessions/pair/current.json 並以原子寫入保存"
  - "支援 start、status、switch、mode、end、history 子命令，並相容 v2 的 --start、--status、--end、--history 旗標"
  - "pair-command.test.ts 18/18 通過；修正測試未強制檔案權限而受 umask 影響的問題（#4365）"
tags: [ruflo, claude-code, cli, pair-programming, backward-compatibility]
topics: [agents.coding_agents, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.12 — restored pair command

讓 Ruflo 的 pair 指令回來，修好依賴它的 pair-programming skill。

**Why** v3 CLI 重寫時整個移除了 pair 指令，使用該 skill 的專案會出現 Unknown command 錯誤。

**How** 恢復為非互動式指令，session 狀態以原子寫入存於 .claude-flow/sessions/pair/current.json。

**What** 支援 start、status、switch、mode、end、history 子命令，並保留 v2 的 --start、--status、--end、--history 頂層旗標別名；另修正一個依賴 umask 的測試（#4365）。

### 重點
- pair 指令恢復為非互動式，session 狀態存於 .claude-flow/sessions/pair/current.json 並以原子寫入保存
- 支援 start、status、switch、mode、end、history 子命令，並相容 v2 的 --start、--status、--end、--history 旗標
- pair-command.test.ts 18/18 通過；修正測試未強制檔案權限而受 umask 影響的問題（#4365）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.12)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 
 Restored the pair command that the bundled pair-programming Claude Code skill depends on ( #3341 ). The v3 CLI rewrite had dropped it entirely, so any project using that skill hit [ERROR] Unknown command: pair . The restored command is non-interactive: session state lives in .claude-flow/sessions/pair/current.json , written atomically. Subcommands: start , status , switch , mode , end , history , plus legacy v2 top-level flag aliases ( --start , --status , --end , --history ). 
 Fixed a host-dependent test ( plugins/ruflo-console/tests/write-argv.spec.ts ) that asserted a file's mode without forcing it past the process umask ( #4365 ) — found while independently verifying an unrelated draft PR. 
 
 Verification 
 
 pair-command.test.ts : 18/18 passing, run directly against the built package. 
 audit-umbrella-version-lockstep.mjs and audit-leaf-versions-published.mjs : both clean. 
 Full CI green on the release PR ( #4367 ): one job ( eject-dryrun ) hit a transient run cancellation, confirmed via conclusion: "cancelled" on the job, and passed clean on rerun. 
 
 🤖 Generated with RuFlo

</details>