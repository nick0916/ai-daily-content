---
id: inbox_355ac250
date: 2026-10-09
source_ref: "[[00-inbox/.../inbox_355ac250]]"
title: "v2.1.296"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.296
source: claude-code-releases
published_at: 2026-10-09T19:28:59+00:00
fetched_at: 2026-10-18T03:34:50.092779+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.296 發布。新增項目包含：subagent frontmatter 與 --agents 定義支援 autoCompactWindow，讓 subagent 比主對話更早 auto-compact；CLAUDE_CODE_WORKFLOW_SUBAGENT_MODEL 可讓所有 workflow agent 使用同一模型；CLAUDE_CODE_OVERLOADED_RETRY_MAX_DELAY_MS 可設定 529 overloaded 重試的最大退避延遲；Read 工具新增 allow_large 選項，可一次讀取超過一般大小限制的文字檔；Claude apps gateway 的 managed.policies[] 新增 code 鍵。安全面修復值得注意：managed-settings 中以 \"continue\": false 拒絕工具呼叫的 PreToolUse hook 原本只拒絕呼叫卻沒結束 turn；Bash 權限檢查曾自動核准某些指派 BASH_ARGV0 後使用它的指令，現在改為詢問；Edit 與 NotebookEdit 對非 UTF-8 檔案（Windows-1252、Shift-JIS、GBK）會替換所有非 ASCII 字元，現在改為拒絕此類編輯；secret redaction 補強。Windows 方面，超過約 1 KB 的 PowerShell 指令原本總是要求權限，現在 allow 規則與唯讀偵測可套用至 32 KB。另修復 Haiku 5.5 等只接受 adaptive thinking 的模型之 token 計數問題。"
key_points:
  - "subagent frontmatter 新增 autoCompactWindow；CLAUDE_CODE_WORKFLOW_SUBAGENT_MODEL 讓所有 workflow agent 共用單一模型"
  - "安全修復：BASH_ARGV0 指派後使用的指令不再被自動核准；Edit/NotebookEdit 對非 UTF-8 檔案不再替換全部非 ASCII 字元而是拒絕編輯"
  - "Windows PowerShell 指令的 allow 規則與唯讀偵測上限從約 1 KB 放寬至 32 KB"
tags: [claude-code, release-notes, subagents, permissions, windows]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.296

Claude Code v2.1.296 發布。新增項目包含：subagent frontmatter 與 --agents 定義支援 autoCompactWindow，讓 subagent 比主對話更早 auto-compact；CLAUDE_CODE_WORKFLOW_SUBAGENT_MODEL 可讓所有 workflow agent 使用同一模型；CLAUDE_CODE_OVERLOADED_RETRY_MAX_DELAY_MS 可設定 529 overloaded 重試的最大退避延遲；Read 工具新增 allow_large 選項，可一次讀取超過一般大小限制的文字檔；Claude apps gateway 的 managed.policies[] 新增 code 鍵。安全面修復值得注意：managed-settings 中以 "continue": false 拒絕工具呼叫的 PreToolUse hook 原本只拒絕呼叫卻沒結束 turn；Bash 權限檢查曾自動核准某些指派 BASH_ARGV0 後使用它的指令，現在改為詢問；Edit 與 NotebookEdit 對非 UTF-8 檔案（Windows-1252、Shift-JIS、GBK）會替換所有非 ASCII 字元，現在改為拒絕此類編輯；secret redaction 補強。Windows 方面，超過約 1 KB 的 PowerShell 指令原本總是要求權限，現在 allow 規則與唯讀偵測可套用至 32 KB。另修復 Haiku 5.5 等只接受 adaptive thinking 的模型之 token 計數問題。

### 重點
- subagent frontmatter 新增 autoCompactWindow；CLAUDE_CODE_WORKFLOW_SUBAGENT_MODEL 讓所有 workflow agent 共用單一模型
- 安全修復：BASH_ARGV0 指派後使用的指令不再被自動核准；Edit/NotebookEdit 對非 UTF-8 檔案不再替換全部非 ASCII 字元而是拒絕編輯
- Windows PowerShell 指令的 allow 規則與唯讀偵測上限從約 1 KB 放寬至 32 KB

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.296)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.296

What's changed 
 
 Added a code key to the Claude apps gateway's managed.policies[] : the same settings as cli , also applied in Claude Desktop's Code tab; beside desktop , it turns on Claude Desktop's gateway mode 
 Added autoCompactWindow to subagent frontmatter and --agents definitions, so a subagent can auto-compact earlier than the main conversation's window 
 Added CLAUDE_CODE_WORKFLOW_SUBAGENT_MODEL to run every workflow agent on one model while other subagents keep theirs 
 Added CLAUDE_CODE_OVERLOADED_RETRY_MAX_DELAY_MS environment variable to set a longer maximum delay for the backoff when retrying an overloaded (529) request 
 Added a note in /plugin on a plugin whose hooks are left out because another enabled plugin has the same name 
 Added an allow_large option to the Read tool so Claude can read a text file past the usual size limits in one call when it needs the whole file and the context has room 
 Fixed managed-settings PreToolUse hooks that deny a tool call with "continue": false , and managed prompt hooks that block one, refusing the call but not ending the turn 
 Fixed PostToolUse hooks in managed settings not applying updatedMCPToolOutput in some sessions 
 Fixed headless sessions starting a folder's .mcp.json or plugin MCP server that was switched off for that folder, after changing directory or reloading plugins 
 Fixed a Claude apps gateway that serves allowedProviders with "gateway" locking out laptops that name that gateway in user settings 
 Fixed a saved Claude apps gateway sign-in being ignored on machines whose managed settings set forceLoginMethod to gateway with no forceLoginGatewayUrl (regression in 2.1.295) 
 Fixed --teleport opening an empty conversation when the session's history could not be read 
 Fixed token counts for Haiku 5.5 and other models that take only adaptive thinking, which failed behind some gateways and were counted with budget thinking elsewhere 
 Fixed resumed subagents being told that the user rejected a tool call that a session shutdown had interrupted 
 Fixed hook output being altered when it contained text resembling a plugin hint tag 
 Fixed secret redaction in shared transcripts and debug logs missing some values that follow a key with no value, including in JSON written inside a shell string 
 Fixed a stray 52;c;... escape sequence printed on screen after copying in older VTE-based terminals such as MATE Terminal 
 Fixed toasts and notifications waiting unseen for as long as the /diff panel or dialog was open 
 Fixed Esc or an interrupt during a UserPromptSubmit hook or a mod's prompt.submit hook ending headless sessions, clearing the typed prompt, or letting the unchecked prompt through 
 Fixed SessionStart hooks of a plugin loaded after a headless session starts being skipped when a different plugin with the same name, or another spelling of it, had already run 
 Fixed claude self-hosted-runner printing misleading errors when registration is refused: it now names the org admin setting, or says a restarted on-demand runner needs a fresh work order 
 Fixed a self-hosted runner session's git fetch, pull and push failing while another session of the same repository starts on a runner with --capacity above 1 
 Fixed workflow scripts silently truncating results, agent options and other values nested deeper than about 20,000 levels, and deeply nested results writing huge task output files 
 Fixed a plugin's served $ methods running in the main session's working directory instead of the calling agent's, and ignoring the turn their calling hook holds 
 Fixed $.agent.register succeeding from a mod's hook that was still running after the mod was reloaded or removed; the call is now refused 
 Fixed $.http.fetch in mods refusing a HEAD request when the response declares a Content-Length over the 4 MiB body limit 
 Fixed claude plugin marketplace add , marketplace update and plugin install failing with an internal error for a marketplace named like constructor ; add now refuses such names clearly 
 Fixed a plugin secret named constructor or prototype being deleted by the next save of that plugin's options 
 Fixed cloud sessions skipping auto mode's checks on Claude in Chrome actions that a saved permission allows when their feature flags had not loaded 
 Fixed CLAUDE_CODE_RESUME_INTERRUPTED_TURN re-running a finished turn after a restart when an MCP tool result had ended that turn 
 Fixed Bash permission checks auto-approving some commands that assign the BASH_ARGV0 shell variable and then use it; these now prompt for approval 
 Fixed Edit and NotebookEdit replacing every non-ASCII character in files that are not valid UTF-8 (Windows-1252, Shift-JIS, GBK); such edits are now refused 
 Fixed a prompt sent just after ← being run twice, once unseen in the foreground, when the background service was slow to answer 
 Fixed a prompt sent while SessionStart hooks were still running vanishing when ← moved the session to the background; it is still not sent, but ↑ now brings it back 
 Fixed a late-loading plugin's SessionStart hook output reaching the new conversation after /clear in headless sessions 
 Fixed PowerShell commands not seeing variables that hooks write to CLAUDE_ENV_FILE (when the file holds only plain assignments) 
 Fixed Claude calling cloud sessions non-interactive and suggesting /mcp or claude mcp when an MCP server needs authentication 
 Fixed /code-review ending on a raw JSON array in cloud sessions, the Agent SDK and IDE integrations; the findings now print as a numbered list 
 Fixed auto mode occasionally refusing one update to your own artifact, saying its sharing had changed when it had not 
 Fixed skills synced from claude.ai never finishing their install, and being downloaded again at every sync, when several sessions share a config directory 
 Fixed a plugin synced from claude.ai being disabled when the marketplace dependency it declares was also synced from claude.ai 
 Fixed a startup hang on macOS when plugin paths copied from a Linux machine pointed under /home 
 Fixed the Workflow tool refusing script files with CRLF line endings, such as files checked out on Windows 
 Fixed OpenTelemetry tool_result events missing git_commit_id after git commit -q or git -C &lt;dir&gt; commit 
 Fixed CLAUDE_CODE_TRANSCRIPT_LOCAL_GC dropping a message from the saved transcript when its text held a Unicode line or paragraph separator (U+2028, U+2029) 
 Fixed claude purge leaving a prompt in the history file when its text held a Unicode line or paragraph separator (U+2028, U+2029) 
 Windows: Fixed PowerShell commands longer than about 1 KB always asking for permission, so allow rules and read-only detection now apply up to 32 KB 
 Windows: Fixed stdio MCP servers being force-killed at shutdown; stdin now closes first and the process tree is killed only if the server is still running after 300 ms 
 Windows: Fixed claude plugin install failing for GitHub owner/repo plugin sources on machines with no GitHub SSH key; the clone is now retried over HTTPS 
 Windows: Fixed rm -rf /c/Users/&lt;name&gt; in Git Bash not asking in bypass permissions mode 
 Improved fullscreen mode: the link under the mouse pointer is now underlined to show it can be opened 
 Improved transcript toggle (ctrl+o) responsiveness in code-heavy conversations by caching syntax-highlighted code blocks 
 Improved Claude Desktop's Code tab behind a Claude apps gateway: when a session can't start, including on a machine not set up for the gateway's code settings, the reason shows as a reply 
 Improved the errors for a refused cloud session: they now say why your organization's policy couldn't be loaded, and name an API key or auth token that overrides your claude.ai login 
 Improved --debug output to name unrecognized frontmatter fields in custom agent files, with a hint for likely typos 
 Improved auto mode: a tool call that wasn't run because auto mode's check had no usable answer now shows as a dim "Not run" row instead of a red error 
 Improved --debug output for hooks: command hooks on tool calls, prompts, SessionStart and Stop now log their command, plugin, outcome and duration when they finish, so a slow hook is identifiable 
 Improved CLAUDE_CODE_TRANSCRIPT_LOCAL_GC : a large transcript file is no longer rewritten when that would free under 10% of it 
 Updated /cost , the status line, --max-budget-usd and the SDK's cost figures to price Sonnet 5.5 cache reads at $0.10 per million tokens (was $0.20) 
 Updated the bundled dataviz skill: lighter violet for the seventh series in light mode, softer primary text in dark mode, and compact y-axis labels like 1K 
 Changed the default limit on MCP tool descriptions sent up front and on MCP server instructions from 2,048 to 4,096 characters 
 Changed ← : a turn or ! command started while the session moves to the background is now stopped instead of finishing out of sight 
 [VSCode] Fixed claudeCode.spinnerVerbs missing from the extension's settings, so settings.json now completes and validates it; a malformed value no longer breaks the chat panel 
 [VSCode] Changed Claude in Chrome to ask before browser actions in every session, including one connected with @browser , as the terminal does; allowing a site for the session stops repeat asks 
 [VSCode] Fixed chat links written as a full Windows path, such as C:\repo\file.ts or file:///C:/repo/file.ts, not opening the file on Windows 
 [VSCode] Fixed the working indicator still animating when reduced motion is turned on in your OS, in VS Code, or with the prefersReducedMotion setting 
 [VSCode] Fixed the prompt cache clock reading warm after the panel caught up on messages late, such as after the display was off or a remote window reconnected 
 [Cloud sessions] Added a status filter to the Sessions and Runners lists on a self-hosted environment's Activity tab in admin settings; you can pick several statuses at once 
 [Cloud sessions] Fixed every cloud session waiting for a self-hosted runner showing the same queue position; each now shows how many sessions are ahead of it 
 [Cloud sessions] Fixed a message you send while Claude is still replying in a cloud session jumping above that reply when it finishes; it now stays below it, including after a reload 
 [Claude Tag] Changed Claude in Slack to show the footer with the session link, model and cost only on its newest reply in a thread; the reply before it drops the footer 
 [Claude Tag] Fixed links to URLs that contain parentheses breaking in some of Claude's Slack replies and task checklists, which showed stray bracket text and opened the wrong page 
 [Claude Tag] Fixed Claude's Slack replies drawing color swatches beside codes that only look like hex colors, such as six-digit pull request numbers 
 [Claude Tag] Added creating, editing and deleting workspace and channel memory files on the Activity page's Memory tab for members with the Claude Tag Admin permission 
 [Claude Tag] Fixed the plugin confirmation card Claude posts in a Slack channel showing a plugin's ID instead of its name 
 [Claude Tag] Fixed Claude in Slack posting a card to remove a plugin the channel's own settings don't include; it now explains where the plugin comes from instead 
 [Claude Tag] Fixed Claude in Slack sometimes losing its reply when a session in a self-hosted environment moved to a new runner partway through a task 
 [Code Review] Fixed the Code Review check sometimes staying "in progress" on a pull request after the review finished; it now shows the review's result 
 [Code Review] Improved Code Review admin settings to say why a setting couldn't be saved, such as a policy restriction, instead of a generic failure message

</details>