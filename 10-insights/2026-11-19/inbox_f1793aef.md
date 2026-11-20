---
id: inbox_f1793aef
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0105-claude-mem-releases-v16-0-1-5788]]"
title: "v16.0.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.0.1
source: claude-mem-releases
published_at: 2026-11-19T11:43:39+00:00
fetched_at: 2026-11-20T01:13:59.990661+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v16.0.1 是緊急修補版，主要修復 Windows 上 Codex 登入與 token 刷新失敗。 **Why** 私有 Codex home 的 auth.json 以 hard link 指向真實憑證，而 Codex 會拒絕多 hard link 的憑證檔。 **How** 改為 symlink；只有在 Windows 且無 symlink 權限時才改用私有複本。 **What** 同時修正 quota cooldown 無法解除與 Chroma 慢時搜尋未 fallback 的問題，並新增 Devin cloud sessions 與 Devin Bots 支援。"
key_points:
  - "Codex 拒絕多 hard link 的 auth.json，導致 codex login 與 token refresh 失敗（#6332）"
  - "有效跳過的 probe 也會解除 quota cooldown，避免每 5 分鐘重新探測（#6324）"
  - "Chroma 搜尋共享 20 秒預算，逾時改 fallback 至 SQLite/FTS5（#6327）；backfill 加入暫停比例與 nice 10（#6299）"
tags: [claude-mem, codex, windows, symlink, chroma]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.0.1

claude-mem v16.0.1 是緊急修補版，主要修復 Windows 上 Codex 登入與 token 刷新失敗。

**Why** 私有 Codex home 的 auth.json 以 hard link 指向真實憑證，而 Codex 會拒絕多 hard link 的憑證檔。

**How** 改為 symlink；只有在 Windows 且無 symlink 權限時才改用私有複本。

**What** 同時修正 quota cooldown 無法解除與 Chroma 慢時搜尋未 fallback 的問題，並新增 Devin cloud sessions 與 Devin Bots 支援。

### 重點
- Codex 拒絕多 hard link 的 auth.json，導致 codex login 與 token refresh 失敗（#6332）
- 有效跳過的 probe 也會解除 quota cooldown，避免每 5 分鐘重新探測（#6324）
- Chroma 搜尋共享 20 秒預算，逾時改 fallback 至 SQLite/FTS5（#6327）；backfill 加入暫停比例與 nice 10（#6299）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.0.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 Signing in to Codex works again on Windows while claude-mem runs ( #6332 , thanks @ffe111 , closes #6331 ). The private Codex home that claude-mem's app-server uses got its auth.json through a hard link to your real ~/.codex/auth.json . Codex refuses to replace a credential file with more than one hard link ( persist_failed: atomic credential replacement does not support hard-linked files ), so codex login and token refresh failed for as long as that home existed. The private home now gets a symlink, which Codex follows. Only on Windows, and only when a symlink is not permitted (no Developer Mode or elevation), it gets a private copy instead. Any other error still fails loudly. 
 A probe answered with ends the quota cooldown ( #6324 , thanks @vaibhav375 , closes #6322 ). After a quota hit, the worker probes the provider and clears the cooldown once a probe stores a memory. A probe the provider answered with a valid stores nothing, so the cooldown never cleared and the worker re-probed every 5 minutes for as long as that session only skipped. A valid skip now releases the cooldown too, on both the store path and the early path before the memory session id is known. Observer-health success still needs a real store. 
 
 Fixes 
 
 Search falls back to SQLite instead of failing when Chroma is slow ( #6327 , thanks @REI-330 , closes #6323 ). The MCP client gives a search 30 s, while each Chroma read waited up to 60 s, so a slow query was still running when the caller gave up and the SQLite/FTS5 fallback never ran. A search now shares one 20 s budget across its Chroma reads and falls back when it runs out, without restarting a healthy chroma-mcp. 
 Chroma rebuilds no longer hold a core for hours ( #6299 , thanks @srieteja ). A full backfill now pauses after each row for its write time times CLAUDE_MEM_CHROMA_BACKFILL_PAUSE_RATIO (default 1, 0 turns it off), and chroma-mcp starts under nice ( CLAUDE_MEM_CHROMA_PROCESS_NICE , default 10) outside Windows. Live sync is unchanged. 
 Windows process cleanup reads taskkill correctly ( #6328 , thanks @REI-330 ; #6307 ). A taskkill exit 255 is now judged by whether the named processes are still alive, not by its wording, so a localized message no longer throws during Chroma teardown, and a mixed message no longer reports success while a process still runs. 
 Observer turns stop leaking SQLite statements ( #6306 ). The statements that store an observer turn are cached instead of prepared on every turn, which could pile up until SQLite ran out of memory and rolled back the whole turn. 
 The login notice says when the observer has no Claude Code login it can use ( #6321 , refs #6319 ). Instead of telling you to run /login when the terminal is signed in to another credential profile, the worker logs a warning with the reason and the notice names which login it read and suggests claude setup-token . 
 The legacy claude-mem shell alias is found and removed on install and update ( #6300 , thanks @0xABCD01 ). doctor reports it, status warns when the worker runs outside the resolved plugin root, multiline aliases are left untouched with a warning, and nothing is changed if you cancel the reinstall. 
 /api/health publishes probe state only ( #6309 , thanks @DeryFerd ). It no longer shows the auth method, the Redis queue descriptor, absolute install paths or the last interaction to unauthenticated callers. 
 An unreadable My Work refresh status no longer breaks setup ( #6305 ). A damaged refresh.json reads as no run and gets replaced; the auto-updater still treats it as busy. 
 Local work stays paused when the machine runs out of file descriptors ( #6303 ). The setup check treats EMFILE/ENFILE as "setup still active" and logs one warning per episode. 
 Timeline file labels look the same on every platform ( #6301 , thanks @POWDER-RANGER ). 
 A press anywhere on a My Work focus card opens its area ( #6315 ). The same fix covers the List, Team and By agent rows. 
 
 New 
 
 Devin cloud sessions and Devin Bots ( #6334 ). An organization can install plugin/ as a Devin plugin and get hooks, MCP search and skills in every session. 
 My Work refresh on OpenCode ( #6330 , thanks @REI-330 ). Opt in with CLAUDE_MEM_WORK_VIEW_AGENT=opencode ; nothing changes otherwise. 
 PostgreSQL search finds terms inside CJK, kana and Hangul text ( #6329 , thanks @REI-330 , refs #3982 ). 
 My Work card titles name the task in 5 to 7 words instead of copying the first sentence of the ask ( #6317 ). 
 The image viewer darkens and blurs the page behind it and casts a shadow ( #6313 ). 
 The installer asks for your work email and a message in the terminal before GUI setup ( #6308 ). 
 
 Tests and docs 
 
 Grok Bot and Zed tests pass on Windows ( #6311 , #6312 , thanks @Lupin133 ). 
 Community sweep worktrees install with bun install ( #6325 ).

</details>