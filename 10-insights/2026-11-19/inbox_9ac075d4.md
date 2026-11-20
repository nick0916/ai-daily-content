---
id: inbox_9ac075d4
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0105-claude-code-releases-v2-1-329-bedf]]"
title: "v2.1.329"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.329
source: claude-code-releases
published_at: 2026-11-19T22:14:41+00:00
fetched_at: 2026-11-20T01:10:29.348791+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版以修 bug 為主，順帶補上 hooks、/tasks、/mcp 等的狀態提示。 **What** Claude Code v2.1.329 新增：信任對話框會標示 hooks 宣告位置、/tasks 可管理排程任務與 /loop wakeups、/mcp 顯示遠端 HTTP MCP server 拒絕連線的 JSON-RPC 錯誤訊息、/status 顯示 marketplace 自動更新狀態，並支援在啟用 OpenTelemetry 事件與指標時開啟 Code Mode。修正項目很多：~/.claude.json 被重設、macOS Keychain 反覆登出、/terminal-setup 破壞 VS Code 設定、Code Mode 失控迴圈耗盡記憶體（現有上限）、/code-review 審到錯誤分支等，另改善長 session 的記憶體用量。（原文後段被截斷）"
key_points:
  - "Code Mode 修正：失控迴圈填滿記憶體現在會在上限處被停止；腳本等待 MCP 呼叫改為最多十分鐘後才報錯；超過 4,096 個工具的 session 不再失去工具存取"
  - "新增 /tasks 管理本 session 的排程任務、/loop wakeups、goal 與 forks（按 x 先確認再停止）；/mcp 新增「Server message」列，/status 新增「Marketplace auto-update」列"
  - "修正 ~/.claude.json 在網路中斷或檔案鎖定時被重設為預設值，以及 macOS 在 Keychain 可讀不可寫時反覆登出的問題"
tags: [claude-code, release-notes, code-mode, mcp, bug-fixes]
topics: [agents.coding_agents, agents.mcp]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.329

Claude Code 這版以修 bug 為主，順帶補上 hooks、/tasks、/mcp 等的狀態提示。

**What** Claude Code v2.1.329 新增：信任對話框會標示 hooks 宣告位置、/tasks 可管理排程任務與 /loop wakeups、/mcp 顯示遠端 HTTP MCP server 拒絕連線的 JSON-RPC 錯誤訊息、/status 顯示 marketplace 自動更新狀態，並支援在啟用 OpenTelemetry 事件與指標時開啟 Code Mode。修正項目很多：~/.claude.json 被重設、macOS Keychain 反覆登出、/terminal-setup 破壞 VS Code 設定、Code Mode 失控迴圈耗盡記憶體（現有上限）、/code-review 審到錯誤分支等，另改善長 session 的記憶體用量。（原文後段被截斷）

### 重點
- Code Mode 修正：失控迴圈填滿記憶體現在會在上限處被停止；腳本等待 MCP 呼叫改為最多十分鐘後才報錯；超過 4,096 個工具的 session 不再失去工具存取
- 新增 /tasks 管理本 session 的排程任務、/loop wakeups、goal 與 forks（按 x 先確認再停止）；/mcp 新增「Server message」列，/status 新增「Marketplace auto-update」列
- 修正 ~/.claude.json 在網路中斷或檔案鎖定時被重設為預設值，以及 macOS 在 Keychain 可讀不可寫時反覆登出的問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.329)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added a trust dialog warning that says where a folder's hooks are declared 
 Added a warning in the conversation, in Claude Desktop and other non-interactive hosts, when hooks in managed settings fail to load 
 Added this session's scheduled tasks, /loop wakeups, the goal and this conversation's forks to /tasks ; x stops one after asking 
 Added a "Server message" row to a server's page in /mcp that shows the JSON-RPC error message of a remote HTTP MCP server that refuses the connection 
 Added a "Marketplace auto-update" row to /status that names managed marketplaces that get no automatic updates, and why 
 Added support for turning on Code Mode while OpenTelemetry events and metrics are enabled; each tool call the code makes sends its events; tracing still keeps it off 
 Fixed ~/.claude.json sometimes being reset to defaults when a network stall or file lock made it unreadable and cleared during a save 
 Fixed repeated sign-outs on macOS when Claude Code could read the Keychain but not save to it. That session now stops at expiry and says why, and other sessions stay signed in 
 Fixed /terminal-setup corrupting VS Code settings or keybindings files around block comments, and reporting success while losing the Shift+Enter binding where keybindings.json has an unclosed string 
 Fixed files accepted through the IDE diff being saved without their last newline, and losing their byte order mark (BOM) when an edit was accepted by saving the diff in VS Code 
 Fixed picking a cloud session in /teleport replacing your open conversation: the pick now starts a new session, as /clear does, and /resume brings the old one back 
 Fixed /usage-credits asking Pro and Max users to log in again after opening the browser, and the link disappearing after 8 seconds if the browser doesn't open and a task stops for usage credits 
 Fixed /usage saying usage credits are off when they had run out or reached the monthly limit, and /model not telling Pro and Max users when that limit blocks a model that runs on usage credits 
 Fixed the spend limit menu showing your spend as your monthly limit and wrapping its rows under the pointer in narrow windows 
 Fixed a status line script that prints without end freezing the prompt and using gigabytes of memory 
 Fixed an empty, frozen screen after approving managed settings while the --resume picker, the trust dialog or another set-up screen was waiting 
 Fixed choosing Default in /model replacing your saved model with your organization's default when the Default row already showed your saved model 
 Fixed an MCP server being signed in again after you cleared its authentication while a token refresh was running 
 Fixed background MCP tasks that stalled after a slow reconnect: Claude Code now reconnects most HTTP MCP servers by itself when one is left on an older protocol version 
 Fixed PDFs, images and .docx , .xlsx or .pptx files that MCP servers or websites send as application/octet-stream being saved as .bin, which kept Claude from reading the PDFs and images 
 Fixed /code-review sometimes reviewing the checked-out branch instead of the pull request without saying so: it now reads the pull request with gh pr diff , or says when it can't 
 Fixed /code-review stopping at a permission prompt, on most models, to look for a ~/.claude/CLAUDE.md that doesn't exist 
 Self-hosted runner: Fixed --push-outcome-on-release sometimes deleting a session's branch on the git host 
 Fixed Code Mode hiding a script's finished edits and the stopped command after Esc, and losing them on exit 
 Fixed a runaway loop in Code Mode filling the machine's memory; it is now stopped at a limit 
 Fixed a background agent running on when it was stopped while it was being resumed 
 Fixed background shell commands using memory for the earlier conversation until they exit 
 Fixed Remote Control using memory for the earlier conversation after a compaction or /clear in sessions run by Claude Desktop, IDEs or the SDK 
 Fixed Stop not ending a request in Claude Desktop sessions on Bedrock while it waits on a hung AWS credential_process or sign-in call 
 Fixed Claude sometimes failing to send you a file on its first try on Opus 4.8 and Opus 5 
 Fixed Claude not being told that a connected MCP server's tools could not be loaded, and taking it for a server with no tools, in sessions with tool search 
 Fixed claude mcp login and /mcp saying a service doesn't accept sign-ins from Claude Code when the service's client registration had been retired (HTTP 410 Gone) 
 Fixed another case of claude.ai-synced plugin hooks failing with "Plugin directory does not exist" while a session was still running on macOS 
 Fixed auto mode asking for manual approval to rm a symlink that points outside the working directory or at itself 
 Fixed /sandbox on Linux listing allowUnixSockets entries as allowed: they don't open those sockets there, and /sandbox now says so 
 Fixed pressing Esc twice to clear a mistyped code ending the sign-in in /install-github-app 
 Remote Control: Fixed sessions going back to their first effort level after a restart while the app still showed the level you picked (not yet for sessions that start in Ultracode) 
 Fixed a removed plugin's MCP server staying connected in headless sessions after reload_plugins or when the account's plugin list drops it 
 Fixed the Claude Docs connector's tools going missing when a plugin or MCP server at the same address failed to connect, and its error wrongly suggesting /login 
 Fixed a new skills, commands or agents folder being missed when --add-dir names the working directory or Claude Code starts in the home folder 
 Fixed sessions started from a pre-warmed process ignoring the autoCompactWindow setting in the project's .claude/settings.json 
 Fixed CLAUDE_AUTOCOMPACT_PCT_OVERRIDE staying in effect in a running session after it is removed from settings.json 
 Fixed the Agent tool's effort parameter being ignored for named teammates in agent teams 
 Fixed /auto-mode-setup ignoring recent auto mode denials when it scans a project for rules to suggest; it may now offer allow rules from them, and you review each before it's saved 
 Fixed a false "Couldn't save this change" warning after adding a permission rule or directory in a subfolder or worktree whose own .claude/settings.local.json is unreadable or malformed 
 Fixed cloud sessions telling Claude to run a network proxy check after a failed request, which auto mode then blocked 
 Fixed headless rewind and fork going ahead while a message sent right after a model change still waited on it 
 Fixed Claude not being told when a background task was stopped while a cloud session was restarting 
 Fixed /team-onboarding reporting a guide as shared on Team and Enterprise plans when the server refused the upload 
 Fixed panels and questions being cut off at the prompt in fullscreen, /help , history search and the background tasks list losing rows or titles in short windows, and tables wrapping in dialogs 
 Fixed resumed sessions showing "Rejected" or "Declined" for edits, questions and plans that were cut off when the session ended 
 Fixed /passes showing the wrong number of passes after a server error, and offering usage credits for sharing when no guest passes are left 
 Fixed claude --help output being cut short when piped to another program 
 Fixed /terminal-setup turning on "Use Option as Meta key" in Terminal.app on macOS 27, and tips there suggesting Option+Enter instead of Shift+Enter 
 Self-hosted runner: Fixed setup failing on Git LFS repositories cloned through Anthropic-managed git; sessions now start on pointer files, and git lfs pull fetches the content 
 Fixed sessions on self-hosted environments not starting from a git remote with an SSH host alias, GitHub SSH certificates or a GHE.com SSH user; an unresolved alias's error gives two git commands 
 Fixed remote MCP servers in self-hosted runner sessions staying without tools, or (over https) disconnected, after a timeout or network error 
 Fixed self-hosted runner sessions being shown as having stopped responding while Claude Code was still starting 
 Fixed Code Mode keeping in memory every large text file that code read, and memory growing each time a background subagent was woken 
 Fixed Code Mode stopping a script at its ten-minute limit while an MCP form, an MCP link prompt or a prompt that always asks was waiting for an answer 
 Fixed Code Mode scripts receiving a "moved to the background" message as data from most MCP calls over two minutes: the script now waits up to ten minutes, then gets an error 
 Fixed mods that list only some tools silently turning Code Mode off; such a mod no longer keeps it off, so use managed settings for that 
 Fixed Code Mode ignoring an MCP tool's request to end the turn when the tool was called from a script that Claude waits for 
 Fixed a Code Mode script's let x; keeping the value that an earlier script gave x 
 Fixed a Code Mode script's call with no argument failing with a missing-parameter error on tools that need none 
 Fixed Code Mode scripts losing access to tools through tools in sessions with more than 4,096 tools 
 Fixed the /code-review findings card often showing "high" for a review that ran at medium, on most models 
 Fixed key hints in permission prompts, questions, /model and /rewind ignoring keybindings.json 
 Fixed auto-scroll, the PR status badge, the auto-compact warning and the ultracode tag not following the /config switches that control them in a running session 
 Fixed a custom cancel key not working in /add-dir , /tui feedback and the save-workflow form 
 Fixed arrow keys in the save-workflow form moving the selection in the workflow view behind it 
 Fixed /config saying nothing, or "dismissed", after changing many settings 
 Fixed Read and @-mentions showing one line too many for files that end in a newline 
 Fixed /status not naming the model that opusplan and haiku use in plan mode 
 Fixed claude doctor advising a Keychain unlock inside a macOS sandbox, where unlocking can't help 
 Fixed the "Jump to bottom" pill staying hidden after copying text and scrolling away, the row under it going blank when its label changed, and quick PageUp presses scrolling too far in fullscreen 
 Fixed a screen update sometimes being skipped when memory is low 
 Fixed long code blocks losing a blank line and repeating another in scrollback 
 Fixed prompt suggestions sometimes showing placeholder text such as _(no suggestion)_ 
 Fixed the line about earlier messages on resume blaming a damaged file when the file was intact 
 Fixed characters disappearing from the prompt when its text held a color code that sets several styles and a keyword or command was highlighted 
 Fixed /rename and UserPromptSubmit hook titles in claude remote-control sessions not showing on claude.ai and mobile 
 Fixed the Remote Control diff listing a file twice when the branch renamed it and it was then edited 
 Improved the automatic clean-up of old sessions on computers with managed settings 
 Improved /tui and other in-place restarts to wait briefly for a login refresh, so they are less likely to sign you out 
 Improved memory use in long sessions that edit many files, and in long Claude Desktop sessions on macOS and Linux with many large MCP tool results 
 Windows: Improved start-up and the first search on PCs where Claude Code's search program starts slowly 
 Improved auto mode's handling of a short reply such as "yes" to Claude's question when telemetry is off, behind a gateway to the Anthropic API, or on Microsoft Foundry 
 Improved memory use of idle Claude Desktop and SDK sessions after a long turn, and after --resume or --continue of a session that holds screenshots or large tool results 
 Improved how fast a Claude Desktop Code session with Remote Control on is ready for the next message after an answer 
 Improved cloud sessions to retry plugins that failed to download at startup 
 Improved Code Mode: 

[... truncated for safety ...]

</details>