---
id: inbox_6784dcb8
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0812-claude-code-releases-v2-1-328-55cc]]"
title: "v2.1.328"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.328
source: claude-code-releases
published_at: 2026-11-19T01:14:04+00:00
fetched_at: 2026-11-19T08:17:15.289758+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版把 auto mode 擴到雲端供應商，並修了大量 Code Mode、遠端 session、終端機顯示等問題。 **What** Claude Code v2.1.328 為 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry 與 Claude apps gateway 上的 Claude Opus 4.6 / Sonnet 4.6 新增 auto mode，未指定權限模式的互動 session 會從 auto mode 開始。mcp_tool hook 新增 \"onFailure\": \"block\"，hook 呼叫失敗就會擋下動作。self-hosted runner 新增 --repository-folder、--hook-label、--metadata 與兩個 orchestrator metrics。修正項目涵蓋 zsh 中以 = 開頭的字被當成指令展開、自動 compaction 沿用舊 system prompt、多項 Code Mode 錯誤、Remote Control 重複斷線訊息等。"
key_points:
  - "auto mode 擴及 Bedrock、Google Cloud Agent Platform、Microsoft Foundry、Claude apps gateway 上的 Opus 4.6 與 Sonnet 4.6"
  - "mcp_tool hook 新增 \"onFailure\": \"block\"，與 command、HTTP hook 行為一致；另新增 CLAUDE_CODE_DISABLE_DEFERRED_TOOL_RESUME"
  - "修正自動 compaction 重用舊 system prompt（現在與 /compact 一樣重建），以及 MCP 工具的 input schema 以 anyOf/oneOf/allOf 開頭時在第三方供應商上消失的問題"
tags: [claude-code, auto-mode, mcp-hooks, self-hosted-runner, code-mode]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.328

Claude Code 這版把 auto mode 擴到雲端供應商，並修了大量 Code Mode、遠端 session、終端機顯示等問題。

**What** Claude Code v2.1.328 為 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry 與 Claude apps gateway 上的 Claude Opus 4.6 / Sonnet 4.6 新增 auto mode，未指定權限模式的互動 session 會從 auto mode 開始。mcp_tool hook 新增 "onFailure": "block"，hook 呼叫失敗就會擋下動作。self-hosted runner 新增 --repository-folder、--hook-label、--metadata 與兩個 orchestrator metrics。修正項目涵蓋 zsh 中以 = 開頭的字被當成指令展開、自動 compaction 沿用舊 system prompt、多項 Code Mode 錯誤、Remote Control 重複斷線訊息等。

### 重點
- auto mode 擴及 Bedrock、Google Cloud Agent Platform、Microsoft Foundry、Claude apps gateway 上的 Opus 4.6 與 Sonnet 4.6
- mcp_tool hook 新增 "onFailure": "block"，與 command、HTTP hook 行為一致；另新增 CLAUDE_CODE_DISABLE_DEFERRED_TOOL_RESUME
- 修正自動 compaction 重用舊 system prompt（現在與 /compact 一樣重建），以及 MCP 工具的 input schema 以 anyOf/oneOf/allOf 開頭時在第三方供應商上消失的問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.328)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added auto mode for Claude Opus 4.6 and Sonnet 4.6 on Amazon Bedrock, Google Cloud's Agent Platform, Microsoft Foundry and Claude apps gateway; interactive sessions with no permission mode start in it 
 Added "onFailure": "block" for mcp_tool hooks, as for command and HTTP hooks: a hook whose call fails blocks the action 
 Added a warning when a message from a session that skips permission prompts may be held and dropped by a cloud session 
 Added a notice in /status and claude doctor when an OpenTelemetry exporter has no endpoint and its data would likely be lost 
 Added CLAUDE_CODE_DISABLE_DEFERRED_TOOL_RESUME , which lets a host stop claude -p --resume and --continue from running a tool call that a hook deferred 
 Added support for apps that embed Claude Code to switch on the policy plugin's allowManagedModsOnly option; an admin's managed settings still win 
 Added a startup warning to the Claude apps gateway when a policy's maxEffortLevel is not a valid effort level 
 Self-hosted runner: Added --repository-folder to name the folder that sessions use for a repository at --capacity 1 , in place of its path under the base folder, which can't be a symbolic link 
 Self-hosted runner: Added a start-up warning when the host's settings.json sets a default permission mode that sessions ignore 
 Self-hosted runner: Added --hook-label to claude self-hosted-runner orchestrator , to hand chosen session labels to the spawn-runner hook 
 Self-hosted runner: Added --metadata key=value to claude --environment , to label a session for the spawn-runner hook 
 Self-hosted runner: Added claude_code_self_hosted_orchestrator_session_queue_wait_by_reason_seconds to the orchestrator's /metrics , so a re-opened session's wait can be told from a new one's 
 Self-hosted runner: Added an orchestrator metric, claude_code_self_hosted_orchestrator_sessions_given_up_total , that counts by cause how often Anthropic gave up starting a runner for a session 
 Fixed Bash commands in zsh stopping with a "not found" error at a word that starts with = , such as echo ==== or [ a == b ] ; =cmd no longer expands to a command's path 
 Fixed automatic compaction reusing the session's earlier system prompt instead of rebuilding it the way /compact does 
 Fixed markdown rendering freezing on some very long or malformed input 
 Fixed rare screen freezes 
 Fixed Esc often being lost at a permission prompt or question when you typed straight after it; in terminals that send Alt as Esc and a key, an unused Alt or Option key now declines there 
 Fixed a paste or a terminal's reply being typed into the prompt when a slow connection cut it in two 
 Fixed saving a scheduled task erasing the project's other saved tasks when the scheduled tasks file can't be read, on third-party providers or with telemetry or feature flags turned off 
 Fixed a scheduled task with a typo in the project's scheduled tasks file being deleted the next time that file was saved 
 Fixed a case where a resumed cloud session could lose its compaction summary or recent messages when a message was saved late 
 Fixed the token counts on the spinner and for subagents counting a retried reply twice, missing replies that were not streamed, and standing still while Claude thinks 
 Fixed the error shown when usage credits run out mid-response, which named a rate limit 
 Fixed auto mode failing every turn outside Claude Desktop with CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS set behind a gateway rejecting betas, on Bedrock, Agent Platform, Foundry or Claude apps gateway 
 Fixed CLAUDE_STREAM_IDLE_TIMEOUT_MS not lengthening the 5-minute connection limit on gateways, custom base URLs and cloud providers 
 Fixed some Claude Desktop sessions on third-party providers, other than scheduled tasks, ending for good with "Prompt is too long" after large tool results; the largest are now left out 
 Fixed MCP tools whose input schema starts with anyOf , oneOf or allOf going missing on third-party providers or with telemetry or feature flags turned off 
 Fixed an MCP tool with an invalid input schema failing requests on third-party providers or with telemetry or feature flags turned off; the tool is now left out and Claude is told why 
 Fixed effort being turned off for a subagent's model for the session if Bedrock, Google Cloud's Agent Platform or Foundry refused its progress summary's effort setting (regression in 2.1.327) 
 Fixed Code Mode stopping a script when a permission prompt outside auto or bypass mode, a plan approval or a question stayed open for ten minutes 
 Fixed Code Mode scripts in auto and bypass-permissions modes failing to call an MCP server that had connected while the previous script was running 
 Fixed Code Mode scripts not running in the background in auto or bypass permissions mode in a session chosen in the claude --resume picker 
 Fixed Code Mode losing a loaded skill, hook context or a note typed with a permission approval when resuming a session in which one reply ran several scripts 
 Fixed Claude not being told that a Code Mode script was cut off when the session was resumed from the picker or in a mode that asks for permission 
 Fixed Code Mode silently using undefined for top-level variables that an earlier failed script never set 
 Fixed Code Mode scripts not being told when a failing command's long output was cut 
 Fixed Code Mode refusing valid scripts that start with a { block 
 Fixed Code Mode refusing scripts that use both a top-level await and a top-level return 
 Fixed an @-mentioned small file not being attached in Code Mode after a script had read or written it 
 Fixed Code Mode offering write() and edit() to read-only subagents that can't call them 
 Fixed Claude starting a turn by itself in Code Mode when Esc was followed by a command such as /model 
 Fixed Claude in Code Mode not being told to run workflows only when you ask, or the workflow size you set in /config 
 Fixed Remote Control repeating the same disconnect message, and telling you to retry a session that can't reconnect 
 Fixed a waiting permission prompt being lost, and its answer ignored, when a remote session restarted while the service was slow 
 Fixed cloud sessions resuming a cleared conversation after a rewind followed by /clear 
 Fixed a remote session losing a turn's tool calls and results when its runner or worker was lost after a dropped model stream had been retried 
 Fixed cloud and Remote Control sessions that just started, or have an @ in their title, being unreachable in cross-session messaging from a session with Remote Control on 
 Fixed Claude being told that cloud sessions can never reply; it now learns when a reply can come and how else to get the result 
 Fixed /diff , the Changes pane of Remote Control sessions and the diff beside an edit leaving out committed work after a command moved into another repository 
 Fixed Remote Control not showing a running workflow's agents when a session run by an IDE extension or other SDK app is opened over an hour after the workflow last made progress 
 Remote Control: Fixed an idle Desktop or VS Code session showing as running after Remote Control is turned on 
 Fixed the model saying background agents were still running after an SDK interrupt had stopped them 
 Fixed Send now in the desktop app and SDK hosts telling Claude that a stopped web search found no results 
 Fixed Cmd+letter being typed into the prompt in terminals that report Cmd 
 Fixed Ctrl+click opening a link twice in GNOME Terminal, side mouse buttons acting as clicks, and the first wheel notch in the other direction being ignored after a pause, in fullscreen mode 
 Fixed Shift+Enter in Konsole outside tmux and ssh, and Alt shortcuts on non-Latin keyboard layouts in terminals that speak the kitty keyboard protocol 
 Linux: Fixed pasting in other apps freezing while Claude Code is suspended with Ctrl+Z, when xclip or wl-copy is installed 
 Linux: Fixed Ctrl+V missing the clipboard image, pasting an old one or hanging 
 Fixed text copied in fullscreen mode including the quote bar, losing spaces at line wraps when a drag scrolled upward, or missing words under the "Jump to bottom" pill 
 Fixed an image path pasted into a ! command becoming an attachment 
 Fixed Ctrl+C showing no exit warning while the ? shortcuts list is open 
 Fixed Ctrl+R search in fullscreen mode and the /theme color editor picking the wrong row when keys arrive together, and keys being dropped there and in the search of /config and /plugin 
 Fixed wrong or missing colors inside GNU screen 
 Fixed many background notifications cutting into the top border of open dialogs in fullscreen mode 
 Fixed a message to a background agent showing a long file path in place of a pasted image 
 Fixed /goal removing a skill's Stop hook, or ending early on another hook's result, when both had the same wording 
 Fixed /bug saying cancelled after the report was sent 
 Fixed Esc not dismissing the transcript share question for Pro and Max users 
 Fixed /hooks losing your place when going back 
 Fixed /export writing a file named .txt when the name was left empty 
 Fixed /terminal-setup in Zed replacing a symlinked keymap.json with a plain file 
 Fixed /install-github-app adding a code review workflow when asked to update the existing workflow file 
 Fixed /plugin reopening a skill, or closing the open page, when a slow save or removal finished after you went back 
 Fixed /plugin asking to uninstall the wrong plugin, or ignoring Esc, after leaving a plugin while a change was still running 
 Fixed typing and arrow keys not working on the /plugin Installed tab after a search with no results or a click on the tab row 
 Fixed holding Enter in /plugin turning off several installed plugins 
 Fixed the /usage plugin total stopping at 2,000 tokens on 1M context models, and low token estimates in /usage and /plugin when no model is picked 
 Fixed Esc on the Bedrock access keys step closing /login instead of going back 
 Fixed /exit and Ctrl+D describing running work differently, and /exit warning about a workflow that had stopped 
 Fixed Claude calling an artifact private after reading one in a shared folder or publishing to another organization's, and saying only named people can open one when its folder's people can too 
 Fixed a plugin's toast sometimes showing another plugin's text 
 Fixed a mod saved just after a turn began sometimes reloading mid-turn instead of at the turn's end 
 Fixed one malformed OTEL_RESOURCE_ATTRIBUTES entry dropping the variable's other labels from metric points, events, and spans. Now only that entry is left off 
 Fixed agent hooks running past their timeout while compacting after a request was refused as too large 
 Fixed a crash at startup when FORCE_COLOR is set to a negative number 
 Fixed a crash in secret masking when the machine is almost out of memory 
 Fixed the Bash sandbox on Linux renaming .git/HEAD after each command when the branch name is not valid UTF-8 
 Self-hosted runner: Fixed all running sessions being stopped when a proxy or web filter answered a poll with HTTP 200 and a body such as {} ; the runner now retries such a poll 
 Self-hosted runner: Fixed deletion of a kept clone's objects or refs, and of commits that existed only there, after a temporary disk error; that start now fails instead 
 Fixed self-hosted runners stopping when their token ran out on a host whose clock is slow or was set back 
 Self-hosted runner: Fixed sessions with Anthropic-managed git losing git access to GitHub after a script or hook in the session ran claude again 
 Fixed self-hosted runners with Anthropic-managed git being unable to fetch or push where the machine's git config sets http.proactiveAuth 
 Self-hosted runner: Fixed a runner that exited without telling the server when setup failed after it had registered; it now deregisters with a reason, and an on-demand runner reports the failed start 
 Self-hosted runner: Fixed archiving or requeueing a sessi

[... truncated for safety ...]

</details>