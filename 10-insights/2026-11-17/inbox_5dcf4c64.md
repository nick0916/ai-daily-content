---
id: inbox_5dcf4c64
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/0812-claude-code-releases-v2-1-327-0e44]]"
title: "v2.1.327"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.327
source: claude-code-releases
published_at: 2026-11-17T23:17:45+00:00
fetched_at: 2026-11-19T08:17:15.301470+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版以修 bug 與補強診斷為主，並新增幾個設定與指令。 **What** Claude Code v2.1.327 新增 /install-github-app 修改 repo 前的確認，以及 claude mcp add-json - 從 stdin 讀入 JSON，讓 token 不必出現在命令列。/status 現在會列出壞掉的 agent、skill、command 檔案、keybinding 錯誤與永遠不會匹配的 hook matcher。新增 attributionProject 設定與 /tui classic 指令。修正包括 claude mcp add/remove 在 project scope 刪掉 .mcp.json 其他頂層 key、/export 未詢問就覆寫檔案，以及 Grep 搭配 head_limit 與 offset 分頁時結果重複或遺漏。"
key_points:
  - "claude mcp add-json - 可從 stdin 讀 server JSON，避免 token 留在命令列（Claude Code session 內不可用）"
  - "/status 新增列出壞掉的 agent、skill、command、output style 檔案、keybinding 錯誤、無效 hook matcher 等診斷清單"
  - "修正 claude mcp add/remove（project scope）會刪掉 .mcp.json 內 $schema 或其他工具 server 的問題；Grep 結果改依檔案路徑排序以修正分頁錯誤"
tags: [claude-code, mcp, release-notes, diagnostics, bug-fix]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.327

Claude Code 這版以修 bug 與補強診斷為主，並新增幾個設定與指令。

**What** Claude Code v2.1.327 新增 /install-github-app 修改 repo 前的確認，以及 claude mcp add-json - 從 stdin 讀入 JSON，讓 token 不必出現在命令列。/status 現在會列出壞掉的 agent、skill、command 檔案、keybinding 錯誤與永遠不會匹配的 hook matcher。新增 attributionProject 設定與 /tui classic 指令。修正包括 claude mcp add/remove 在 project scope 刪掉 .mcp.json 其他頂層 key、/export 未詢問就覆寫檔案，以及 Grep 搭配 head_limit 與 offset 分頁時結果重複或遺漏。

### 重點
- claude mcp add-json - 可從 stdin 讀 server JSON，避免 token 留在命令列（Claude Code session 內不可用）
- /status 新增列出壞掉的 agent、skill、command、output style 檔案、keybinding 錯誤、無效 hook matcher 等診斷清單
- 修正 claude mcp add/remove（project scope）會刪掉 .mcp.json 內 $schema 或其他工具 server 的問題；Grep 結果改依檔案路徑排序以修正分頁錯誤

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.327)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added a confirmation before /install-github-app changes a repository 
 Added claude mcp add-json - to read the server's JSON from stdin, so tokens can stay off the command line; not available inside a Claude Code session 
 Added a line when a resumed session's earlier messages can't be loaded 
 Added a list in /status of broken agent, skill, command and output style files, keybinding errors, an unavailable sandbox, ignored permission settings and hook matchers that never match 
 Added a note in /config when other settings override a row 
 Added x-claude-code-managed-settings-checksum to the gateway hint headers; sent where managed settings set CLAUDE_CODE_GATEWAY_HINT_HEADERS=1 , including where they already do 
 Added support for naming a session's billing group with the attributionProject setting, for Claude apps gateways that set admin.billing_group_tag 
 Added /tui classic as the name for the non-fullscreen renderer; /tui default still works 
 Remote Control: Fixed stopping the server in worktree mode deleting a running session's git-ignored files, such as .env 
 Fixed self-hosted runners with --use-anthropic-git-proxy deleting a non-empty directory named by GIT_CONFIG_GLOBAL at startup: the runner now keeps it, ignores the variable and warns 
 Fixed claude mcp add and claude mcp remove with project scope deleting other top-level keys from .mcp.json , such as $schema or another tool's servers 
 Fixed /export overwriting an existing file without asking: the dialog now asks, and /export keeps the file and says to run /export 
 Fixed a command you had allowed still running after you pressed Stop, when the approval arrived after a restart, in cloud and self-hosted runner sessions with no feature flags loaded 
 Fixed Enter closing /teleport 's load error screen 
 Fixed a click followed by Enter in /plugin installing or disabling a plugin 
 Fixed a half-typed ! command running on an extra Enter after the usage limit menu 
 Fixed some --disallowedTools rules with parentheses in their content 
 Fixed auto mode ignoring some wildcard PowerShell allow rules that name a script with .\ , such as PowerShell(.\scripts\build.ps1 *) 
 Fixed a running Code Mode script in auto mode getting permission prompts and denials once Claude started a second script that auto mode also allowed 
 Changed some pre-started background sessions to be discarded after an account change 
 Changed a workflow paused at a usage limit in the terminal to stay paused after a login, until the earlier login returns or you type a prompt 
 Fixed a nested claude with its own token being refused by forceLoginOrgUUID : commands that don't get the session's token no longer get its CLAUDE_CODE_OAUTH_SCOPES ; set it on any that need it 
 Fixed headless sessions losing stored messages on resume when a message was sent again with the same UUID after the process was killed 
 Fixed cases where a session resumed after an empty reply or a killed command lost an answer, or brought back a rewound prompt, after another crash or a move to the background 
 Fixed a remote session forgetting messages sent after Stop was pressed during a restart, if Claude Code then crashed 
 Fixed tasks created after /clear being lost, and cleared tasks coming back, when a cloud or self-hosted runner session with no feature flags loaded resumed later 
 Fixed a compaction right after a reply cut at the output token limit losing that reply's tool call and its result 
 Fixed a settings change from /config and similar commands failing to save with no warning; a line under the prompt now says so 
 Fixed /rewind closing without a word when some files could not be restored 
 Fixed pasted images being dropped when the prompt starts with a file path such as /tmp/a.txt 
 Fixed agents passed with --agents being lost once plugins loaded or reloaded 
 Fixed a plugin's agent being dropped when resuming a session from the --resume picker 
 Fixed Claude Code refusing to start when https_proxy or HTTPS_PROXY is a bare host:port and neither its input nor its output is a terminal (the desktop app, an SDK, cron) 
 Fixed Claude Code on Linux sometimes returning to the shell while restarting itself at startup, such as after the first sign-in to a Claude apps gateway or when turning on Code Mode 
 Fixed claude -p hanging before its first request when the fetch of a model's settings stalled, such as at a proxy; it now goes on without them after 10 seconds 
 Fixed the screen staying blank or frozen after a brief out-of-memory error 
 Fixed a rare display fault that could freeze the screen or end the session 
 Fixed cloud sessions breaking when a program left thousands of connections open to the session's network proxy 
 Fixed a turn hanging when a mod's $.model.complete or $.model.classify call met a usage limit: the call now gets the API's error at once; mods should handle that error 
 Fixed stalls on a compaction reply with thousands of unclosed tags and on some very long WebFetch URLs; WebFetch now refuses a URL over 2,000 characters before any permission prompt 
 Fixed a message with thousands of @ mentions stalling before Claude replies; only the first 100 mentions are now looked up as files 
 Fixed the prompt freezing after rejecting a write to a very large file; a rejected write now shows a short preview 
 Fixed a crash when a burst of keys reached the search box in /plugin 
 Fixed a false crash report and exit code when a suspended session resumes, or at exit, where a Linux security policy blocks a process from signalling itself 
 Fixed remote MCP servers staying disconnected after a longer outage such as a VPN drop: most servers on other machines reached by hostname over https are now retried in the background for about a day 
 Fixed Edit refusing with "File has not been read yet" after a compaction on unchanged files outside the project that Claude had already read in full 
 Fixed Grep repeating or skipping results when paging with head_limit and offset ; content and count results are now sorted by file path 
 Fixed Read failing on Jupyter notebooks that contain an output of an unknown type 
 Fixed NotebookEdit removing the notebook file's final newline 
 Fixed the Read tool reporting 512KB instead of the real size when a file of 10 MB or more is too large to read at once 
 Fixed the Bash tool's diff of changed files not naming files that are binary, too large or too many to show 
 Fixed artifact publishes failing with "the source file changed between approval and publish" when a synced or remote-backed folder had only changed the file's timestamp 
 Fixed a new artifact that you approved being refused in a cloud scheduled task's session, in organizations that require approval of each new artifact 
 Fixed a new artifact being refused after an app built on the Agent SDK approved it, in organizations that require approval of each new artifact 
 Fixed /artifacts showing part of your list, or "No artifacts yet", when a request for more of the list failed: it now tries again, then warns if it can't load the whole list 
 Fixed in-process agent teammates on a different model from the lead compacting at the lead's context limit and on the wrong model; they now use their own limit and model, at that model's rate 
 Fixed a finished subagent resuming on the model and effort of a sibling subagent that messaged it 
 Fixed the main conversation not being told a background agent had finished when the subagent that started it ended by itself without reading the result, outside auto mode 
 Fixed Claude reporting a background agent as still running when it had waited 30 seconds or more on a permission prompt in the desktop app, on the web and in the SDK 
 Fixed Claude not being told in auto mode when a background agent's reply to a follow-up message was dropped, and reduced repeat wake-ups there from agents waiting on background commands 
 Fixed the desktop app, Claude Code on the web and VS Code showing a raw task notification as a subagent's prompt after its background task woke it 
 Fixed messages sent from another session with "later" priority joining the running turn, instead of waiting for it to end, in Remote Control and Claude Desktop sessions 
 Fixed messages to cloud and Remote Control sessions being reported as failed with a stale address after a timeout or rate limit; Claude now says when a message may have arrived 
 Fixed cloud sessions giving no error when a UserPromptSubmit hook blocks a message sent while Claude works 
 Fixed failing hooks showing nothing: SubagentStop in background agents, SessionEnd at /clear and /resume , and CwdChanged and FileChanged in fullscreen 
 Fixed a Stop hook that failed to run being shown as having reported a problem 
 Fixed focus view keeping a finished reply hidden while a Stop hook was running 
 Fixed Claude getting a long managed PostToolUse hook output twice when a mod added context to the tool call 
 Fixed /model listing the wrong models in some terminal sessions when a project's .claude/settings.json sets ANTHROPIC_BASE_URL to an LLM gateway 
 Fixed /statusline writing to ~/.claude/settings.json when CLAUDE_CONFIG_DIR points to another folder 
 Fixed claudeMdExcludes patterns on Windows not matching a path whose drive letter is written in the other case 
 Fixed claude agents and claude rm refusing to remove a fully pushed session ("The worktree has unpushed commits") when its worktree has a file or folder named HEAD at the top level 
 Fixed long ListAgents results hiding most sessions on accounts with many cloud or Remote Control sessions: long lists now come in pages 
 Fixed slow turns in resumed sessions for organizations with tens of thousands of connector tool permissions 
 Self-hosted runner: Fixed claude -p started by a session's script or hook waiting out rate limits, because it inherited the session's own retry setting 
 Fixed the spend limit menu reporting a changed limit when the server refused it 
 Fixed a second x on a task's details in /tasks stopping the next task too 
 Fixed Esc being ignored on a permission prompt that had just appeared 
 Fixed lists that load their rows late sometimes ignoring Enter and the arrow keys 
 Fixed /autofix-pr holding the keyboard after Esc while it stopped the cloud session; the dialog now closes at once, and a stop that fails is reported afterwards with a link 
 Fixed a blank screen and stray mouse codes in the shell after quitting with ctrl+c just after ← opens the agents view 
 Fixed Ctrl+C right after the trust question leaving the terminal in fullscreen 
 Fixed the shell flashing on screen when ← opens the agents view in fullscreen mode 
 Fixed terminal display faults: most scrambled scrollback in Ghostty on resize, link addresses hidden in Windows Terminal under old tmux and in VTE 0.50.0, and no selection highlight with 16 colors 
 Fixed some garbled rows in tmux with allow-passthrough on inside kitty, Ghostty or iTerm2 
 Fixed /mcp saying no servers were configured after one was added during a session or declined; it now says what to do 
 Fixed /hooks leaving out hooks given by --settings 
 Fixed the / menu listing a row for each skill of the same name, though every row ran the first 
 Fixed /teleport showing no message when the chosen session failed to resume 
 Fixed n and N in transcript search skipping matches 
 Fixed cancelling a transcript search (ctrl+o, then /) in a long session landing far from where the search started 
 Fixed up and down losing the cursor's column over a short or blank line 
 Fixed Tab in shell mode filling in a file name after && , ; or | , where a command goes 
 Fixed the selected session leaving the screen in claude --resume and /resume when branch names or folder paths are long 
 Fixed the MCP tool list in /mcp and /plugin losing your place when going back from a tool 
 Fixed /resume listing one session fewer than the window has room for, and a 'Resend your message' hint after most spend caps, where resending can't help 
 Fixe

[... truncated for safety ...]

</details>