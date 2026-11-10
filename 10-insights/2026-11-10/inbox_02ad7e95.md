---
id: inbox_02ad7e95
date: 2026-11-10
source_ref: "[[00-inbox/.../inbox_02ad7e95]]"
title: "v15.15.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.15.0
source: claude-mem-releases
published_at: 2026-11-10T02:20:40+00:00
fetched_at: 2026-11-10T23:36:56.558881+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 修復 worker 在處理第一張圖片時永久凍結的問題。 **Why** 無 node_modules 的 plugin 環境中，Bun 自動安裝載入的 sharp wasm 版，其首次呼叫會阻塞主執行緒，使 timer 與 /api/health 停止回應。 **How** 所有 spawn 改用 bun --no-install；安裝程式從 plugin cache 啟動 worker；media converter 遇到 wasm 版 sharp 時拒絕解碼並回報 decoder_unavailable。 **What** v15.15.0（2026-11-10）另新增單行 Rules + Tools 標頭，指向 ~/.claude-mem/RULES-AND-TOOLS.md，並移除 CLAUDE_MEM_CONTEXT_SHOW_SAVINGS_AMOUNT 與 _PERCENT 節省量設定。"
key_points:
  - "Bun 自動安裝載入 sharp wasm，其首次呼叫阻塞主執行緒，導致 worker 與 /api/health 停止回應"
  - "修正：所有 spawn 加上 bun --no-install；media converter 拒絕 wasm 版 sharp 並回報 decoder_unavailable"
  - "SessionStart 標頭改為單行指向 RULES-AND-TOOLS.md；移除 savings 相關設定與 viewer 開關"
tags: [bun, wasm, sharp, worker-freeze, claude-mem]
topics: [engineering.architecture, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.15.0

claude-mem 修復 worker 在處理第一張圖片時永久凍結的問題。

**Why** 無 node_modules 的 plugin 環境中，Bun 自動安裝載入的 sharp wasm 版，其首次呼叫會阻塞主執行緒，使 timer 與 /api/health 停止回應。

**How** 所有 spawn 改用 bun --no-install；安裝程式從 plugin cache 啟動 worker；media converter 遇到 wasm 版 sharp 時拒絕解碼並回報 decoder_unavailable。

**What** v15.15.0（2026-11-10）另新增單行 Rules + Tools 標頭，指向 ~/.claude-mem/RULES-AND-TOOLS.md，並移除 CLAUDE_MEM_CONTEXT_SHOW_SAVINGS_AMOUNT 與 _PERCENT 節省量設定。

### 重點
- Bun 自動安裝載入 sharp wasm，其首次呼叫阻塞主執行緒，導致 worker 與 /api/health 停止回應
- 修正：所有 spawn 加上 bun --no-install；media converter 拒絕 wasm 版 sharp 並回報 decoder_unavailable
- SessionStart 標頭改為單行指向 RULES-AND-TOOLS.md；移除 savings 相關設定與 viewer 開關

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.15.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v15.15.0

Critical fix 
 
 The worker no longer freezes on its first image ( #5601 ): a worker started from a plugin root with no node_modules (the Claude Code marketplace clone) could freeze for good. Bun's auto-install loaded sharp's wasm build, whose first call blocks Bun's main thread, so timers and /api/health stopped and hooks kept reclaiming the worker. Now every worker, server and plugin spawn runs bun --no-install , the installer starts the worker from the plugin cache copy where it just ran bun install , and the media converter refuses sharp's wasm build before decoding, so a worker started some other way reports decoder_unavailable instead of freezing ( #5653 ). Thanks to @vieGPT for the report and to @Kirat0201 for reproducing it and proposing the approach. 
 
 New 
 
 One Rules + Tools line at session start: the SessionStart header (project and time, Mode, Legend, Format, Fetch, Stats) is now one line, Access Claude-Mem Rules + Tools: ~/.claude-mem/RULES-AND-TOOLS.md . That file holds the format, legend, mode, how to fetch details, the work-state rule and memory-use guidance, and is rewritten only when its text changes. The terminal banner now ends on a closing line with the viewer link and how many timeline lines are shown ( #5654 ). 
 Savings settings removed: the context header no longer prints a savings line, so CLAUDE_MEM_CONTEXT_SHOW_SAVINGS_AMOUNT and CLAUDE_MEM_CONTEXT_SHOW_SAVINGS_PERCENT and their viewer toggle are gone. Settings files that still carry them load as before ( #5654 ). 
 
 Fixes 
 
 Installer: the setup state is prepared before the browser opens, so a quick first choice is no longer erased and the installer no longer waits for a choice you already made ( #5631 , thanks @Afloat16 ). 
 Context: the prior-session reply shown at startup is read from the end of the transcript instead of loading the whole file, so long sessions start faster and very large transcripts keep that context ( #5625 , thanks @Afloat16 ). 
 Terminal banner: when the banner cut lands exactly on a line boundary, the whole line that fits is kept, and the line count also counts rows in the plain block format ( #5654 ). 
 Tests: the server's semantic context route probes the embedding model only where pgvector exists, so CI no longer times out on a cold model download ( #5659 ). 
 
 Full changelog: v15.14.0...v15.15.0

</details>