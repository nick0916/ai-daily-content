---
id: inbox_75fcf057
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2348-claude-mem-releases-v15-12-1-f33d]]"
title: "v15.12.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.12.1
source: claude-mem-releases
published_at: 2026-11-08T22:09:47+00:00
fetched_at: 2026-11-08T23:55:35.181701+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 macOS 12 下無法存檔與 CMEM Pro 登入失敗兩個關鍵問題。 **What** 在 macOS 12（系統 SQLite 3.37）上，observations 每次寫入都出現「SQL logic error」，現改用 .all() 讀取 RETURNING 語句後恢復存檔；CMEM Pro 自 15.11.0 起登入卡在「Could not start OAuth login」，安裝程式現在接受 cmem.ai 回傳的 setup id。另含 Cursor hooks.json 原子寫入與 worker 安全性等修正。"
key_points:
  - "macOS 12（SQLite 3.37）下 observations 寫入失敗「SQL logic error」，改用 .all() 讀取 RETURNING 語句後恢復（#5499）"
  - "CMEM Pro 自 15.11.0 起登入卡在「Could not start OAuth login」，安裝程式改為接受 setup id（#5502）"
  - "Cursor 安裝程式原子寫入 hooks.json，避免中斷安裝或解除安裝後留下損壞檔案（#5484）"
tags: [claude-mem, release-notes, bug-fix, macos, cursor-hooks]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.12.1

修正 macOS 12 下無法存檔與 CMEM Pro 登入失敗兩個關鍵問題。

**What** 在 macOS 12（系統 SQLite 3.37）上，observations 每次寫入都出現「SQL logic error」，現改用 .all() 讀取 RETURNING 語句後恢復存檔；CMEM Pro 自 15.11.0 起登入卡在「Could not start OAuth login」，安裝程式現在接受 cmem.ai 回傳的 setup id。另含 Cursor hooks.json 原子寫入與 worker 安全性等修正。

### 重點
- macOS 12（SQLite 3.37）下 observations 寫入失敗「SQL logic error」，改用 .all() 讀取 RETURNING 語句後恢復（#5499）
- CMEM Pro 自 15.11.0 起登入卡在「Could not start OAuth login」，安裝程式改為接受 setup id（#5502）
- Cursor 安裝程式原子寫入 hooks.json，避免中斷安裝或解除安裝後留下損壞檔案（#5484）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.12.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Two critical fixes 
 
 macOS 12 (system SQLite 3.37): observations failed to save with "SQL logic error" on every write. Statements that use RETURNING are now read with .all() , so observations store again ( #5499 , thanks @xunguangzlj-cloud ; reported in #5497 by @hamadikante0-ship-it ). 
 CMEM Pro sign-in: since 15.11.0, sign-in stopped at its first step with "Could not start OAuth login". The installer now accepts the setup id that cmem.ai echoes into its sign-in links ( #5502 ; reported in #5493 by @luciano-fiandesio ). 
 
 Other fixes 
 
 Cursor: the installer writes hooks.json atomically, so an interrupted install or uninstall can no longer leave Cursor with a broken hooks file ( #5484 , thanks @DeryFerd ). 
 Worker security: the operator processing route rejects requests from foreign localhost origins ( #5482 , thanks @DeryFerd ). 
 Timeline: a #123 anchor is read as an observation id, not a date ( #5479 , thanks @rudycelekli ). 
 Prompt import: Claude Code transcripts and settings are read from CLAUDE_CONFIG_DIR when it is set ( #5476 , thanks @rudycelekli ). 
 Server: truncating event payloads in the generation prompt keeps emoji and other surrogate pairs whole ( #5478 , thanks @rudycelekli ). 
 Server: the legacy SERVER_BETA key is rotated when the canonical key is blank ( #5477 , thanks @rudycelekli ). 
 OpenClaw: /claude-mem-search 4019 searches for the number instead of reading it as a result limit ( #5474 , thanks @rudycelekli ). 
 OpenClaw: worker session posts are stamped with platform source openclaw ( #5475 , thanks @rudycelekli ). 
 
 Also in this release 
 
 CI: superseded runs are cancelled, and the 5-OS image matrix runs only for image changes ( #5481 ). 
 Tests: orphan-process snapshots skip unrelated system processes on Windows ( #5501 , thanks @liuyinchu ). 
 
 Full changelog: v15.12.0...v15.12.1

</details>