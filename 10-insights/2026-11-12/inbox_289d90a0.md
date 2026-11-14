---
id: inbox_289d90a0
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0145-claude-code-releases-v2-1-323-8bac]]"
title: "v2.1.323"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.323
source: claude-code-releases
published_at: 2026-11-12T22:12:13+00:00
fetched_at: 2026-11-14T01:50:42.145901+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.323 新增實驗性的 Code Mode，讓 Claude 改寫 JavaScript 來呼叫工具，並大量修補 Bash 權限與沙箱缺口。 **Why** 原文未說明 Code Mode 的設計動機；修正項目集中在 Bash 權限檢查遺漏、沙箱可能被關閉，以及背景 session 登入帳號被切換等問題。 **What** 新增 Code Mode（實驗性、需手動開啟，組織也可關閉）；plugin.json 新增 engines[\"claude-code\"]，版本範圍不符的 plugin 不會被安裝、更新或載入；claude plugin validate 新增 TypeScript hooks 型別檢查。另新增 CLAUDE_CODE_DISABLE_AGENT_PROGRESS_SUMMARIES、CLAUDE_CODE_RESUME_HINT_COMMAND 等環境變數、.docx 上傳支援，以及 hooks 長時間執行時每 30 秒的 progress heartbeat。修正多項安全問題：Bash allow 規則的萬用字元（如 Bash(ls*)）可能略過提示、deny/ask 規則漏掉 sudo/env 包裝的指令、Write 與 Edit 工具可寫入被 Read deny 規則涵蓋的路徑、--permission-mode auto 在 auto mode 不可用時應退回 Manual 模式。"
key_points:
  - "Code Mode（實驗性、opt-in）：Claude 寫 JavaScript 呼叫工具，文件見 code.claude.com/docs/en/code-mode，組織可關閉"
  - "Plugin 生態：plugin.json 新增 engines[\"claude-code\"] 版本範圍限制；claude plugin validate 新增 TypeScript hooks 型別檢查，--strict 時警告即失敗"
  - "權限與沙箱修正：Bash(ls*) 這類附帶萬用字元的 allow 規則可能略過提示、deny/ask 規則漏掉 sudo/env 包裝、sandbox.excludedCommands 與沙箱可能失效，auto mode 不可用時改為退回 Manual 模式"
tags: [claude-code, code-mode, plugins, permissions, sandbox]
topics: [agents.coding_agents, security, agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.323

Claude Code v2.1.323 新增實驗性的 Code Mode，讓 Claude 改寫 JavaScript 來呼叫工具，並大量修補 Bash 權限與沙箱缺口。

**What** 新增 Code Mode（實驗性、需手動開啟，組織也可關閉）；plugin.json 新增 engines["claude-code"]，版本範圍不符的 plugin 不會被安裝、更新或載入；claude plugin validate 新增 TypeScript hooks 型別檢查。另新增 CLAUDE_CODE_DISABLE_AGENT_PROGRESS_SUMMARIES、CLAUDE_CODE_RESUME_HINT_COMMAND 等環境變數、.docx 上傳支援，以及 hooks 長時間執行時每 30 秒的 progress heartbeat。修正多項安全問題：Bash allow 規則的萬用字元（如 Bash(ls*)）可能略過提示、deny/ask 規則漏掉 sudo/env 包裝的指令、Write 與 Edit 工具可寫入被 Read deny 規則涵蓋的路徑、--permission-mode auto 在 auto mode 不可用時應退回 Manual 模式。

### 重點
- Code Mode（實驗性、opt-in）：Claude 寫 JavaScript 呼叫工具，文件見 code.claude.com/docs/en/code-mode，組織可關閉
- Plugin 生態：plugin.json 新增 engines["claude-code"] 版本範圍限制；claude plugin validate 新增 TypeScript hooks 型別檢查，--strict 時警告即失敗
- 權限與沙箱修正：Bash(ls*) 這類附帶萬用字元的 allow 規則可能略過提示、deny/ask 規則漏掉 sudo/env 包裝、sandbox.excludedCommands 與沙箱可能失效，auto mode 不可用時改為退回 Manual 模式

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.323)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added Code Mode, an experimental opt-in in which Claude writes JavaScript to call its tools; see https://code.claude.com/docs/en/code-mode to turn it on, or to turn it off for an organization 
 Added engines["claude-code"] to plugin.json : plugins outside their stated Claude Code version range are not installed, updated or loaded, and install and update pick the newest version that fits 
 Added type checking of a plugin's TypeScript hooks module to claude plugin validate ; each finding is a warning, and --strict fails on it 
 Added to claude plugin validate the $ nouns a mod's engine.create hook adds, withholds or replaces 
 Added support for CLAUDE_CODE_AUTO_MODE_MODEL in managed settings for Claude Desktop sessions on third-party providers (takes effect once Claude Desktop includes this version) 
 Added an options menu (stop, switch to usage credits, upgrade) when a model needs usage credits that are turned off or used up 
 Added a progress heartbeat every 30 seconds while hooks run long in claude -p and SDK sessions, so a host such as Claude Desktop won't end the turn as hung (once it includes this version) 
 Added .docx support to Artifact tool asset uploads 
 Added a /diff to close hint to the diff panel, and the keys that focus and close a panel to the ? shortcut guide 
 Added a start-up warning for Bash allow rules with a * in a variable's value, such as Bash(PORT=* npm run dev) 
 Added a warning when a plugin's language server can't start, naming the server and what to check 
 Added a one-time startup notice naming CLAUDE_CODE_PERFORCE_MODE when Perforce settings are found and the mode is off 
 Added CLAUDE_CODE_DISABLE_AGENT_PROGRESS_SUMMARIES (available since 2.1.318): set it to 1 to turn off subagent progress summaries and the requests that write them ( #86879 ) 
 Added CLAUDE_CODE_RESUME_HINT_COMMAND , which a program that starts Claude Code can set to have the exit hint name its own resume command 
 Added unsetOptionCount to the claude plugin install --json result: how many userConfig options are not yet set 
 Added isPromptCovered to the props a mod's pane is drawn with, telling it when a dialog or a field above the prompt covers the prompt 
 Fixed running /compact again, or after a command such as /context , summarizing away a message that Claude had not answered yet 
 Fixed a resumed session joining your next message to an old interrupted message that was not resumed 
 Fixed a memory spike at the next prompt after Claude changed a very large file 
 Fixed a setting saved in a running session undoing a hand edit made to settings.json moments earlier; a settings file you delete during a session now stays deleted 
 Fixed claude plugin commands and claude mcp list signing you out of a Console profile when they ended while the token was being renewed 
 Fixed Edit and Bash running out of memory on certain /proc files, and Edit hanging or running out of memory on devices and named pipes 
 Fixed Claude Code failing to start, or to clear stored credentials at sign-out, when saving its configuration file failed with "Out of memory" 
 Fixed requests sent without streaming failing on errors that streamed requests recover from, such as a rejected image, thinking block or beta header 
 Fixed ExitWorktree , the worktree exit dialog and /resume leaving the session in the wrong folder when the folder the shell was in before entering the worktree had been deleted 
 Fixed accents and other combining marks sometimes landing left of the text, leaving stale copies on screen, or silently disappearing when text wraps 
 Fixed the last key of a key chord, such as Enter in ctrl+x enter, acting on a dialog's text field when the chord's own action isn't available there 
 Fixed ps processes piling up when the process listing Claude Code runs before stopping a command takes too long 
 Fixed subagent transcripts and large tool results being saved apart from the session's transcript after entering a worktree created by a WorktreeCreate hook or belonging to a nested repository 
 Fixed a session on a named Anthropic profile moving to another sign-in when /fork , the Left arrow or --bg continued it in the background; reopen any session that was open during the update 
 Fixed a background session sending a conversation under another sign-in when its named Anthropic profile is missing, changed or overridden; it now stops and says so 
 Fixed a session on an API key, auth token or workload identity from its shell (not a setup token) moving to another sign-in in the background; it now stops and says so 
 Fixed MCP tool calls ending in the sign-in server's error, such as TOKEN_EXPIRED , instead of asking you to sign in again 
 Fixed an expired claude.ai login showing "Credit balance too low" when a saved Console key or ant auth login profile without credit was used instead 
 Fixed a session on a named Anthropic profile being handed to an older background service that could not keep its sign-in; it now says to restart the service 
 Fixed a background session's sign-in leaving the previous account's login or other credentials in place; it now clears them for every session on the computer, and a refused sign-in can leave no login 
 Fixed background sessions moving between a profile and the stored login when an update restarted them 
 Fixed sessions opened before a sign-in keeping signed-out feature flags after the sign-in 
 Fixed sessions that kept failing after a Claude apps gateway sign-in expired: once you sign in again with /login in another terminal, they carry on at the next message 
 Fixed the billing notice naming your ant auth login organization when a custom X-Api-Key header is set 
 macOS: Fixed "Not logged in · Please run /login" coming back right after a successful /login or a token refresh when the keychain was slow to answer 
 Fixed turns failing in Claude Desktop when an organization's gateway answers an expired token with 403: Claude Code now asks Desktop for a fresh token and retries 
 Fixed the error shown when Amazon Bedrock refuses your account a model: it no longer says to refresh your AWS credentials, it says to enable the model 
 Fixed the awsAuthRefresh or gcpAuthRefresh command sometimes running twice for one request when three or more sessions needed a fresh sign-in at once 
 Fixed the claude -p warning about an ended claude.ai login to say that claude auth logout also removes saved MCP server logins and plugin secrets 
 Fixed Bash permission prompts offering "don't ask again" for commands that write to sensitive paths such as .git or .claude , where the saved rule did not stop the next prompt 
 Fixed a case where some lsof commands ran without a permission prompt 
 Fixed Bash commands that write a file with cat > file being shown as "Read 1 file" 
 Fixed a case where Bash permission checks judged an rm from the wrong folder and skipped the dangerous-removal prompt under bypass permissions or a Bash allow rule 
 Fixed --permission-mode auto or a settings defaultMode: auto starting in a mode that could allow more when auto mode was unavailable. It now starts in Manual mode, which asks first 
 Fixed plan files sometimes being written outside the project when plansDirectory is set; a write that can't be shown to stay inside the project is now refused 
 Fixed a permission prompt when Claude read the output of its own background command or agent after entering a worktree 
 Fixed a case where Bash permission checks missed part of a command 
 Fixed a case where the Bash sandbox could switch off during a session 
 Fixed Bash allow rules with an attached wildcard, such as Bash(ls*) , skipping the permission prompt in some cases; a rule that names a variable, such as Bash(NODE_ENV*) , now asks 
 Fixed auto mode running behind a gateway at ANTHROPIC_BASE_URL on a model whose gateway name contains "haiku"; such a model, other than claude-haiku-5-5 , is now refused, as Haiku 4.5 is 
 Fixed Bash deny and ask rules missing some commands run through sudo , env and similar wrappers 
 Fixed Bash allow rules written with combined sudo flags skipping the permission prompt in some cases 
 Fixed sandbox.excludedCommands letting a command that it does not name run outside the sandbox in some cases 
 Fixed a case where the Write and Edit tools could write to a path covered by a Read deny rule 
 Fixed a case where a Bash command ran without a permission prompt for zsh users with certain non-default shell options set 
 Fixed the Bash sandbox not fully protecting Claude Code's own config on installs still using the legacy config file 
 Fixed a permission prompt from a mod's tool.check hook naming every plugin hooked on the tool instead of the one that asked 
 Fixed sandboxed commands being able to read Claude Code's file checkpoint copies under the config directory 
 Fixed a rewind sometimes changing your permission mode 
 Fixed project settings sometimes being read through a symbolic link that leads to a different folder than the one Claude Code checked 
 Fixed HTTP hooks failing with HTTP 500 on Linux when CLAUDE_CODE_SUBPROCESS_ENV_SCRUB is set and sandbox.enabled is off 
 Fixed claude -p and the Agent SDK running Bash unsandboxed when --settings or SDK settings that turn the sandbox on fail validation; Claude Code now stops at start-up and names the invalid setting 
 Fixed /export silently stopping early after a long run of calls to an MCP tool that is no longer loaded 
 Fixed earlier MCP tool calls missing from a resumed conversation, and lines repeating in scrollback, when the server connects late 
 Fixed claude mcp add --help splitting long example commands across lines in narrow terminals and pipes, so a pasted example ran without its header 
 Fixed plugins with defaultEnabled: false staying off in a claude.ai chat's cloud session after you turn them on in claude.ai 
 Fixed /fast on and /fast off on Vertex not asking a plugin's config.set hook, as the /fast menu does 
 Fixed documents created through the Claude Docs connector not opening in your browser when you work in a terminal 
 Fixed the misleading "not cached" error for a plugin only a repository's settings enable: it now says it isn't installed, gives the install command, and shows in text and stream-json -p runs 
 Fixed mods being able to reword Claude Code's own confirmation questions 
 Fixed a mod's hot reload sometimes ignoring a file created just after a failed reload 
 Fixed marketplaces named npm , pip , uv , cargo , github or gh being refused as reserved names 
 Fixed a stopped MCP call, or a stopped shell command in fullscreen, reading as "Called" or "Ran" in a collapsed tool group: it now says no result was recorded and shows its input 
 Fixed load errors of plugins enabled by managed settings going only to the debug log in SDK and Desktop sessions: init.plugin_errors now lists them 
 Fixed plugin installs hiding what a plugin's install command wrote to stderr when that command succeeded, such as a note that the plugin has no skills yet 
 Fixed one malformed entry in a plugin marketplace's renames map making Claude Code ignore the marketplace's other renames 
 Fixed claude --bg --safe-mode sessions stopping at startup to ask about project MCP servers that safe mode never starts 
 Fixed MCP link prompts offering Accept for non-http links without saying the link wouldn't open 
 Fixed /mcp and /plugins opening an MCP server's page with the cursor on "Disable" when the server needs authentication but still holds its sign-in; the page now offers "Reconnect" and opens on it 
 Fixed plugins with a version list in enabledPlugins staying off with no message: /plugin and claude plugin list now say why 
 Fixed plugins and marketplaces failing to install on Windows when the path of a cloned file reaches 260 characters 
 Fixed a Stop pressed right after sending a message showing as an error in remote and SDK sessions while a UserPromptSubmit or plugin prompt hook was still running 
 Fixed an MCP server staying disconne

[... truncated for safety ...]

</details>