---
id: inbox_f7685f2f
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-claude-code-releases-v2-1-319-f991]]"
title: "v2.1.319"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.319
source: claude-code-releases
published_at: 2026-11-06T17:04:01+00:00
fetched_at: 2026-11-07T01:45:05.028346+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.319 讓 auto mode 在無法連到伺服器檢查時改為詢問或拒絕，並新增 MCP 背景任務與大量修正。 **Why** auto mode 在關閉 telemetry、feature flag 或走 LLM gateway 時，伺服器端安全檢查可能無法到達；原文因此調整為「查不了就問或拒絕」，並修補多項權限繞過與沙箱問題。 **How** 無法由伺服器檢查的呼叫不再退回內建 classifier，可用 CLAUDE_CODE_AUTO_MODE_SERVER=0 保留舊行為，=1 則在 gateway 後強制開啟伺服器端檢查；MCP server 以 task 執行工具時會立即移到背景，完成後再通知 Claude。 **What** 新增 permissions.denyInsteadOfPrompting（遇權限提示直接拒絕並繼續）、CLAUDE_CODE_DISABLE_FEATURE_FLAGS、CLAUDE_CODE_DISABLE_MCP_TASK_BACKGROUND、/claude-api latency-optimize、/usage 顯示今日/本週/本月花費，以及 Claude apps gateway 的 admin.pooled_conflict_rule、login_notice、JSON log 等設定。安全修正包含 Bash 權限的環境變數前綴繞過、sed 跳過權限檢查、建立 worktree 時的沙箱逃逸、/rewind 經 symlink 還原或刪檔；另外 claude -p 在 auto mode 被拒時改為 exit 1。"
key_points:
  - "auto mode 在 telemetry/feature flag 關閉或 LLM gateway 後，無法查證的呼叫改為詢問或拒絕；CLAUDE_CODE_AUTO_MODE_SERVER=0 可保留內建 classifier，=1 強制啟用伺服器端檢查（Bedrock、Vertex、Foundry 不變）"
  - "新增 MCP task 背景執行支援、permissions.denyInsteadOfPrompting 設定與 CLAUDE_CODE_DISABLE_FEATURE_FLAGS（停止 flag 抓取但不關 telemetry）"
  - "多項安全修正：Bash 環境變數前綴權限繞過、sed 跳過 accept-edits/auto mode 檢查、worktree 沙箱逃逸、/rewind 經目錄 symlink 還原或刪檔、--trust-workspace false 現在也會擋 repo 內 hooks"
tags: [claude-code, auto-mode, permissions, mcp-tasks, llm-gateway]
topics: [agents.coding_agents, agents.mcp, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.319

Claude Code v2.1.319 讓 auto mode 在無法連到伺服器檢查時改為詢問或拒絕，並新增 MCP 背景任務與大量修正。

**Why** auto mode 在關閉 telemetry、feature flag 或走 LLM gateway 時，伺服器端安全檢查可能無法到達；原文因此調整為「查不了就問或拒絕」，並修補多項權限繞過與沙箱問題。

**How** 無法由伺服器檢查的呼叫不再退回內建 classifier，可用 CLAUDE_CODE_AUTO_MODE_SERVER=0 保留舊行為，=1 則在 gateway 後強制開啟伺服器端檢查；MCP server 以 task 執行工具時會立即移到背景，完成後再通知 Claude。

**What** 新增 permissions.denyInsteadOfPrompting（遇權限提示直接拒絕並繼續）、CLAUDE_CODE_DISABLE_FEATURE_FLAGS、CLAUDE_CODE_DISABLE_MCP_TASK_BACKGROUND、/claude-api latency-optimize、/usage 顯示今日/本週/本月花費，以及 Claude apps gateway 的 admin.pooled_conflict_rule、login_notice、JSON log 等設定。安全修正包含 Bash 權限的環境變數前綴繞過、sed 跳過權限檢查、建立 worktree 時的沙箱逃逸、/rewind 經 symlink 還原或刪檔；另外 claude -p 在 auto mode 被拒時改為 exit 1。

### 重點
- auto mode 在 telemetry/feature flag 關閉或 LLM gateway 後，無法查證的呼叫改為詢問或拒絕；CLAUDE_CODE_AUTO_MODE_SERVER=0 可保留內建 classifier，=1 強制啟用伺服器端檢查（Bedrock、Vertex、Foundry 不變）
- 新增 MCP task 背景執行支援、permissions.denyInsteadOfPrompting 設定與 CLAUDE_CODE_DISABLE_FEATURE_FLAGS（停止 flag 抓取但不關 telemetry）
- 多項安全修正：Bash 環境變數前綴權限繞過、sed 跳過 accept-edits/auto mode 檢查、worktree 沙箱逃逸、/rewind 經目錄 symlink 還原或刪檔、--trust-workspace false 現在也會擋 repo 內 hooks

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.319)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Changed auto mode with telemetry or feature flags off, including behind LLM gateways: calls the server can't check are asked about or denied, with no fallback to the built-in classifier; set CLAUDE_CODE_AUTO_MODE_SERVER=0 to keep using it (Bedrock, Vertex and Foundry are unchanged) 
 Changed auto mode behind an LLM gateway: CLAUDE_CODE_AUTO_MODE_SERVER=1 turns on the server-side check even with CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS set; if managed settings set the latter, they must set the 1 too 
 Added support for MCP tasks in the terminal: when an MCP server runs a tool call as a task, Claude Code moves it to the background right away and tells Claude the result when it finishes 
 Added the CLAUDE_CODE_DISABLE_MCP_TASK_BACKGROUND environment variable to make Claude Code wait for an MCP task inside its tool call instead of moving it to the background right away 
 Added permissions.denyInsteadOfPrompting setting: a tool call that would wait on a permission prompt is denied and the turn continues, in terminal sessions, subagents and teammates 
 Added /claude-api latency-optimize to find where your Claude API code makes people wait and try faster settings against your eval 
 Added the CLAUDE_CODE_DISABLE_FEATURE_FLAGS environment variable, which stops feature-flag fetching without turning off telemetry; every flag then uses its built-in default 
 Added spend for today, this week and this month to /usage for developers behind a Claude apps gateway who have no spend limit, when the gateway runs this version or later 
 Added admin.pooled_conflict_rule and admin.pooled_priority_order to the Claude apps gateway, to set which pooled group budget pays first for a developer in several groups 
 Added an optional login_notice setting to the Claude apps gateway that shows an operator-defined message on the gateway's browser verification page and on Claude Code's sign-in screen 
 Added CLAUDE_GATEWAY_LOG_FORMAT=json to the Claude apps gateway: operational log lines become JSON with severity , time and message , for log collectors that read the level from a field 
 Added a Claude apps gateway boot warning for a case where another policy's availableModels also allows a custom model id that one policy lists by name 
 Added start-up warnings to the Claude apps gateway for policies with no desktopHome that rely on coworkTabEnabled: false or chatSessionRetentionDays , ahead of Claude Desktop's November 10 change 
 Added a warning when your claude.ai login ends and Claude Code continues on the sign-in from ant auth login , which bills usage to your Claude Console organization 
 Added a line at startup naming the Claude Console organization that is billed in a case where Claude Code uses the sign-in from ant auth login 
 Added an "Earlier in this session" row to /tasks that lists finished subagents, so you can reopen one and message it even after it leaves the list or you restart 
 Added a note to /loop confirmations in cloud sessions that a timer stops with its container, with an offer of a loop that survives 
 Fixed MCP servers on the older handshake failing to connect, or returning empty results, because Claude Code declared an extension that it only uses with newer servers 
 Fixed a long-running MCP tool call on a claude.ai connector sometimes never reporting its result after --resume 
 Fixed a session's diff failing to load on claude.ai and the mobile apps when the folder Claude Code runs in has a file or folder named HEAD 
 Fixed /diff showing "Diff unavailable" when a git repository has a file or folder named HEAD at its top level 
 Fixed the /diff pane opening blank in sessions where 64 or more turns edited files 
 Fixed slash commands typed after a leading space, tab or newline being sent to Claude as plain text instead of running 
 Fixed a request that kept failing with a 401 refreshing your login on every retry and causing 401s in your other sessions 
 Fixed /context sending its full visual grid to Claude on every later turn; Claude now reads only the table 
 Fixed claude -p exiting 0 in auto mode when its actions were refused because no safety check was available: text and JSON output now exit 1 
 Fixed a case where Claude Code listed every project file at start on Linux for projects on a network file system (NFS, SMB, Lustre and similar) 
 Fixed a case where auto mode was wrongly refused when a client sent a model change and a request for auto mode back to back 
 Fixed /status showing "Auto mode server: Enabled" when the server-side review isn't reaching the session, for example behind an LLM gateway that drops it 
 Fixed Claude-drafted feedback, surveys and /feedback continuing to appear after the server refused feedback for your organization 
 Fixed Claude drafting feedback on third-party gateways, where it can't be sent 
 Fixed auto mode refusing actions without saying why when permission rules or autoMode settings are very large: it now explains and, unless autoMode deny rules are set, asks you in the terminal 
 Fixed a case where Bash deny and ask rules missed commands written with quoted words 
 Fixed subagent hand-back reports showing an internal marker and provenance note when expanded outside verbose mode 
 Fixed claude -p --resume with a prompt losing a deferred tool call when its MCP server is missing: the run now exits 1, keeps the call and refuses later input 
 Fixed a case where text was dropped from informational messages sent to SDK clients 
 Fixed a case where Agent SDK hosts got a generic exit-code error instead of a failed run's own error message when the disk was full 
 Fixed CLAUDE_CODE_RESUME_INTERRUPTED_TURN re-running a turn that was interrupted in plan mode when the session resumes in another permission mode 
 Fixed edits to a settings file being ignored when made within a few seconds of Claude Code writing that file 
 Fixed a config file left at the legacy name hiding your setup with no warning: Claude Code now says on stderr when a home holds two config files, and which is in use 
 Fixed ~/.claude.json , settings and edited files ending up empty or cut off when the disk fills during a save in a read-only folder or to a bind-mounted file (one session saving at a time) 
 Fixed Write ending the turn as a refusal when it couldn't read the file to overwrite 
 Fixed background Bash commands that finish almost instantly losing their output while being reported as completed 
 Fixed the Bash tool's diff of changed files missing a file that the command wrote just before it ended 
 Fixed a mistyped model name, such as opus-5-5 , telling you to update Claude Code instead of suggesting the model you meant 
 Fixed a case where NotebookEdit changed the wrong cell when the notebook changed while a permission prompt was open 
 Fixed a ~0.5s hang after pressing Enter on the /login success screen: the dialog now dismisses immediately and the post-login refresh runs in the background 
 Fixed Ctrl+G not opening the external editor while typing an "Other" answer to a question in screen reader mode 
 Fixed Monitor's WebSocket watch failing with "could not resolve" behind a proxy when CLAUDE_CODE_PROXY_RESOLVES_HOSTS is set and the machine has no DNS of its own 
 Fixed claude plugin eval warnings suggesting max: 0 for a tool that must not be called, which could never pass 
 Fixed background plugin auto-update not installing a dependency added by the updated plugin version 
 Fixed Cmd+click not opening links in Ghostty over tmux in sessions opened from the agents view 
 Fixed a mod's hot reload in .claude/skills missing a file that was deleted just after it appeared, and missing its return 
 Fixed /rewind failing with "No files were restored" when restoring code to a checkpoint from before /branch 
 Fixed the /claude-api skill saying Console web settings don't apply to Managed Agents sessions, and tightened its credential and permission examples 
 Fixed needless permission prompts for read-only commands wrapped in a plain timeout DURATION , such as timeout 30 rg foo 
 Fixed WebFetch describing claude.ai shared-chat links as empty pages; it now says shared chats can't be read and to paste the conversation instead 
 Fixed Artifact database calls being re-sent to artifacts without a database; errors now say whether republishing helps 
 Fixed a case where artifact database reads that save to a folder ( out_dir ) were refused 
 Fixed detailed beta tracing not presenting CLAUDE_CODE_CLIENT_CERT to collectors that require a client certificate 
 Fixed the OpenTelemetry claude_code.session.count metric counting Agent SDK prewarm() processes that were never claimed; a pre-started process now counts once, when it is claimed 
 Fixed /clear killing running commands of background agents, teammates and workflows that keep running, and foreground subagents of background agents and teammates 
 Fixed a terminal whose Claude apps gateway sign-in had expired sending telemetry and managed-settings requests that the gateway refused and logged as invalid_token 
 Fixed the agents view appearing to send a reply to a background session waiting on a permission prompt; the reply now stays in the box with a hint to open the session and answer 
 Fixed agent view removing a draft saved by another agent view in the same directory when exiting 
 Fixed a case where agent view came back with another agent view's input text after restarting itself for an update 
 Fixed the agents view preview cutting off long commands, results and status lines without an ellipsis, and dropping ** , backticks and tags from commands waiting for approval 
 Fixed Claude in Chrome reporting the extension as not connected when the connection dropped mid-action; Claude now checks the page before repeating an action that may have run 
 Fixed Remote Control sessions still showing "Limit reached" on other devices after a usage limit was lifted outside the session 
 Fixed the file card sometimes missing in the Claude iOS app when Claude sent a single file 
 Fixed self-hosted runner sessions failing with no explanation when the server keeps refusing to renew model access: the runner now retries sooner and posts a warning in the session 
 Fixed /permissions in cloud sessions replying only that it isn't available; it now says where the session's rules live and how to change them 
 Fixed cloud sessions losing session-scoped deny and ask permission rules, such as those a PermissionRequest hook adds, when the session moves to a new worker 
 Fixed mod hot-reloading turning off for the session when you typed three messages instead of answering its question in a cloud session 
 Fixed background tasks that keep running after /clear disappearing from the task list in Claude Code on the web until another task started or ended 
 Fixed hidden commands appearing in the slash command menu of cloud sessions on mobile and web 
 Fixed a case where /rewind could restore or delete a file through a directory symlink 
 Fixed a case where a sed command could skip the permission check in accept-edits and auto mode 
 Fixed a case where CLAUDE_CODE_AUTO_MODE_SERVER=1 in managed settings was ignored behind an LLM gateway when the gateway's URL is set only there and server-managed settings can't be fetched 
 Fixed a Bash permission bypass where a crafted environment prefix could hide part of a command from permission checks 
 Fixed a case where deny and ask rules, hook matchers and disallowedTools entries written with a claude.ai connector's terminal name ( mcp__claude_ai_Slack ) were ignored in Claude Desktop (takes effect once Claude Desktop includes this version) 
 Fixed a sandbox escape when creating a worktree 
 Fixed self-hosted runners: --trust-workspace false now also stops hooks in the repository's settings files and skills from running 
 Fixed a case where idle background sessions started through a shell-exported LLM gateway left the gateway after an update 
 Fixed help links in /status and the auto mode billing notice opening only part o

[... truncated for safety ...]

</details>