---
id: inbox_5ca6c3e8
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2316-claude-code-releases-v2-1-326-b0e7]]"
title: "v2.1.326"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.326
source: claude-code-releases
published_at: 2026-11-16T22:11:05+00:00
fetched_at: 2026-11-17T23:20:47.402420+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版以修 bug 與補提示為主，讓權限、登入、MCP 與 /rewind 等日常操作更不容易出錯。 **What** Claude Code v2.1.326。新增：agent teams 開啟時可使用 Code Mode、對不完整的 --allowedTools/--disallowedTools/--tools 值顯示啟動警告、OTEL_RESOURCE_INCLUDE_HOST（預設關閉）、/status 顯示功能被關閉的原因。修正：設定檔巢狀超過 64 層會丟棄並警告、/rewind 在檔案變更無法追蹤時顯示「Code changes unknown」、compaction 在 Bedrock/Vertex/Foundry 上偶爾沒做摘要、Vertex AI 圖片過多時卡在 30 MB 的 400 錯誤，以及多項 MCP、/login、/privacy-settings 問題。"
key_points:
  - "新增 Code Mode 可在 agent teams 開啟時使用；已開啟者，帶 teams 的 session 預設進入 Code Mode"
  - "設定檔巢狀超過 64 層的值會被丟棄並警告；mid-session 存檔出錯的設定檔現在會點名警告，不再靜默略過"
  - "Vertex AI 圖片過多導致 30 MB 請求過大的 400 錯誤，現在會 compact 後重試；max_tokens 超限時改用 Anthropic API 回報的上限重試"
tags: [claude-code, release-notes, mcp, permissions, code-mode]
topics: [agents.coding_agents, agents.mcp]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.326

Claude Code 這版以修 bug 與補提示為主，讓權限、登入、MCP 與 /rewind 等日常操作更不容易出錯。

**What** Claude Code v2.1.326。新增：agent teams 開啟時可使用 Code Mode、對不完整的 --allowedTools/--disallowedTools/--tools 值顯示啟動警告、OTEL_RESOURCE_INCLUDE_HOST（預設關閉）、/status 顯示功能被關閉的原因。修正：設定檔巢狀超過 64 層會丟棄並警告、/rewind 在檔案變更無法追蹤時顯示「Code changes unknown」、compaction 在 Bedrock/Vertex/Foundry 上偶爾沒做摘要、Vertex AI 圖片過多時卡在 30 MB 的 400 錯誤，以及多項 MCP、/login、/privacy-settings 問題。

### 重點
- 新增 Code Mode 可在 agent teams 開啟時使用；已開啟者，帶 teams 的 session 預設進入 Code Mode
- 設定檔巢狀超過 64 層的值會被丟棄並警告；mid-session 存檔出錯的設定檔現在會點名警告，不再靜默略過
- Vertex AI 圖片過多導致 30 MB 請求過大的 400 錯誤，現在會 compact 後重試；max_tokens 超限時改用 Anthropic API 回報的上限重試

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.326)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added support for turning on Code Mode while agent teams are enabled; if you already turned it on, sessions with teams on now start in Code Mode 
 Added a startup warning when an --allowedTools , --disallowedTools or --tools value has an entry that doesn't look like a complete rule 
 Added a message explaining why MCP servers stop loading when an administrator adds managed-mcp.json during a session 
 Added a row to /status that says when your provider or an environment variable such as DISABLE_TELEMETRY turns features off 
 Added a note in /plugin and claude plugin list when a malformed plugin.json field such as author or homepage is ignored 
 Added Ctrl+O to show hidden startup notices 
 Added a hint in the empty prompt that says what to do after a request fails 
 Added an esc to stop footer hint in a subagent's view where Esc would stop it 
 Added OTEL_RESOURCE_INCLUDE_HOST to include host.name and host.id in OpenTelemetry resource attributes (off by default) 
 Added overflowX="scroll" on a mod's Box , and maxLines and wrap="clip" on its Text 
 Fixed cp of a file being refused when only its source was covered by an Edit deny rule 
 Fixed Bash commands that delete or overwrite files ( find -delete , cat a > b , sort -o ) being summed up in the transcript as a search or a read 
 Fixed a misleading "Dangerous rm operation" warning in the Bash permission prompt on some commands with no rm that Claude Code can't read reliably 
 Fixed background sessions losing the LLM gateway your shell exported after a crash, after a reopen from another folder, or when the background service lacks it: they now stop before any model request 
 Fixed the background service ending your own processes, such as an SSH login, when a process number on its list had been reused by another user's process 
 Fixed rules added in /permissions or at a main-conversation tool prompt, and /add-dir folders, looking saved when the settings file couldn't be written; the terminal now warns and names it 
 Fixed a failed MCP headersHelper , or one not run in an untrusted folder, making other sessions start without that server, for most servers with no stored OAuth refresh token 
 Fixed managed settings with certain key names stopping Claude Code from starting or affecting other managed files 
 Fixed settings files with values nested thousands of levels deep crashing Claude Code or applying only some of the time; values past 64 levels are now dropped with a warning 
 Fixed a settings file saved with an error mid-session being skipped silently; a warning now names the file 
 Fixed the subagent model set in managed settings not applying in Claude Desktop's Code tab; it now overrides your own, as in a terminal, unless those settings also pick a provider or gateway 
 Fixed sandboxed commands failing to start on Linux when the home or config directory is reached through a symlink into /net and sandbox settings deny reads of it 
 Fixed empty placeholder files, including .git/config.lock , sometimes being left in the project on Linux when Claude Code was stopped during a sandboxed command 
 Fixed Up then Enter answering Yes at the folder trust prompt shown under an already trusted parent folder 
 Fixed an extra Enter at the end of setup accepting the offer to make auto mode the default 
 Fixed a message typed over the startup auto mode offer being lost, and its Enter accepting the offer 
 Fixed a note typed on a permission prompt being sent to Claude after Tab had hidden it 
 Fixed PreToolUse hooks in managed settings leaving no OpenTelemetry tool_decision event or permission_denials entry when they refused a direct tool call 
 Fixed letters typed over /sandbox or a delete question in /permissions moving the selection 
 Fixed resumed sessions losing recent turns after a crash when the previous turn ended with an empty reply 
 Fixed resumed sessions losing earlier conversation history when Claude Code ran low on memory 
 Fixed a re-sent file overwriting Claude's changed copy in Remote Control and cloud sessions on Linux with no feature flags loaded: the copy moves to a .kept- folder, or the new file isn't saved 
 Fixed a background session being killed and its request lost when you opened, stopped or removed the older session whose conversation it had resumed 
 Fixed claude purge hiding its prompts when stdout is redirected, where one unseen Enter could delete a project's data; they now show on the terminal 
 Fixed the spend limit menu removing the monthly limit without asking when Backspace and Enter were pressed as it opened 
 Fixed /rewind restoring only some files after running /branch twice while a slow backup copy was still running 
 Fixed /rewind saying "No code changes" when a shell command changed files it can't restore; a turn whose changes weren't tracked now reads "Code changes unknown" 
 Fixed /rewind : Esc now cancels its summary, its list shows more than one past prompt in fullscreen, and a long prompt no longer hides its warning about losing later file changes 
 Fixed Ctrl+C or Ctrl+D twice in /skills quitting Claude Code and dropping changes; it now saves and closes the panel 
 Fixed the usage limit menu erasing your draft and opening while you were typing 
 Fixed pasted text and images being dropped when ↑ recalls a draft cleared with Esc Esc 
 Fixed an edited typed answer to Claude's question sending the old text when you moved on without pressing Enter 
 Fixed going back to a question you answered from its list putting the cursor on the first option, where Enter replaced your answer 
 Fixed /feedback and /bug sending the report when you typed a space on the confirmation screen, and losing the typed report after Ctrl+O or Ctrl+Z 
 Fixed a prompt typed after --add-dir , --allowedTools or another list option being dropped without a message 
 Fixed /plan ignoring the description when plan mode was already on 
 Fixed valid PDFs being dropped from the conversation after the API rejected a different PDF read in the same batch 
 Fixed a session ending after a single failed memory allocation while drawing the screen 
 Fixed compaction on Bedrock, Vertex and Foundry, and with telemetry turned off, sometimes replying to one of your messages instead of summarizing, or leaving Claude's last reply out of the summary 
 Fixed image-heavy sessions on Vertex AI getting stuck on a 400 error about the request size exceeding a 30 MB limit, instead of compacting and retrying 
 Fixed an error when max_tokens exceeded the model's limit: Claude Code now retries the request with the maximum the Anthropic API reports 
 Fixed grep in the Bash tool silently skipping some text files 
 Fixed a crashed Node or Python hook showing only the first line of its stack trace; the error is now shown, and Ctrl+O shows up to 10,000 characters of the output 
 Fixed /goal clear or a new /goal not sticking when typed while Stop hooks were running and background work was still in progress 
 Fixed the automatic session recap being sent after a reply billed to usage credits; /recap still works 
 Fixed auto mode staying on its local classifier, which counts toward usage, because of a stale saved value, such as one from an older Claude Code 
 Fixed "Sign in with your Console account" in /login replacing your Claude subscription login when the browser sign-in used your Claude plan instead of a Console organization 
 Fixed /login ending on "Login successful" while an approved ANTHROPIC_API_KEY was still used; it now says requests still use the key 
 Fixed "Not logged in" staying after turning on the API key in /config ; "Not logged in", /login and /status now name an unused ANTHROPIC_API_KEY 
 Fixed claude auth logout leaving credentials behind, and token refresh failing, when only a Console profile's credentials are on a drive that rejects folder timestamps 
 Fixed a past conversation resumed from agent view being sent on the background service's sign-in when the service doesn't have the terminal's API key or token 
 Fixed model requests failing on a one-off authentication error (401) in Claude Desktop's Code tab: they are now sent once more first 
 Fixed forceLoginOrgUUID and forceRemoteSettingsRefresh startup errors telling you to sign in again when a network block page (HTTP 403) was the cause 
 Fixed claude auth login not showing a pasted sign-in code, so a wrong paste couldn't be seen or corrected before Enter 
 Fixed /login and claude setup-token showing nothing after you submit a pasted code; they now show "Finishing sign-in..." 
 Fixed Esc doing nothing while the first-run sign-in waits for the browser or a pasted code; it now goes back one screen 
 Fixed /logout in fullscreen mode exiting without leaving the logged-out message on screen 
 Fixed the shell prompt being drawn over the last screen after quitting with Ctrl+C or Ctrl+D at a sign-in or first-run step 
 Fixed Ctrl+C twice doing nothing on the first-run theme choice, and freezing the terminal on setup screens or a background session at its startup question 
 Fixed your OFF answer to the updated terms being replaced when keys were typed while it was saving, at startup and in /privacy-settings 
 Fixed the /privacy-settings toggle sometimes saving the opposite of what the screen showed on a quick double press, changing your setting on keys pressed after Esc, and not saying when a save failed 
 Fixed /privacy-settings saving your choice on the wrong account after signing in to a different account in another terminal 
 Fixed /privacy-settings saying "set to true" when you picked OFF right after ON 
 Fixed skills and slash commands failing to load in Code Mode under auto mode when an inline ! command needs approval; Claude is now asked to run it 
 Fixed background subagents started in Code Mode failing when they preload a skill with an inline ! command 
 Fixed mods being unable to use Bash, Read and other tools through $.tool.call and $.tool.check in Code Mode 
 Fixed parallel MCP tool calls reading another call's saved result when two long results arrived in the same millisecond ( #105138 ) 
 Fixed tool search sometimes loading another MCP server's tool when asked for a tool by its exact name; you may be asked again for that tool 
 Fixed MCP prompts disappearing when two servers have nearly identical names 
 Fixed a tool call to an MCP server that an SDK host had just removed reconnecting to it, or reporting that it needs authentication 
 Fixed Claude not being told that a remote MCP server's question was declined when the server then failed the tool call 
 Fixed MCP tools with a root anyOf or oneOf showing Claude only the first branch's form of an argument; text such as 42 can now arrive as a number where another branch takes one 
 Fixed Claude not being told when an approved MCP resource tool was unavailable after a cloud session's worker was replaced 
 Fixed /mcp not showing why a local (stdio) MCP server failed to start 
 Fixed Esc doing nothing while an MCP server reconnects: Esc, or Ctrl+C pressed twice, now closes the wait and the reconnect continues in the background 
 Fixed Enable in /mcp showing no progress for a slow server, and a second Enter disabling it again 
 Fixed claude mcp add-json answering most mistakes with "Invalid configuration: : Invalid input"; it now says what to change 
 Fixed the Ctrl+C hint on a background MCP task's question saying "cancel" when the second press leaves the question to answer later 
 Fixed pressing c to copy an MCP sign-in URL leaving a stray c in the paste field 
 Fixed Tab and Shift+Tab not moving between fields in an MCP server's input form, and a required field there keeping its tick after being emptied 
 Remote Control: Fixed a session disconnecting mid-reply when the server was briefly unavailable 
 Remote Control: Fixed the QR code in /remote-control being cut off in short terminal windows such as 80×24 
 Remote Control: Fixed terminal sessions showing as idle on your phone while background subagents were still running

[... truncated for safety ...]

</details>