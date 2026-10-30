---
id: inbox_6dbf1356
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2251-claude-code-releases-v2-1-314-1c6c]]"
title: "v2.1.314"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.314
source: claude-code-releases
published_at: 2026-10-30T01:06:26+00:00
fetched_at: 2026-10-30T22:56:01.122720+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.314 新增禁止寫入工作目錄外的設定，並修了一大批閘道、Bedrock、MCP 與 TUI 的問題。 **Why** 企業與 CI 環境需要更嚴格的寫入邊界與政策控管，同時多種雲端/閘道組合會讓 session 反覆失敗。 **How** 新增 `permissions.blockWritesOutsideWorkingDirectories` 讓 Write、Edit、NotebookEdit 在任何權限模式下都拒絕工作目錄外的路徑；遇到 effort 上限、被閘道拒絕的 beta header 或 tool_reference 時，改為降級或移除後自動重試。 **What** Claude Code v2.1.314：Claude apps gateway upstream 新增 IdP `groups` 篩選與 Bedrock `guardrail_trace`；VS Code 與 Claude Desktop Code tab 新增閒置壓縮（200K+ token 對話閒置後先摘要）；PreCompact hook 輸出上限 10,000 字元；`claude -p` 啟動失敗改為輸出錯誤並以 exit 1 結束；`claude-opus-4.8` 這類帶點號的 model ID 能被正確辨識；另有大量 vim mode、resume、Remote Control 修正。"
key_points:
  - "新增 permissions.blockWritesOutsideWorkingDirectories：Write/Edit/NotebookEdit 在所有權限模式下都拒絕工作目錄外路徑"
  - "Claude apps gateway 新增 upstream 的 IdP groups 篩選（failover 時同樣適用）與 Bedrock guardrail_trace 記錄"
  - "VS Code 與 Claude Desktop Code tab 新增 idle compaction；PreCompact hook 輸出截斷至 10,000 字元，避免 compaction 失敗或重複"
tags: [claude-code, release-notes, permissions, gateway, bedrock]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.314

Claude Code v2.1.314 新增禁止寫入工作目錄外的設定，並修了一大批閘道、Bedrock、MCP 與 TUI 的問題。

**Why** 企業與 CI 環境需要更嚴格的寫入邊界與政策控管，同時多種雲端/閘道組合會讓 session 反覆失敗。

**How** 新增 `permissions.blockWritesOutsideWorkingDirectories` 讓 Write、Edit、NotebookEdit 在任何權限模式下都拒絕工作目錄外的路徑；遇到 effort 上限、被閘道拒絕的 beta header 或 tool_reference 時，改為降級或移除後自動重試。

**What** Claude Code v2.1.314：Claude apps gateway upstream 新增 IdP `groups` 篩選與 Bedrock `guardrail_trace`；VS Code 與 Claude Desktop Code tab 新增閒置壓縮（200K+ token 對話閒置後先摘要）；PreCompact hook 輸出上限 10,000 字元；`claude -p` 啟動失敗改為輸出錯誤並以 exit 1 結束；`claude-opus-4.8` 這類帶點號的 model ID 能被正確辨識；另有大量 vim mode、resume、Remote Control 修正。

### 重點
- 新增 permissions.blockWritesOutsideWorkingDirectories：Write/Edit/NotebookEdit 在所有權限模式下都拒絕工作目錄外路徑
- Claude apps gateway 新增 upstream 的 IdP groups 篩選（failover 時同樣適用）與 Bedrock guardrail_trace 記錄
- VS Code 與 Claude Desktop Code tab 新增 idle compaction；PreCompact hook 輸出截斷至 10,000 字元，避免 compaction 失敗或重複

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.314)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added permissions.blockWritesOutsideWorkingDirectories : Write, Edit and NotebookEdit refuse paths outside the working directories in every permission mode 
 Added an optional groups list to Claude apps gateway upstreams: only developers in the listed IdP groups are sent to that upstream, on failover too 
 Added guardrail_trace to Claude apps gateway Bedrock upstreams, to log which Amazon Bedrock guardrail filter fired on a request, without the matched text 
 Added idle compaction to VS Code and Claude Desktop's Code tab: a 200K+ token conversation left idle is summarized, and the summary is used on your next message if the prompt cache has expired 
 Fixed sessions failing turn after turn with "Invalid effort level" when an organization's admin caps a model's effort: Claude Code now lowers the effort, retries, and says which level it uses 
 Fixed claude -p exiting with code 0 and no output when startup failed; it now prints the error and exits 1 
 Fixed Bedrock sessions with many images failing every turn and /compact with "400 Input is too long." instead of removing older images and compacting 
 Fixed Microsoft Foundry sessions failing when the resource has no deployment for the default Sonnet, Opus or Haiku model: Claude Code now falls back to an older model of that family 
 Fixed repeated refused requests behind a gateway that doesn't accept tool search's tool_reference blocks: the request is sent again once without tool search, and the session remembers 
 Fixed TLS connections failing with UNABLE_TO_GET_ISSUER_CERT when the system certificate store holds a renewed root certificate that is cross-signed with its predecessor 
 Fixed MCP servers that also work without sign-in showing "needs authentication" after their stored sign-in stopped working; they are now used signed out 
 Fixed claude mcp logout reporting success when the MCP sign-in was not removed, for example while the macOS keychain is locked over SSH 
 Fixed extra sign-in renewals when several sessions share an Anthropic profile login and the credentials lock is busy 
 Fixed claude ultrareview and claude remote-control asking the workspace trust question in a CI job that has a terminal; with CI set they now refuse an untrusted folder at once 
 Fixed an administrator's TLS trust settings in managed settings not being applied in Claude Desktop sessions 
 Fixed model switching being refused on machines with managed plugin settings when one of your own --plugin-dir or --plugin-url plugins had a broken manifest or failed to download 
 Fixed the Bedrock and Vertex model upgrade offer coming back at every start when managed settings pin the model 
 Fixed forceRemoteSettingsRefresh set only in remote managed settings no longer applying once the stored copy had expired, which let sessions start without policy when the server could not be reached 
 Fixed "Continue automatically at usage limit" continuing more than three times without a prompt from you when a task restarted itself between waits (a /goal check-in, a background or scheduled task) 
 Fixed background and cloud sessions started with Ultracode turning it back on at their next start after it had been switched off 
 Fixed the last broken reply and its retry prompts staying in the conversation after Claude gave up on a tool call that could not be parsed 
 Fixed a PreCompact hook with very large output making compaction fail or repeat; each hook's output is now cut at 10,000 characters 
 Fixed background diff refreshes briefly taking the repository's index lock, which could make a git command run at the same moment fail with "Unable to create '.git/index.lock': File exists" 
 Fixed markdown tables jumping between grid and stacked layouts on half-typed rows while streaming, and long tables falling back to raw pipes 
 Fixed the /resume picker showing the text of CLAUDE.md or CLAUDE.local.md as a session's title when the session only ran slash commands 
 Fixed /btw answering from the main conversation when asked from a subagent's open transcript 
 Fixed pasting an image over SSH to a Linux machine doing nothing silently; the prompt now says to copy the file over and paste its path 
 Fixed claude remote-control sessions that failed to start when the session service was slow for a moment: the worker's registration is now retried with growing waits 
 Fixed model switches over Remote Control that take over 8 seconds getting a "still pending" error instead of the final result 
 Fixed the sandbox.excludedCommands setting description saying listed commands always run outside the sandbox; it now says every command in a call must match an entry 
 Fixed shell and MCP calls that auto mode, a deny rule or a PreToolUse hook blocked, or that otherwise did not run, reading as if they ran in a collapsed tool group 
 Fixed sandbox protections not applying to a worktree entered by claude -p --resume or --continue 
 Fixed hooks matching Bash not running on shell commands started by the Monitor tool; such hooks can block or ask, but not approve or rewrite those commands 
 Fixed a settings file excluded with --setting-sources still supplying some settings, such as auto mode rules and saved permission consents 
 Fixed auto mode reporting a call as blocked, and listing it in /permissions , when its safety check gave no verdict 
 Fixed a Claude apps gateway Vertex upstream hanging for minutes when a Google token endpoint accepts the connection and never answers 
 Fixed the Claude apps gateway's start-up warning for a deprecated Claude Desktop key that it still serves as written saying "stops being accepted" after the key's end date 
 Fixed /upgrade opening the browser and starting a new login for plans billed through the App Store or Google Play; it now says where to change the plan 
 Fixed --resume , and rewinding past a switch to another model after a refusal, moving a session on a model name Claude Code doesn't recognize to a different model 
 Fixed requests failing when a gateway or cloud provider refuses one of Claude Code's beta headers by name: the request is sent again without it 
 Fixed model IDs spelled with a dot behind an LLM gateway, such as claude-opus-4.8 , being treated as an older model with the wrong context window, output limit, effort, thinking mode and cost 
 Fixed Remote Control clients showing a stray "Compacted (ctrl+o to see full summary)" row after /compact 
 Fixed the cloud sessions tip and the Remote Control idle notice showing when an organization's policy turns those features off 
 Fixed a resumed claude.ai cloud session making a model call nobody asked for when the previous worker stopped just after receiving a new chat's files 
 Fixed WebFetch in Cowork cloud sessions silently dropping a PDF's text past 100,000 characters; it now says how much was unread and where to read on 
 Fixed Claude being told only that a command was declined after you stopped it with Esc or Stop in a cloud session or the IDE; it now also hears that the command may have run 
 Fixed blank lines at the top of a code block disappearing when the code block opens a quote 
 Fixed a blank line appearing above some ⎿ rows in the transcript view (Ctrl+O) 
 Fixed vim mode dw , dW , yw and yW carrying on past the end of the line, and made w and W stop on empty lines 
 Fixed x and Enter in the agent panel sometimes acting on the wrong agent when another agent started or finished 
 Fixed pasted text and dragged-in files being lost in Claude's question dialog unless the "Other" row had focus 
 Fixed pasted text being lost when a row in the prompt footer was selected 
 Fixed vim mode p over a character selection ignoring whether the yanked text was whole lines 
 Fixed vim mode aw and iw taking the line break at the end of a line 
 Fixed ↓ selecting footer items hidden by the ? help menu, the command list or a paste hint 
 Fixed Esc on a command's panel, such as /btw , also interrupting the subagent whose transcript is open 
 Fixed the welcome header in fullscreen mode showing the session's model while viewing a subagent or teammate that runs on a different model 
 Fixed the fullscreen transcript being left mid-conversation after "Restore conversation" in the rewind menu while scrolled up 
 Fixed a rare case where a deleted session could reappear in the resume list as an almost empty entry 
 Fixed prompts containing tags such as or not being acknowledged to a local stream-json host 
 Fixed sessions staying untitled when the first prompt failed (for example on a usage limit) and the conversation continued afterward 
 Fixed the skill file watcher checking every removed skill kept in ~/.claude/skills/.trash , which added file system load that grew with each removal 
 Fixed the session name from /rename disappearing while Claude asks for permission or a plan decision, so side-by-side sessions stay identifiable 
 Fixed background sessions that fail to start being reported as a deleted daemon binary when the binary is still on disk 
 Fixed the tip and idle reminder about push notifications appearing when the push settings in /config are hidden or your organization has turned off Remote Control 
 Fixed ~/.claude/skills/.trash and ~/.claude/plugins/.trash growing without limit: each now holds about 1024 entries, whatever cleanupPeriodDays says 
 Fixed the Bash edit diff listing a whole file as changed when a CRLF file under git's line-ending conversion was re-saved unchanged or had one line edited 
 Self-hosted runner: Fixed an idle session moving to another runner instead of pausing when the runner's request to pause it lost its connection before Anthropic answered 
 Improved memory use in long headless and SDK turns that run many subagents: the parent session no longer keeps each subagent's tool results until the turn ends 
 Improved prompt history: Ctrl+R now matches text inside collapsed [Pasted text] pills 
 Improved the /design-sync upload prompt to show the folder, the project and the files it will upload or delete 
 Improved /permissions review tab, now called Recently blocked: the footer says what Esc will do with marked rows 
 Improved auto mode's blocked calls: messages name the command, say Claude may retry and auto mode checks again, and point to /permissions to review 
 Improved permission prompts: a long reason takes fewer rows, so it pushes the command being approved off the screen on fewer terminals 
 Improved the cloud session error shown while a request refused for your claude.ai login is still being retried: it now also suggests claude auth login 
 Improved the behavior of stored claude.ai, Team, and Enterprise logins when MDM and remote settings differ on base URL or apiKeyHelper 
 Improved /config in agent view to say how to stop agent view opening by default 
 Improved session auto-titles: a session that starts with a skill or a prompt-based command such as /security-review now gets a title from it instead of staying untitled 
 Improved --resume speed and memory use on damaged transcripts 
 Improved /context speed in sessions with ten thousand or more MCP tools 
 Self-hosted runner: Improved the error shown when a session's branch isn't on the git remote: it now covers a never-pushed branch, says how to fix each case, and no longer suggests retrying 
 Updated the /claude-api skill: its Datadog setup for API tracing now sends the dd-llmobs-enabled: true header, as the Console does, and its ant install instructions drop the outdated macOS xattr step 
 Updated the bundled dataviz skill to advise printing y-axis tick labels in full under 10,000, and horizontal ones in full under a million where they fit 
 Updated the bundled dataviz skill to answer donut and pie chart requests with ranked bars or a segmented bar that prints its values 
 Changed Claude's file tools to ask before editing the local copy of your organization's server-managed settings, as they do for your settings files 
 Changed /ultrareview to check workspace trust before it runs git, as claude ultrarevie

[... truncated for safety ...]

</details>