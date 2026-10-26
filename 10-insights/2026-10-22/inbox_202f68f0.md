---
id: inbox_202f68f0
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0050-claude-code-releases-v2-1-309-d932]]"
title: "v2.1.309"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.309
source: claude-code-releases
published_at: 2026-10-22T22:18:57+00:00
fetched_at: 2026-10-23T00:54:39.928821+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版主要在補沙盒與權限檢查的漏洞，並修掉大量 VS Code、雲端工作階段、Slack 整合的小錯誤。 **Why** Claude Code 能執行 Bash、改檔、連 MCP，沙盒或權限檢查若有縫隙，指令就可能在使用者不知情下越界執行或改到不該改的檔案。 **How** 逐一補上各種繞過路徑：沙盒內 shell 啟動檔、symlink 下的 denyWrite、compound 指令中包了 cd 的 git、Edit deny 規則對 Bash redirect 的攔截、PowerShell 權限檢查等；部分行為改成更保守的預設（拒絕或詢問）。 **What** Claude Code v2.1.309。安全面：修正 macOS/Linux 沙盒指令會在沙盒外執行 shell 啟動檔、沙盒指令可修改 --mcp-config 指定的 MCP 設定檔、worktree 隔離守門漏放部分 locale 前綴與 zsh 算術指令等問題；行為變更包括 sed -i 改走標準 Bash 提示且不再被 /rewind 還原、claude ultrareview 需 workspace trust（腳本用 --trust-workspace 或環境變數 CLAUDE_CODE_DISABLE_ULTRAREVIEW_TRUST_CHECK=1）、Desktop/VS Code 的 bypass permissions 模式下危險的 rm/rmdir 直接拒絕並給改寫提示。另有 nested CLAUDE.md 過大只載入開頭以避免反覆 compact、Windows 上 git 指令加速、VS Code 與 Cloud sessions、Claude Tag（Slack）、Code Review 等多項修復。"
key_points:
  - "沙盒/權限修補：沙盒內 Bash 不再於沙盒外執行 shell 啟動檔；沙盒指令與自動接受的編輯不能再改 --mcp-config 指定的 MCP 設定檔；macOS denyWrite glob 在 symlink 路徑下可正確生效"
  - "行為變更：sed -i 改走標準 Bash 提示且不再被 /rewind 還原；claude ultrareview 需 workspace trust（--trust-workspace 或 CLAUDE_CODE_DISABLE_ULTRAREVIEW_TRUST_CHECK=1）；Desktop/VS Code 的 bypass permissions 模式下危險 rm/rmdir 直接拒絕並附改寫提示"
  - "過大的 nested CLAUDE.md 現在只載入開頭，避免 session 反覆 compact；Windows 上 Claude Code 自身執行的 git 指令變快，且錯誤訊息一律顯示英文"
tags: [claude-code, sandbox, permissions, release-notes, vscode]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.309

Claude Code 這版主要在補沙盒與權限檢查的漏洞，並修掉大量 VS Code、雲端工作階段、Slack 整合的小錯誤。

**Why** Claude Code 能執行 Bash、改檔、連 MCP，沙盒或權限檢查若有縫隙，指令就可能在使用者不知情下越界執行或改到不該改的檔案。

**How** 逐一補上各種繞過路徑：沙盒內 shell 啟動檔、symlink 下的 denyWrite、compound 指令中包了 cd 的 git、Edit deny 規則對 Bash redirect 的攔截、PowerShell 權限檢查等；部分行為改成更保守的預設（拒絕或詢問）。

**What** Claude Code v2.1.309。安全面：修正 macOS/Linux 沙盒指令會在沙盒外執行 shell 啟動檔、沙盒指令可修改 --mcp-config 指定的 MCP 設定檔、worktree 隔離守門漏放部分 locale 前綴與 zsh 算術指令等問題；行為變更包括 sed -i 改走標準 Bash 提示且不再被 /rewind 還原、claude ultrareview 需 workspace trust（腳本用 --trust-workspace 或環境變數 CLAUDE_CODE_DISABLE_ULTRAREVIEW_TRUST_CHECK=1）、Desktop/VS Code 的 bypass permissions 模式下危險的 rm/rmdir 直接拒絕並給改寫提示。另有 nested CLAUDE.md 過大只載入開頭以避免反覆 compact、Windows 上 git 指令加速、VS Code 與 Cloud sessions、Claude Tag（Slack）、Code Review 等多項修復。

### 重點
- 沙盒/權限修補：沙盒內 Bash 不再於沙盒外執行 shell 啟動檔；沙盒指令與自動接受的編輯不能再改 --mcp-config 指定的 MCP 設定檔；macOS denyWrite glob 在 symlink 路徑下可正確生效
- 行為變更：sed -i 改走標準 Bash 提示且不再被 /rewind 還原；claude ultrareview 需 workspace trust（--trust-workspace 或 CLAUDE_CODE_DISABLE_ULTRAREVIEW_TRUST_CHECK=1）；Desktop/VS Code 的 bypass permissions 模式下危險 rm/rmdir 直接拒絕並附改寫提示
- 過大的 nested CLAUDE.md 現在只載入開頭，避免 session 反覆 compact；Windows 上 Claude Code 自身執行的 git 指令變快，且錯誤訊息一律顯示英文

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.309)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed sandboxed Bash commands on macOS and Linux running the shell's startup files outside the sandbox before each command 
 Fixed macOS sandbox denyWrite glob patterns not applying at a path's real location when the pattern's folder is reached through a symlink 
 Fixed sandboxed commands and auto-accepted edits being able to modify the MCP config file passed with --mcp-config 
 Fixed a disabled MCP server being reconnected by a later permission prompt in print and SDK sessions 
 Fixed the Bash permission check trusting a variable set by a command whose redirect can fail to open 
 Fixed Bash permission checks not prompting for some compound commands that change directory before running git when the cd is wrapped or prefixed, as they do for a plain cd 
 Fixed an Edit(path) deny rule not blocking a Bash redirect to that path in some commands that also held a subshell 
 Fixed worktree-isolated sessions accepting some locale-prefixed commands the isolation guard should refuse 
 Fixed worktree-isolated sessions on zsh accepting some arithmetic commands that the isolation guard should refuse 
 Fixed worktrees and branch checkouts that Claude Code creates so they ignore git replace refs, as its other git operations already do 
 Fixed profile store write protection not applying when the config directory is reached through a symlink 
 Fixed sessions compacting repeatedly after reading files under a very large nested CLAUDE.md; a nested CLAUDE.md over the size limit now loads only its start 
 Fixed ctrl+enter (send now) only queuing a message when pressed before the response had started, and restarting a prompt's hooks while leaving the message queued when pressed while those hooks were running 
 Fixed key-bound slash commands running in the shell from ! mode 
 Fixed ctrl+o not showing messages from other agents and sessions that are still waiting to be delivered; they now appear in full under the transcript, marked as waiting 
 Fixed long tool output previews being cut through an emoji, leaving session transcripts that jq could not parse 
 Fixed Read reporting "File does not exist" for PDF page ranges in Linux sandboxes that share the parent's /proc 
 Fixed messages from a Claude Desktop-hosted session sometimes being lost when its connection refreshed 
 Fixed features missing from Claude Code sessions in the Claude desktop app when the terminal on the same computer was signed in to a different account or organization 
 Fixed the claude remote-control status line showing HEAD as the branch for a folder that is not in a git repository 
 Fixed split-pane agent teammates not inheriting the tool deny and --tools rules given on the leader's command line 
 Fixed sessions renamed with /rename appearing to other sessions under a generated name after a VS Code window reload or a non-interactive --resume 
 Fixed the /rewind list showing "No code changes" for a turn that changed checkpointed files through /code-review --fix , a subagent or a shell command 
 Fixed /privacy-settings showing an out-of-date "Help improve our AI models" value; it now also says when the setting can't be fetched 
 Fixed feedback saying "try again later" when your organization does not accept feedback; it now shows the server's reason and where to report a bug 
 Fixed oversized /feedback reports failing instead of being resent without the transcript 
 Fixed a skill in an --add-dir folder being unreachable when another skill already held its name; it is now offered as &lt;folder&gt;:&lt;name&gt; 
 Fixed /verify and /code-review not finding a nested package's own skill when its files were changed from the shell 
 Fixed the /claude-api skill saying that ant beta:worker poll --on-work passes trace context to the command 
 Fixed the /claude-api skill's C# tracing setup missing spans from the cloud platform clients 
 Fixed the /claude-api skill saying that API spans for requests to Claude Platform on AWS can't join the caller's trace 
 Fixed hooks that run in PowerShell not blocking when the hook's program exits with code 2, and on Windows PreToolUse and PermissionRequest hooks with "shell": "powershell" failing open when Git for Windows isn't installed 
 Fixed a mod's turn.step hook that names a model by alias, such as haiku , failing every request with a model error: the alias now resolves to its model 
 Fixed plugins and skills synced from claude.ai being removed, sometimes mid-session, after a disk read error 
 Fixed artifact publishes and updates being refused for some ordinary pages, such as pages with certain minified scripts or artifacts Claude could not read first 
 Fixed Claude asking for permission on each artifact update for the rest of a turn after the conversation was compacted in that turn 
 Fixed fine-grained tool streaming staying off on Amazon Bedrock when ANTHROPIC_BEDROCK_BASE_URL is set to the default bedrock-runtime.&lt;region&gt;.amazonaws.com endpoint 
 Fixed the "Waiting for API response" hint flickering behind gateways that send only keepalive pings: routes off Anthropic's backend now wait 45 seconds 
 Fixed Claude notifying unrelated GitHub users by writing role names and placeholders as mentions in PRs, issues and comments 
 Linux: Fixed sandbox write denies lifting when a background command outlived the session 
 Windows: Fixed PowerShell permission checks auto-approving some Set-Location or cd commands that target the current directory and carry extra arguments; these now prompt for approval 
 macOS: Fixed the "Install Command Line Developer Tools" dialog opening each time Claude Code starts on a Mac without Xcode or the Command Line Tools 
 Self-hosted runner: Fixed --startup-timeout-min stopping a session whose first prompt, such as /code-review , was still working in a subagent; a frozen process is still stopped 
 Improved the speed of many git commands Claude Code runs for itself on Windows; on every platform, errors from those commands now show in English even when git is set to another language 
 Improved the error when a hooks module is nested too deep to load: it now names the file instead of showing a bare stack-overflow message 
 Improved disk-full handling: a Bash command cut off by a full disk now says so and names the folder to free up, and starting on a full temp volume prints a clear message, not a raw ENOSPC error 
 Improved the /claude-api skill to offer API tracing alongside SDK tracing when asked to add OpenTelemetry 
 Improved the /claude-api skill to check the live docs before saying a feature is unsupported 
 Self-hosted runner: Improved sessions that move to a new runner: Claude now sees the tool call that was interrupted, marked as outcome unknown 
 Updated the bundled dataviz skill to accept APCA as a text-contrast measure (keeping WCAG 2 ratios where AA conformance is required), add an apca(text, background) function to its palette validator scripts, and say whether a label inside a colored chart fill should be white or near-black 
 Updated the /claude-api skill: service account keys and Workload Identity Federation tokens can now manage OpenTelemetry destinations 
 Changed sed -i to get the standard Bash prompt and run as written, not a simulated file-edit preview; like other Bash edits, it is no longer restored by /rewind 
 Changed claude ultrareview to require workspace trust: it asks on a terminal, else refuses; scripts pass --trust-workspace , which takes no value (put a PR number or base branch before it), or set CLAUDE_CODE_DISABLE_ULTRAREVIEW_TRUST_CHECK=1 
 Changed the dangerous rm and rmdir prompt in bypass permissions mode in the Desktop app and VS Code to deny the command at once with a rewrite hint, so unattended sessions keep going 
 Changed commands the settings exclude from the sandbox to ask before writing to its write-list paths while the sandbox is enabled but cannot run; the unsandboxed fallback is refused there 
 Changed worktree creation and reuse so git no longer fetches objects on demand, in ordinary clones and in partial clones with a Bash sandbox configured; such a partial clone fetches them first 
 Changed the /claude-api skill to build Managed Agents subagent teams on multiagent_20261001 with dynamic workflows on by default, instead of coordinator 
 [VSCode] Added a log warning that says what to do when dictation or the extension's own requests fail certificate verification, such as behind a TLS-inspecting proxy 
 [VSCode] Fixed the Claude panel staying blank after the editor cached an incomplete copy of its files; it now recovers by itself, or says what went wrong and how to fix it 
 [VSCode] Fixed Session history filling up with empty "Untitled" sessions each time you start a new session without sending a message 
 [VSCode] Fixed long slash-command messages such as /goal filling the chat panel; they now fold behind Show more like other prompts ( #97469 ) 
 [VSCode] Fixed long messages not folding behind Show more after the chat panel is made narrower 
 [VSCode] Fixed Ctrl+J in the chat input always inserting a newline: it is now left to VS Code and the OS when "ctrl+j" is set to null in the Chat context of ~/.claude/keybindings.json 
 [VSCode] Fixed a mod's "From the ... plugin" label above the prompt being drawn over the slash command and @-mention menus ( #102981 ) 
 [VSCode] Fixed an empty list item, paragraph or code block, and list items renumbered from 1, when pasting copied LaTeX math 
 [VSCode] Fixed the feedback error showing only an HTTP status when your organization does not accept feedback 
 [VSCode] Improved Edit and Write speed in the chat panel: the wait for new problems after each edit is now 0.75 seconds in most cases, down from 1 to 1.5 seconds 
 [Cloud sessions] Fixed the Add connector list in routine forms saying no connectors were available while they were still loading 
 [Cloud sessions] Fixed the cloud environment editor shuffling environment variables and adding backslashes to values that contain both kinds of quote 
 [Cloud sessions] Fixed the self-hosted environment details dialog in admin settings so its title, tabs and buttons stay in view while only the content scrolls 
 [Cloud sessions] Fixed the "read documentation" tool row in cloud sessions, which showed escaped JSON instead of a readable page 
 [Cloud sessions] Improved a cloud session's Changes pane, which now says when it lists only pushed commits or only Claude's edits 
 [Claude Tag] Fixed Claude in Slack posting a draft you approved for a channel into your DM by mistake; a post with no channel is now refused so it can go to the approved channel 
 [Claude Tag] Fixed Allow and Deny on Claude's approval cards in Slack doing nothing when the session had stopped; your answer now restarts the session 
 [Claude Tag] Fixed Claude ignoring untagged messages in a Slack channel after its workspace moved to a different Claude organization, including unshared channels on Enterprise Grid 
 [Claude Tag] Fixed Claude in a Slack channel posting a threaded reply before reading a newer message someone had just added to that thread 
 [Claude Tag] Fixed the Slack page in Claude Tag admin settings saying no workspaces were connected when the list failed to load; it now shows an error with a Retry button 
 [Code Review] Fixed a finished review showing no check on the pull request when earlier tries to create it failed; a final try now adds a completed check 
 [Code Review] Fixed a push queued behind a running review still starting a review after @claude review stop ; its check now closes and says why

</details>