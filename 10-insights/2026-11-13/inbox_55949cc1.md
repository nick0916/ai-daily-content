---
id: inbox_55949cc1
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0145-claude-code-releases-v2-1-325-c6e0]]"
title: "v2.1.325"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.325
source: claude-code-releases
published_at: 2026-11-13T20:40:01+00:00
fetched_at: 2026-11-14T01:50:42.137810+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.325 是一次大規模的修補版，重點補強權限規則、沙箱與驗證流程的漏洞，並修正 subagent、MCP 與 session 的多處錯誤。 **Why** 原文未列出單一動機，但修正內容集中在 Bash 權限檢查缺口、deny/ask 規則失效、沙箱防護不完整等安全面向，以及登入切換與 MCP 連線的穩定性。 **What** Claude Code v2.1.325 修正 zstd 壓縮回應解碼的安全問題；修正部分 Bash deny/ask 規則未套用、某些複合指令未經詢問就執行、allow 規則可能執行不同程式等權限缺口；修正沙箱對 worktree 設定、hooks 與共用 git 資料夾的保護不足。另修正 subagent 在 opusplan 或 haiku 設定下被誤換成 plan-mode 模型、第三方 gateway 與 Foundry 每輪都報 context length 錯誤而不壓縮、多個 MCP 任務卡住或重連問題，並改善 subagent 輸出被截斷時會要求更簡短地重答。"
key_points:
  - "安全修補：zstd 壓縮回應解碼漏洞；Bash 複合指令可能未詢問就執行、allow 規則可能執行與名稱不同的程式、部分 deny/ask 規則未套用"
  - "沙箱強化：修正 worktree 設定與 hooks、linked worktree 共用 git 資料夾、native updater 下載資料夾的防護缺口"
  - "穩定性修正：subagent 在 opusplan/haiku 下被誤換模型、第三方 gateway 與 Foundry 的 context length 錯誤無法壓縮、多項 MCP 任務與背景 session 登入切換問題"
tags: [claude-code, release-notes, permissions, sandbox, mcp]
topics: [agents.coding_agents, security, agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.325

Claude Code v2.1.325 是一次大規模的修補版，重點補強權限規則、沙箱與驗證流程的漏洞，並修正 subagent、MCP 與 session 的多處錯誤。

**Why** 原文未列出單一動機，但修正內容集中在 Bash 權限檢查缺口、deny/ask 規則失效、沙箱防護不完整等安全面向，以及登入切換與 MCP 連線的穩定性。

**What** Claude Code v2.1.325 修正 zstd 壓縮回應解碼的安全問題；修正部分 Bash deny/ask 規則未套用、某些複合指令未經詢問就執行、allow 規則可能執行不同程式等權限缺口；修正沙箱對 worktree 設定、hooks 與共用 git 資料夾的保護不足。另修正 subagent 在 opusplan 或 haiku 設定下被誤換成 plan-mode 模型、第三方 gateway 與 Foundry 每輪都報 context length 錯誤而不壓縮、多個 MCP 任務卡住或重連問題，並改善 subagent 輸出被截斷時會要求更簡短地重答。

### 重點
- 安全修補：zstd 壓縮回應解碼漏洞；Bash 複合指令可能未詢問就執行、allow 規則可能執行與名稱不同的程式、部分 deny/ask 規則未套用
- 沙箱強化：修正 worktree 設定與 hooks、linked worktree 共用 git 資料夾、native updater 下載資料夾的防護缺口
- 穩定性修正：subagent 在 opusplan/haiku 下被誤換模型、第三方 gateway 與 Foundry 的 context length 錯誤無法壓縮、多項 MCP 任務與背景 session 登入切換問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.325)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed a security issue in how zstd-compressed responses are decoded 
 Added a spinner tip in VS Code and similar integrated terminals about re-running a notebook cell, shown once Claude has read or edited a Jupyter notebook 
 Added a line under the error shown when your organization's policy blocks a request, saying how to continue: run /rewind and change the message, or run /clear 
 Added a note for Claude when a sandboxed git checkout , git stash or autostash pull cannot update protected files such as those in .claude 
 Fixed /security-review and skills' inline git commands stopping with an error in worktrees of bare repositories, --separate-git-dir checkouts and Android repo checkouts 
 Fixed subagents with their own model being moved to the plan-mode model when the model setting is opusplan or haiku 
 Fixed subagents on a different model sizing file reads and MCP results with the main session's model 
 Fixed sessions on many third-party gateways and Foundry stopping with a context length error on every turn instead of compacting 
 Fixed recent turns sometimes going missing from a resumed session after Claude Code stopped without a clean exit 
 Fixed shell commands running in the launch directory after the working directory was deleted; the command now fails with a message and can be re-issued 
 Fixed an approved plan edit being lost when the plansDirectory folder can't take it: the plan is now saved in the default plans folder, and a warning says where and why 
 Fixed a saved sonnet[1m] model setting being rewritten on a new install to a model id the API rejects 
 Fixed focus view hiding the reply to your prompt when a scheduled task replied after it 
 Fixed the prompt sometimes missing from a background subagent's view when fullscreen is off 
 Fixed long options in lists and permission prompts being partly overwritten when they wrap, and first-run screens losing lines on narrow terminals 
 Fixed startup warnings about permission rules and the "N MCP servers need authentication" notice being recorded as seen when they were scrolled out of view 
 Fixed the welcome header showing control characters or splitting across lines when an agent's name or the working folder contains them or a line break 
 Fixed the red error shown when Claude tries a command only you can run: a dim line now says it runs only when you type it at the prompt 
 Fixed /stats showing an Active days total that was one day too high 
 Fixed /insights saying a report was ready when no session qualified for analysis, and writing two values into its HTML report without escaping them 
 Fixed /voice saying voice mode changed when managed settings, --settings , or the project's .claude/settings.json or .claude/settings.local.json kept it as it was; it now says what holds it 
 Fixed the IDE welcome dialog showing Cmd+Esc for Quick Launch on Windows and Linux 
 Fixed Slack app tips showing when your organization's policy denies cloud sessions 
 Fixed claude purge hanging silently when there is no terminal to read keys from, and its project picker and -i prompts ignoring the keyboard when stdin is piped 
 Fixed claude plugin eval --output-dir '' writing the report into the current folder; it now exits with an error 
 Fixed claude -p text output on a terminal passing control sequences other than text styling; pipes and files are unchanged 
 Fixed leftover .oauth_refresh.lock.owner.tmp.* files piling up in the config directory 
 Fixed /fast saying "Fast mode has been disabled by your organization" under the keyless Console sign-in, where Claude Code had not asked the server 
 Fixed /model saying that your organization restricts a model when Claude Code could not check that, for example with no network 
 Fixed "Sign in with your Console account" in /login replacing your existing login when you pressed Esc right after the browser step 
 Fixed the browser showing the sign-in success page in some cases where sign-in failed or was canceled 
 Fixed claude auth status and other short commands leaving a lock behind on a Console profile, which made the next session hang for about a minute 
 Fixed background sessions started on your claude.ai login using (and billing) an API key or token from the shell that started the background service 
 Fixed more cases of a session moving to another sign-in in the background; these moves are now refused, with a message saying what works 
 Fixed a second Enter in the exit dialog stopping background work after the move to the background was refused 
 Fixed token counting on Amazon Bedrock sending the conversation to Bedrock when the allowedProviders managed setting does not allow it 
 Fixed AWS credential_process helpers and Google Cloud default credentials failing when Claude Code is started without a HOME environment variable 
 Fixed a session sometimes going back to an earlier permission mode after a subagent's plan was approved 
 Fixed one invalid value in an Agent SDK applyFlagSettings() call silently discarding all settings from earlier calls; a call that would do this is now refused with an error 
 Fixed sessions showing as waiting for input when a finished pull request only needed your own review or merge 
 Fixed an unrecognized teammateMode settings value being ignored without a warning: claude -p , the startup warning and claude doctor now list it as a skipped entry (still not applied) 
 Fixed --worktree skipping a WorktreeCreate hook from a plugin in CLAUDE_CODE_PLUGIN_SEED_DIR on the first run in a new home directory 
 Fixed brief-mode sessions, such as Dispatch, sending a reply again after the turn had already replied 
 Fixed Claude saying a working Atlassian, Asana or Sentry connector had failed in cloud sessions when a plugin listed it at a different URL 
 Fixed Claude Desktop and SDK sessions listing a folder's own MCP servers ( .mcp.json , local) as host-added or not at all, and not connecting WebSocket ones, after a folder move or pre-warmed start 
 Fixed /mcp still listing a plugin's MCP server after a plugin reload removed it while it was connecting 
 Fixed an MCP server staying "needs authentication", and its mcp_tool hooks being skipped, after a token refresh that was refused only for a moment 
 Fixed MCP elicitation requests being cancelled without asking in headless mode after a server's connection was replaced during a tool call 
 Fixed MCP tool calls from an SDK host answering "Not connected" after a tool call had reconnected the MCP server 
 Fixed an MCP task getting stuck after its question was closed with Esc or asked again: the footer now says it needs your input, and Enter in /tasks shows the question again 
 Fixed background MCP tasks that stopped updating after another call to the same server lost the connection, when a later call reconnects 
 Fixed a background MCP task's question opening over a message you were still typing; it now waits until you send or clear the draft, and the spinner and turn timer keep running 
 Fixed worktree.sparsePaths and sparse plugin and marketplace clones leaving out the repository's root files on older git versions, such as 2.34 
 Fixed self-hosted runner sessions with several repositories being unable to use a repository added mid-session 
 Fixed Claude asking for permission before reading your own artifact or its data 
 Fixed deny and ask permission rules and hooks for the Artifact tool not applying in some cloud sessions 
 Fixed Code Mode scripts ignoring a worktree entered with EnterWorktree , writing ~ paths into the project, and leaving /mcp showing an MCP server as connected after its sign-in expired 
 Fixed words typed with a Yes at a permission dialog or plan approval not reaching Claude in Code Mode 
 Fixed Claude starting work by itself when you resumed a session that ended during a Code Mode script; it now waits for your next prompt 
 Fixed a missing OpenTelemetry user_prompt event for a message sent while tool calls run. The event has delivery.mode: "mid_turn" and the running turn's prompt.id 
 Fixed the OpenTelemetry user_prompt event leaving out earlier messages' text when queued messages merged into one turn in VS Code, or when one message had an image 
 Fixed a slash command's allowed-tools grants applying to background agents woken during or after its turn 
 Fixed /feedback and /bug to upload other sessions only when they were recorded by the signed-in account or organization 
 Fixed relative deny and ask permission rules (e.g. Read(./.env) ) no longer covering the project after a cd ; they now also apply in added directories 
 Fixed deny and ask permission rules starting with mcp__plugin_*_ missing a plugin's MCP server or tool spelled in another letter case 
 Fixed deny rules not being applied to a permission approval that arrives after Claude Code restarts, in self-hosted runner and claude remote-control sessions 
 Fixed a case where a committed .claude/settings.local.json could be treated as the user's own when Claude Code was started in certain subfolders of a repository 
 Fixed some deny and ask rules not applying to certain Bash commands 
 Fixed a gap in Bash permission checks where some compound commands could run without asking; these now ask for permission 
 Fixed a case where a Bash allow rule could run a different program than the one it names 
 Fixed a connector tool's approval prompt in cloud sessions being answered automatically while plugins were still loading 
 Fixed some subagents changing an artifact that people outside your organization can see, or uploading files to it, without asking first when an allow rule is set or uploads were approved earlier 
 Fixed some artifact publishes skipping the confirmation for pages that people outside your organization can see when "don't ask again" had been chosen for Artifact 
 Fixed auto mode judging only the first change to an artifact that people outside your organization can see; its yes now covers that change alone 
 Fixed a managed strictPluginOnlyCustomization lock on agents and skills not taking effect in sessions that were already running 
 Fixed sandboxed commands being able to write to the native updater's download folder in some cases 
 Fixed a case where the Bash sandbox did not fully protect a worktree's settings and hooks 
 Fixed a case where the Bash sandbox did not fully protect a linked worktree's shared git folder 
 Fixed /teleport 's stash choice in some unusual git states: it now stops and says what to do 
 Windows: Fixed a start-up stall that could last about a second when a PATH entry sits under a folder your account cannot open 
 Fixed /resume on Windows refusing or hiding sessions whose folder was recorded with a different drive-letter case or slashes 
 Fixed an in-session /resume on Windows dropping a project's saved trust when the session was recorded with a different drive-letter case 
 Linux: Fixed sandboxed Bash commands failing with bwrap: Can't create file when the working directory was below an allowRead folder inside a denyRead , such as under a symlinked home directory 
 Fixed Claude Desktop's third-party deployments staying on "Stopping" until a token renewal finished (once it includes this version) 
 Improved subagents cut off at the output token limit: they are now asked for the whole answer again, more briefly, instead of returning only its end 
 Improved startup with a keyless Console sign-in or other Anthropic profile login: a token that is still valid is read without waiting for the credentials lock 
 Improved the account email check: it now also refuses your email as a client's identity in scripts a command runs, file writes, web fetches and MCP calls 
 Improved the HTTPS authentication failed message for private plugin marketplaces: it now says git's terminal prompts and askpass programs are disabled, and it also appears with newer git versions 
 Improved the add-marketplace confirmations, plugin recommendation prompts and plugin install warning to say that plugins can run code on your c

[... truncated for safety ...]

</details>