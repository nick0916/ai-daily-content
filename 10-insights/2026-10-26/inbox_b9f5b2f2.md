---
id: inbox_b9f5b2f2
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-claude-code-releases-v2-1-311-0c09]]"
title: "v2.1.311"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.311
source: claude-code-releases
published_at: 2026-10-26T21:51:23+00:00
fetched_at: 2026-10-27T01:31:02.016541+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 2.1.311 以大量修正為主，補強長 session、MCP、subagent 與 Remote Control 的穩定性。 **What** Claude Code v2.1.311：標準 context session 的請求超過 200K tokens 時，改為自動 compact 並繼續，不再停在「Usage credits required for 1M context」；修正 CLAUDE.md 含超長清單項目造成的啟動與讀寫凍結、subagent 無法使用較晚連線的 MCP server 工具、SubagentStop hook 每分鐘約觸發兩次。ultrathink 在 Opus 5.5、Sonnet 5.5、Haiku 5.5 與 Fable 5.1 上（經 Anthropic API）改為以 xhigh effort 執行該 turn。另新增 self-hosted-runner 的 --hold-idle-file 與 --max-hold-min；Bedrock、Mantle、Vertex、Foundry 改從 downloads.claude.ai 的簽章檔載入模型設定，可用 CLAUDE_CODE_MODEL_CATALOG=off 關閉。"
key_points:
  - "標準 context session 超過 200K tokens 時不再報錯停止，改為自動 compact 後繼續"
  - "ultrathink 在 Opus 5.5 / Sonnet 5.5 / Haiku 5.5 / Fable 5.1 上讓該 turn 以 xhigh effort 執行；只在關鍵字真能提高 effort 時才顯示彩虹色"
  - "修正 MCP 與 subagent 相關問題：subagent 可用較晚連線的 MCP 工具、MCP 無回應時中斷不再卡到逾時、SubagentStop hook 不再重複觸發"
tags: [claude-code, release-notes, ultrathink, compaction, mcp]
topics: [agents.coding_agents, agents.mcp, foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.311

Claude Code 2.1.311 以大量修正為主，補強長 session、MCP、subagent 與 Remote Control 的穩定性。

**What** Claude Code v2.1.311：標準 context session 的請求超過 200K tokens 時，改為自動 compact 並繼續，不再停在「Usage credits required for 1M context」；修正 CLAUDE.md 含超長清單項目造成的啟動與讀寫凍結、subagent 無法使用較晚連線的 MCP server 工具、SubagentStop hook 每分鐘約觸發兩次。ultrathink 在 Opus 5.5、Sonnet 5.5、Haiku 5.5 與 Fable 5.1 上（經 Anthropic API）改為以 xhigh effort 執行該 turn。另新增 self-hosted-runner 的 --hold-idle-file 與 --max-hold-min；Bedrock、Mantle、Vertex、Foundry 改從 downloads.claude.ai 的簽章檔載入模型設定，可用 CLAUDE_CODE_MODEL_CATALOG=off 關閉。

### 重點
- 標準 context session 超過 200K tokens 時不再報錯停止，改為自動 compact 後繼續
- ultrathink 在 Opus 5.5 / Sonnet 5.5 / Haiku 5.5 / Fable 5.1 上讓該 turn 以 xhigh effort 執行；只在關鍵字真能提高 effort 時才顯示彩虹色
- 修正 MCP 與 subagent 相關問題：subagent 可用較晚連線的 MCP 工具、MCP 無回應時中斷不再卡到逾時、SubagentStop hook 不再重複觸發

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.311)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added --hold-idle-file and --max-hold-min to self-hosted-runner , to keep an idle session while your host reports processes it left running 
 Added a tip for the Explanatory output style, shown when you ask Claude for explanations 
 Fixed long freezes at startup and after reading or editing files when a CLAUDE.md file holds a very long list item 
 Fixed interrupting Claude not taking effect until a timeout while an MCP server had not answered a resource read or a skill was still downloading 
 Fixed standard-context sessions stopping with "Usage credits required for 1M context" when a request ran over 200K tokens; Claude Code now compacts the conversation and continues 
 Fixed Write and Edit stalling for up to 5 seconds after they ran, and reporting 0 lines changed, when changing thousands of lines in a file 
 Fixed subagents being unable to use MCP tools from servers that finish connecting after the subagent starts 
 Fixed Claude seeing stale MEMORY.md and CLAUDE.md content right after automatic compaction when those files were edited earlier in the session 
 Fixed claude -p and SDK sessions saving transcript messages out of order or keeping messages that were taken back 
 Fixed SubagentStop hooks running about twice a minute for each running subagent instead of once when it finishes 
 Fixed the @ file picker ignoring .ignore / .rgignore negation rules that re-include git-ignored files 
 Fixed a subagent's isolated worktree being removed while a background subagent it started was still working in it 
 Fixed background agents in auto mode that wait on their own shells starting a new main conversation turn on every wake 
 Fixed the Bash tool description claiming the working directory always persists between calls 
 Fixed the environment block naming a shell commands don't run in, such as fish when the Bash tool uses zsh 
 Fixed claude mcp add , claude mcp remove and /mcp naming the current folder instead of the project entry in ~/.claude.json that holds a local-scope server when run below a repository root 
 Fixed claude mcp list and claude mcp get showing the error code twice on failed-connection lines (for example ENOENT: ENOENT: ... ) 
 Fixed Remote Control sessions staying on "Connecting" for about two minutes when a network proxy blocks a startup request 
 Fixed messages that Claude sends to a cloud or Remote Control session appearing as your own message in the Claude mobile apps 
 Fixed Claude not being told the cause when a file attached to a message sent over Remote Control or to a cloud session could not be saved because the disk was full, or that a message's attachments past the first 20 were left out 
 Fixed WebFetch and WebSearch hanging on a stalled response in Cowork cloud sessions; an unfinished request now fails after 300 seconds 
 Fixed a background session that crashed between turns not being restarted while it was attached, pinned, or had a scheduled task or wake-up set 
 Fixed the "background service did not respond" error suggesting the disabled claude daemon restart ; it now suggests claude daemon stop --any and says it ends background sessions 
 Fixed claude respawn starting the background service before reporting that no background session matches the id 
 Fixed /effort not warning about a prompt cache miss in plan mode when the plan model differs from the session model 
 Fixed /ide saying the VS Code extension was installed before the install finished or when it failed 
 Fixed the Write tool's file preview skipping rows and miscounting hidden lines when a line is wider than the terminal 
 Fixed ↑ in an agent's chat tab recalling a message that was still waiting to be delivered, so resending it sent a second copy 
 Fixed Cowork cloud sessions losing their connectors and most tools after a restart when a plugin or your settings named an agent ; Cowork cloud sessions now ignore that setting 
 Fixed agent teams sessions showing an empty task list when coming back with --resume , --continue , /resume or --session-id , including after /clear or a crash, and /branch writing to the original session's list 
 Fixed pasting text that mentions an image file, such as ! open /tmp/shot.png or /review look at /tmp/shot.png , attaching the image and dropping its path from the prompt 
 Fixed the feedback draft card showing its 1/2/0 and Esc shortcuts while the prompt has text, when those keys act on the prompt instead of the card 
 Fixed a lone backslash in quotes or brackets, like "\" or (\) , disappearing from Claude's responses 
 Fixed agent teammates compacting their history when DISABLE_COMPACT is set 
 Fixed the rewind menu offering "Summarize from here" and "Summarize up to here" when DISABLE_COMPACT is set 
 Fixed a finished /code-review , or another skill that runs in a sub-agent, running a second time when a cloud or background session restarts 
 Fixed long hidden thinking being cut off as idle on Google Vertex AI, Microsoft Foundry and Claude Platform on AWS, where the endpoint sends thinking progress updates 
 Fixed /ide saying it had installed the JetBrains plugin when nothing was installed 
 Fixed Claude Pro and Max subscribers being told to ask their admin when their subscription can't be used; the message now points to billing settings 
 Fixed the diff pane opening by itself after an edit in wide fullscreen terminals when it had nothing to show 
 Fixed /mcp showing a remote server as failed after "Clear authentication" when the server works without sign-in 
 Fixed /mcp showing "authenticated" for a remote server that Claude Code sends no credentials to 
 Fixed a --plugin-dir folder of plugins loading as one plugin when an empty .mcp.json was at its top 
 Fixed /usage never showing large prompt-cache misses under "What's contributing to your limits usage?" 
 Fixed status line links staying plain text in background sessions after you open them from a terminal that supports links 
 Fixed the /rewind confirmation saying the conversation "will be forked" when the later messages are removed from the conversation 
 Fixed the /rewind warning that wrongly said manual and Bash edits are never affected by a code restore 
 Fixed plan approval in screen reader mode sending feedback you had dismissed with Escape 
 Fixed Claude Code retrying requests the API marked not to retry, which could hold a turn for minutes or, in unattended retry mode ( CLAUDE_CODE_RETRY_WATCHDOG ), indefinitely 
 Linux: Fixed sandboxed Bash commands failing with bwrap: Can't create file when a --plugin-dir folder was also an added directory and permissions.blockReadsOutsideWorkingDirectories was on 
 Self-hosted runner: Fixed a session failing to start when a rate limit (HTTP 429, or a git wrapper that exits 75) blocks an added read-only repository; it now starts without that repository 
 Improved startup time for Pro and Max accounts by skipping two network requests on launches within an hour of the last check 
 Improved /teleport and claude --teleport to warn when a compacted cloud session loads from its last compaction, so the messages it summarized aren't in the local copy 
 Improved the messages shown when a background session's process exits: they no longer promise a restart that isn't coming, and they say how to resume the session 
 Improved artifacts with several views: Claude now routes each view on the link's #name and no longer says the address bar stays the same as you switch views 
 Improved shell commands that reach their timeout: the result now shows the output so far and says the command is still running in the background 
 Improved compaction: when the model's reply has no summary in it, Claude Code now usually asks for the summary once more before it replaces the conversation 
 Improved the Artifact tool's choice between a page and a document: explainers and visual or interactive work become artifact pages; documents are for writing people keep editing or pass around 
 Improved startup time for launches whose only arguments are options and their values, such as claude --model opus 
 Improved the "Connection dropped" API error: it now says where to look first (the proxy or gateway in use, else VPN or firewall; Anthropic API only, Bedrock, Vertex and Foundry are unchanged) 
 Improved screen reader mode: deleting a rule in /permissions says "Deleted allow rule ..." right away 
 Improved the message shown when a pasted sign-in code is refused: it now says the code may have expired or been used, and to sign in again 
 Improved Slack connector sends: Claude now checks a channel's topic for posting rules before messaging a channel you didn't name 
 Improved screen reader mode: Claude's questions are listed as "Questions: Color (answered), Pages", without arrows or symbols 
 Changed ultrathink in the interactive terminal to run its turn at xhigh effort on Opus 5.5, Sonnet 5.5, Haiku 5.5 and Fable 5.1 through Anthropic's API; typed while Claude is working, it raises the rest of that turn 
 Changed the ultrathink rainbow to appear only where the keyword can raise effort, and not when the word is quoted or part of a file path 
 Changed Ctrl+D in agent view to match the prompt: on an empty input, pressing it twice exits 
 Changed --output-format json and stream-json output to write DEL, C1 control and Unicode format characters inside strings as \uXXXX escapes; parsed values are unchanged 
 Changed model names and IDs to drop the [1m] suffix and its label on models where the suffix has no effect; the suffix is still accepted 
 Changed startup warnings about permission rules in settings files to show once per user until the rule changes 
 Changed /code-review to tell Claude to put the effort level first and use max only when asked 
 Changed DISABLE_COMPACT in settings files and in a mod's $.env.set so they can only turn compaction off, not back on 
 Changed Claude Code on Bedrock, Mantle, Vertex, and Foundry to load model settings from a signed file on downloads.claude.ai; set CLAUDE_CODE_MODEL_CATALOG=off to turn this off 
 Changed sessions that set CLAUDE_CODE_SYNC_SKILLS with feature-flag fetching off to reuse a claude.ai skills list up to 10 minutes old that another session on the machine fetched 
 Changed clicks on scrollbar arrows and bars in fullscreen lists to act when the mouse button is released, so moving off the scrollbar before letting go cancels the click 
 Changed claude purge to say it deletes data only on this computer, not anything stored by Anthropic 
 [VSCode] Added syntax coloring to code blocks in Claude's replies, in light, dark and high contrast dark themes 
 [VSCode] Added a "Running UserPromptSubmit hooks" spinner status and screen reader announcement for slow UserPromptSubmit hooks 
 [VSCode] Fixed custom skills and custom slash commands sent from the VS Code or JetBrains panel leaving out the open file or selected lines that ordinary messages include ( #102799 ) 
 [VSCode] Fixed the extension host freezing while the login shell ran its start-up files to read PATH on macOS and Linux 
 [VSCode] Fixed clicking an image in a tool result, or closing its preview, also opening the result's text in an editor tab 
 [VSCode] Fixed voice dictation continuing to record after a message was sent with the Send button; sending now stops dictation first, as pressing Enter already did 
 [VSCode] Changed the extension to start Claude Code sessions with DISABLE_TELEMETRY set while VS Code's telemetry setting is off, so they send no usage metrics or error reports and fetch no feature flags 
 [VSCode] Changed the session list side bar to load Web sessions when the Web tab is first opened, not at startup 
 [Cloud sessions] Fixed routines in Anthropic-hosted environments staying locked after their owner left the organization and rejoined; the owner can now turn them back on 
 [Cloud sessions] Fixed a failed routine API token delete or regenerate showing nothing if the edit dialog had already closed; it now shows an error toast 
 [Cloud sessions] Fixed cloud envi

[... truncated for safety ...]

</details>