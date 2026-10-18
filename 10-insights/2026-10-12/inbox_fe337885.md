---
id: inbox_fe337885
date: 2026-10-12
source_ref: "[[00-inbox/.../inbox_fe337885]]"
title: "v13.36.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.36.0
source: claude-mem-releases
published_at: 2026-10-12T18:12:46+00:00
fetched_at: 2026-10-18T03:35:42.226184+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.36.0 是社群主導的發布，幾乎所有自 v13.35.0 以來的變更都來自外部貢獻者。最重要的變更是供應商拒絕時不再丟棄記憶：Anthropic 信用餘額為空、組織封鎖訂閱存取，或本地模型伺服器停止運作時，observer 會暫停並保留工作（@Mola-maker）；observer 串流提前結束時，該批次會退回重新處理（@shantanukhanwalkar）。資料庫安全方面，資料庫會記錄最新寫入的 schema 版本，較舊的 claude-mem 會拒絕開啟已被新版升級的資料庫。其他修正包括：非 ASCII 的 Windows 使用者資料夾名稱（如韓文、日文）現在可找到 Bun 與 Claude；React Native 與 Expo 專案的 tsconfig 不再被誤報為錯誤；搜尋支援中日韓泰文字在句子中比對。新增功能包括 Qoder plugin 支援、CLAUDE_MEM_TOOL_USES_RETENTION_DAYS（選擇性修剪原始工具紀錄，預設保留全部）。另外，專案分支現在只剩 main，core-dev 與 community-edge 已停用。"
key_points:
  - "observer 遇到 Anthropic 信用餘額為空、訂閱存取被封鎖或本地模型服務停止時會暫停並保留工作；串流提前結束的批次會退回重新處理"
  - "資料庫記錄最新寫入的 schema 版本，較舊的 claude-mem 會拒絕開啟被新版升級過的資料庫"
  - "新增 CLAUDE_MEM_TOOL_USES_RETENTION_DAYS（選擇性修剪原始工具紀錄，預設保留全部）；開 PR 請改對 main"
tags: [community-release, observer, provider-fallback, search, sqlite]
topics: [engineering.rag, engineering.architecture]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.36.0

claude-mem v13.36.0 是社群主導的發布，幾乎所有自 v13.35.0 以來的變更都來自外部貢獻者。最重要的變更是供應商拒絕時不再丟棄記憶：Anthropic 信用餘額為空、組織封鎖訂閱存取，或本地模型伺服器停止運作時，observer 會暫停並保留工作（@Mola-maker）；observer 串流提前結束時，該批次會退回重新處理（@shantanukhanwalkar）。資料庫安全方面，資料庫會記錄最新寫入的 schema 版本，較舊的 claude-mem 會拒絕開啟已被新版升級的資料庫。其他修正包括：非 ASCII 的 Windows 使用者資料夾名稱（如韓文、日文）現在可找到 Bun 與 Claude；React Native 與 Expo 專案的 tsconfig 不再被誤報為錯誤；搜尋支援中日韓泰文字在句子中比對。新增功能包括 Qoder plugin 支援、CLAUDE_MEM_TOOL_USES_RETENTION_DAYS（選擇性修剪原始工具紀錄，預設保留全部）。另外，專案分支現在只剩 main，core-dev 與 community-edge 已停用。

### 重點
- observer 遇到 Anthropic 信用餘額為空、訂閱存取被封鎖或本地模型服務停止時會暫停並保留工作；串流提前結束的批次會退回重新處理
- 資料庫記錄最新寫入的 schema 版本，較舊的 claude-mem 會拒絕開啟被新版升級過的資料庫
- 新增 CLAUDE_MEM_TOOL_USES_RETENTION_DAYS（選擇性修剪原始工具紀錄，預設保留全部）；開 PR 請改對 main

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.36.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.36.0

A community release: nearly every change since v13.35.0 came from outside contributors and is merged under their own name. Thank you all. 
 Highlights 
 
 Memories are no longer dropped when the provider says no. An empty Anthropic credit balance, an organization blocking subscription access, or a local model server that is down now pauses the observer and keeps the work instead of discarding it ( @Mola-maker ). When the observer stream ends early, its batch is handed back for reprocessing ( @shantanukhanwalkar ). 
 Windows home folders with non-ASCII names work again. Bun and Claude are found when your user folder name contains Korean, Japanese or other non-ASCII characters ( @akushonkamen ). 
 Hooks don't report your project's tsconfig as errors. This affected React Native and Expo projects ( @Totopo27 ). 
 The viewer saves only what you changed, so an old settings tab can't undo a change you made elsewhere ( @Cassian433 ). 
 Search improvements: 
 
 Correct paging ( @junnhwan ). 
 Chinese, Japanese, Korean and Thai words are found inside sentences ( @rudycelekli ). 
 Long natural-language queries fall back to any-term matching when no memory matches every word ( @devkancheti4-design ). 
 
 
 Chroma reliability: 
 
 No more stalls after a reboot on large stores ( @akushonkamen ). 
 Orphaned chroma-mcp processes that hold your data directory are cleaned up safely before starting, so they no longer cause lock fights ( @akushonkamen ). 
 
 
 
 New 
 
 Qoder plugin support ( @shouldnotappearcalm ). 
 Screenpipe skill for searching meeting and screen history and saving it to memory ( @EzraEllette ). 
 Atlas Cloud preset for the OpenAI-compatible provider ( @binyangzhu000-sudo ). 
 CLAUDE_MEM_OPENROUTER_TEMPERATURE setting ( @aeneasr ). 
 CLAUDE_MEM_SEMANTIC_INJECT_FORMAT=index : compact per-prompt memory injection ( @ktdrv ). 
 CLAUDE_MEM_WORK_STATE_ENABLED=false to turn off the work-state to-do rule ( @noesis-bot ). 
 CLAUDE_MEM_TOOL_USES_RETENTION_DAYS : opt-in pruning of the raw tool log. The default keeps everything ( @Montinou ). 
 Duplicate review: record a "distinct" or "dismissed" verdict on duplicate candidates ( @Montinou ). 
 Viewer: a Claude auth method control in settings ( @akushonkamen ). 
 Server runtime: idempotent memory uploads ( @escooterclinic ). 
 
 Fixes 
 
 Capture and sessions: 
 
 Original capture timestamps are kept for delayed events ( @junnhwan ). 
 Stale session-end events are retired ( @akushonkamen ). 
 Warnings are logged before queued work is discarded ( @Boulea7 ). 
 Tool calls whose input is null are captured, logging recovers when the log folder appears later, and every shutdown step runs ( @rudycelekli ). 
 Search triggers are restored after database upgrades ( @akushonkamen ). 
 Fewer SQLite warnings on macOS ( @CCCLL ). 
 
 
 Database safety: the database records the newest schema version that has written to it, and an older claude-mem refuses to open a database a newer one has upgraded ( @akushonkamen ). 
 Memory import and notes: 
 
 Restored memories attach to existing sessions ( @junnhwan ). 
 Native note revisions survive title dedup ( @junnhwan ). 
 Explicit notes keep their platform source in the search index ( @junnhwan ). 
 Notes that start with ---- are no longer mangled ( @akushonkamen ). 
 
 
 Search robustness: malformed file lists, plain-text concepts, folder search against absolute paths, consistent date parsing, and better patterns for native search commands ( @rudycelekli ). 
 Installers and integrations: 
 
 Cursor configs with a BOM and commented Codex TOML are read correctly, and npm can no longer hang the installer ( @rudycelekli ). 
 Worker ports and IPv6 addresses are honored everywhere, and the uvx path can be set in settings ( @Ravencloned ). 
 
 
 Providers and streaming: 
 
 OpenCode Go session header ( @Cassian433 ). 
 Sturdier streamed replies, emoji never split when long output is trimmed, and Zstandard transcripts keep their text intact ( @rudycelekli ). 
 
 
 Server runtime: 
 
 Fresh installs no longer get 403 errors ( @DeryFerd ). 
 File edits reach the server, and CLAUDE_MEM_SKIP_TOOLS is honored in server mode ( @DeryFerd ). 
 Stuck jobs are reclaimed ( @escooterclinic ). 
 No stray local database ( @vinay121314 ). 
 Leaner prompts ( @rich-murphey ). 
 Postgres keeps literal __proto__ keys in stored JSON ( @rudycelekli ). 
 Stricter Redis settings ( @rudycelekli ). 
 
 
 Sync, Chroma and duplicates: 
 
 Prompts from other devices are linked ( @necatisozer ). 
 Turning Chroma off is fully honored ( @CCCLL ). 
 Fewer Chroma rewrites at startup ( @Montinou ). 
 Accent-aware duplicate detection ( @rudycelekli ) and a corrected similarity threshold ( @udsy19 ). 
 
 
 Viewer: 
 
 "Select all" in the Logs drawer works ( @DrDLyuan ). 
 The context preview opens on a project that has data ( @rudycelekli ). 
 
 
 
 Project 
 
 main is now the only branch. core-dev and community-edge are retired, so please open pull requests against main .

</details>