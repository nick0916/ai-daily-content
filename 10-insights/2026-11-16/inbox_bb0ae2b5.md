---
id: inbox_bb0ae2b5
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-claude-mem-releases-v15-19-0-7c4c]]"
title: "v15.19.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.19.0
source: claude-mem-releases
published_at: 2026-11-16T02:13:21+00:00
fetched_at: 2026-11-17T23:28:32.973565+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 15.19.0 讓使用者從 My Work 直接續接 Claude Code 或 Codex 對話，並可一次性匯入 Mem0 與 Supermemory 的記憶。 **How** 每次送出訊息會啟動一次 headless resume（claude --resume -p 或 codex exec resume），訊息經 stdin 傳入；失敗不重試，且不排程、不在啟動或重連時自動執行。 **What** 新增 npx claude-mem import --from mem0 / supermemory（預設上限 10,000 筆）；Codex fork thread 現可載入記憶，但需重新批准 SessionStart hook；另新增 Zed、Aider、Grok Build 整合，並把資料夾權限改為僅擁有者可讀（0700）。"
key_points:
  - "My Work 的 Send 執行一次 headless resume；worker 重啟或關閉前會先停止所有執行中的 turn，避免重啟後的 worker 與終端機成為同一對話的第二個寫入者（Claude Code 文件指出兩個寫入者可能遺失訊息）"
  - "Mem0 / Supermemory 匯入為單向且一次性，已存在的紀錄計為 existing，--dry-run 可先預覽；限制為 10,000 筆（--max-records 最多 100,000）與 100 MiB 回應"
  - "Codex 0.165 的 fork 會觸發 SessionStart hook 的新 matcher，hooks 定義變更後需在 Codex 執行 /hooks 重新批准，否則 fork thread 沒有召回記憶"
tags: [claude-mem, my-work, headless-resume, memory-import, codex-hooks]
topics: [agents.coding_agents, agents.mcp, security]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.19.0

claude-mem 15.19.0 讓使用者從 My Work 直接續接 Claude Code 或 Codex 對話，並可一次性匯入 Mem0 與 Supermemory 的記憶。

**How** 每次送出訊息會啟動一次 headless resume（claude --resume -p 或 codex exec resume），訊息經 stdin 傳入；失敗不重試，且不排程、不在啟動或重連時自動執行。

**What** 新增 npx claude-mem import --from mem0 / supermemory（預設上限 10,000 筆）；Codex fork thread 現可載入記憶，但需重新批准 SessionStart hook；另新增 Zed、Aider、Grok Build 整合，並把資料夾權限改為僅擁有者可讀（0700）。

### 重點
- My Work 的 Send 執行一次 headless resume；worker 重啟或關閉前會先停止所有執行中的 turn，避免重啟後的 worker 與終端機成為同一對話的第二個寫入者（Claude Code 文件指出兩個寫入者可能遺失訊息）
- Mem0 / Supermemory 匯入為單向且一次性，已存在的紀錄計為 existing，--dry-run 可先預覽；限制為 10,000 筆（--max-records 最多 100,000）與 100 MiB 回應
- Codex 0.165 的 fork 會觸發 SessionStart hook 的新 matcher，hooks 定義變更後需在 Codex 執行 /hooks 重新批准，否則 fork thread 沒有召回記憶

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.19.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Continue a Claude Code or Codex conversation from My Work 
 Open a request in My Work, then open "Where this came from". Under each Claude Code or Codex conversation there is now a message box. Type a message and press Send, and that same conversation takes the turn. The reply shows right there ( #6191 ; the command shapes follow @wiesenthal 's answer code in #6054 , and the commit credits him). 
 
 Each conversation keeps the messages you sent from My Work and their replies, in order. Stop ends a running turn. 
 The box says which folder the turn runs in. When the recorded folder no longer exists (common after a worktree is cleaned up), the turn runs in the nearest existing folder above it. 
 "Copy resume command" copies claude --resume or codex resume . On a Mac, "Open in Claude" opens a Claude Code conversation in the Claude desktop app. 
 One Send starts one headless resume ( claude --resume -p --output-format json , or codex exec resume - --skip-git-repo-check ) with your message on stdin. A failed turn is recorded as failed and never retried. Nothing is queued or saved for replay, and nothing starts at startup, on a timer or on reconnect. 
 A worker restart or shutdown stops every running turn first, so a restarted worker never becomes a second writer on the same conversation. Nothing re-sends a stopped turn. 
 A turn runs in your own default permission mode, the same one claude -p --resume uses in your terminal. In Manual mode, tool calls that need approval are denied and the row counts them. No permission, model or sandbox flag is passed. 
 The new routes answer only on loopback and refuse other origins. With local API token mode off, another program on the same computer can call them, as it can every other worker route. On a shared computer, turn on local API token mode. 
 One change for every request: while a newer version of an open request loads, the drawer keeps showing the version it already has instead of "Loading request detail...". 
 
 Known limits: 
 
 The Codex path through the page was not run end to end on the test machine. Codex turns were checked at the runner level with the real CLI. 
 On Windows, Stop may not reach a CLI behind a .cmd shim, and "Open in Claude" is not offered. 
 A conversation that is mid-turn in a terminal can still get a turn from My Work. Claude Code's docs say two writers on one session can lose messages. My Work blocks two of its own turns on one conversation. 
 A worker crash (not a graceful restart) cannot stop a running turn. It finishes on its own. 
 A helper the CLI leaves behind, such as a slow-exiting MCP server, keeps the turn marked as running until it exits or you press Stop. 
 
 Bring your existing memory 
 npx claude-mem import fetches memories straight from Mem0 Platform or Supermemory and saves them as searchable observations in a project you choose. No export file and no model calls ( #6106 ). 
 # MEM0_API_KEY in the environment 
npx claude-mem import --from mem0 --source-account personal-mem0 --user my-user-id --project imported-memory

 # SUPERMEMORY_API_KEY in the environment 
npx claude-mem import --from supermemory --source-account personal-supermemory --namespace my_namespace --project imported-memory 
 
 Start the worker first ( npx claude-mem start ). Add --dry-run to fetch and check the source and print counts without writing anything. 
 Every source page is fetched and checked before anything is written. Expired or replaced Mem0 memories and forgotten or older Supermemory memories are skipped. For Supermemory, --documents imports extracted document text instead of memories. 
 Imported memories are filed for Claude Code ( claude ), so its memory search finds them. --platform (for example codex or cursor ) files them under another host. Each observation keeps the source record, ID, timestamps, metadata, account label and scope. 
 Running the same command again is safe: records already saved are counted as existing. There is no background job and no automatic retry. 
 This is a one-way import, not a sync. Edits at the source make new observations. Deletions and expirations at the source are not carried over. 
 Limits: 10,000 records by default ( --max-records up to 100,000), 100 MiB of source responses, a 15-second request deadline ( --timeout-ms up to 120,000) and 100,000 characters per record. Nothing is cut short silently: an oversized record or a failed request stops the run. 
 The tests use synthetic Mem0 and Supermemory responses, not live accounts. 
 
 Docs: https://docs.claude-mem.ai/usage/import-providers 
 Codex: forked threads get memory 
 
 
 Forked Codex threads start with recalled memory ( #6101 ). Codex 0.165 added a fork session start for its experimental attached thread forks. claude-mem's SessionStart hook didn't match it, so a forked thread started with no memory. The hook now matches fork . 
 Codex users: approve one hook again. The SessionStart hook's matcher changed, and Codex asks for approval again whenever a hook's definition changes. 
 
 Get the new matcher into ~/.codex/hooks.json . npx claude-mem update and auto-update do this when your last install selected Codex. Otherwise run npx claude-mem install and select Codex. 
 Open interactive Codex, run /hooks , and approve claude-mem's SessionStart hook. 
 
 Until you approve it, Codex sessions start without recalled memory. Capture keeps working. Until the new matcher is in hooks.json , npx claude-mem doctor shows the Codex hooks row as out of date. 
 
 
 Also new 
 
 Server runtime: search results say which agent made a memory ( #6100 ). The server runtime now stores the agent on each memory and fills it in for existing memories from their session. Its MCP search and detail lines add [via ] , for example #8 — Auth redirect decision (myproject) [via cursor] . Memories with no recorded agent show no tag. /api/sessions/observations no longer labels every client as Claude Code. The local worker's observation results don't carry the agent yet, so they show no tag. 
 Zed ( #6111 , thanks @AdityaxDeore , closes #5900 ). npx claude-mem install (or --ide zed ) registers claude-mem's MCP server in Zed's context_servers , for search, timeline, details and explicit saves. Comments in Zed's settings file are kept. There is no automatic capture, because Zed has no hooks or transcript access. Docs: https://docs.claude-mem.ai/zed-integration 
 Aider ( #6112 , thanks @AdityaxDeore , closes #5893 ). Run npx claude-mem aider install inside a project. It adds .claude-mem/aider-memory.md to the read: list in .aider.conf.yml , and npx claude-mem aider sync refreshes that file from the worker. It is opt-in per project: npx claude-mem install doesn't offer it, the memory file is kept out of git through .git/info/exclude , and it refuses to run in your home folder. No automatic capture. Docs: https://docs.claude-mem.ai/aider-integration 
 Grok Build gets recalled memory at session start ( #6180 , thanks @krishnadobhal , closes #5950 ). Grok Build ignores what SessionStart hooks print, so recalled notes never reached the model. claude-mem grok install writes .grok/rules/claude-mem-context.md in the current folder, which Grok Build loads from trusted folders. The worker refreshes it after each session summary, only in folders you installed it in. An excluded project gets an "excluded" line instead of notes. Capture is unchanged. Docs: https://docs.claude-mem.ai/grok-build 
 French in the language picker for My Work, the viewer, first-run setup and Observation TV ( #6107 , thanks @QuantScorpus ). Your memories, rules and quotes stay as written. 
 Three new presets for the OpenAI-compatible provider. Each defaults to a small, fast model, because memory extraction is high volume:
 
 AtmoRouter, zai/glm-5.3-flash ( #6108 , thanks @BeckleyTenriajeng ) 
 TrustedRouter, deepseek/deepseek-v4-flash ( #6174 , thanks @jperla ). trustedrouter/auto stays available as an opt-in. It can route a request to a model priced at frontier rates. 
 HopBase, deepseek-v4.1-flash ( #6181 , thanks @victor-zzh ) 
 
 
 
 Fixes 
 Privacy and security 
 
 The claude-mem data folder is owner-only ( #6091 , thanks @DeryFerd ). On macOS and Linux, ~/.claude-mem (database, settings, .env , hook spool, backups) was created with a plain mkdir , so under the common 022 umask other accounts on the machine could read it. It is now created as 0700 , an existing folder is tightened on the next start, and new hook spool entries are written as 0600 . 
 MCP save_memory honors CLAUDE_MEM_EXCLUDED_PROJECTS ( #6105 , thanks @Zhong-fan , reported by @Kirat0201 in #6098 ; @0xABCD01 sent the same fix in #6166 ). A save from an excluded checkout was stored over MCP while the same save over HTTP was skipped. It is skipped now, and the reply says "Not saved: this checkout is excluded by CLAUDE_MEM_EXCLUDED_PROJECTS." instead of "Saved memory #?: Untitled.". The Cline and Kilo guides now say so ( #6190 ). 
 Server runtime: the MCP connect command refuses an unusable Host ( #6176 , thanks @DeryFerd ). Without CLAUDE_MEM_PUBLIC_URL , GET /v1/connect and POST /v1/keys built the paste-ready command from the request's Host header and copied whitespace, quotes or paths into it. A value that cannot be a host now gets 400 InvalidHost , and no key is minted. 
 Sync hub: FORWARD_ORIGIN must use https:// ( #6175 , thanks @DeryFerd ). The forward proxy copies the incoming Authorization header to the target, so a plain http:// origin could send it without TLS. http:// is allowed only for loopback hosts. A value that isn't a usable URL now fails loudly instead of quietly falling back to the Durable Object path. 
 
 Install and uninstall 
 
 Uninstall removes the Gemini CLI hooks ( #6088 , thanks @tanishqbaweja ). npx claude-mem uninstall deleted the plugin but left claude-mem's five Gemini CLI hooks in ~/.gemini/settings.json , so Gemini CLI printed a failed-hook message at every session start, prompt, tool call and turn end. Uninstall now removes them and keeps your own settings and hooks. A settings.json with comments is left untouched, so remove those hooks by hand. 
 Cancelling the API-key prompt no longer switches you to Claude ( #6161 , thanks @bulanovk ). With --provider gemini or --provider openrouter and no saved key, cancelling the key prompt wrote CLAUDE_MEM_PROVIDER='claude' and carried on. It now stops with an error and changes nothing. 
 The Codex installer's legacy-config check expands a leading ~\ only on Windows, like the rest of claude-mem ( #6093 , thanks @DeryFerd ). 
 
 Worker and storage 
 
 A worker that meets a busy database at startup retries instead of answering 503 for minutes ( #6145 , thanks @montjeffrey , refs #3603 ). A replacement worker could hit SQLITE_BUSY_SNAPSHOT once during database startup, never retry, and answer every request with "Service initializing" until a manual restart (about 11 minutes in the report). Startup now retries a busy error 3 times, after 1, 2 and 4 seconds. The worst case (27 s) fits inside the 30 s the hook waits for the worker to be ready. Other errors still fail at once. 
 Closing the database releases it ( #6090 , thanks @DeryFerd ). Cached prepared statements kept the connection and the database file open after close. On Windows that blocked restore swaps and temp-folder cleanup with EPERM or EBUSY . 
 Chroma cleanup for deleted sessions survives a worker exit ( #6163 , thanks @Afloat16 ). If the worker exited before the queued cleanup ran, the deleted rows' vectors were never removed. The cleanup is now recorded before it starts. The same change fixes a check that treated a missing row as restored on Bun. 
 On Bun, a database whose sync launch exclusions table went missing rebuilds it instead of keeping an empty list ( #6189 ). 
 A failing /api/ready subscriber no longer stops startup progress for the others or turns into a startup failure ( #6127 , thanks @Afloat16 ). 
 
 Capture and memory notes 
 
 CLAUDE_MEM_SKIP_BASH_PATTERNS applies to Antigravity CL

[... truncated for safety ...]

</details>