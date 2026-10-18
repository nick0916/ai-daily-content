---
id: inbox_b8b24647
date: 2026-10-15
source_ref: "[[00-inbox/.../inbox_b8b24647]]"
title: "v2.1.301"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.301
source: claude-code-releases
published_at: 2026-10-15T19:22:06+00:00
fetched_at: 2026-10-18T03:34:50.090638+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.301 發布。新增項目包含 CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS（無人值守 retry 模式遇到重置時間太遠的 usage limit 時直接結束請求）、vim mode 的 % 括號跳轉動作、claude-api skill 的 OpenTelemetry tracing 指引，以及 OpenTelemetry tool_decision 事件新增 classifier_verdict、permission_mode，並在 OTEL_LOG_TOOL_DETAILS=1 時提供 classifier_category，可區分 auto mode classifier 決策與 permission rule。修復包含：fable/best 模型別名在最新 Fable 模型對組織不可用時改為重試前一個 Fable 模型、Grep/Glob 搜尋程式意外失敗時誤報無結果、Read 工具把 .xlsm/.parquet/.epub/.heic 當文字讀取、切換到較小 context window 模型時可能未經詢問就花費 credits 做摘要、LLM gateway 回應模型名稱不同導致反覆 compaction 等。改進方面：切換到較小 context window 模型時，會先由前一個模型摘要過長對話。VS Code 新增 LaTeX 數學渲染與 usage-limit banner 的「Get more usage」連結。另有多項 mods 相關 API 調整與 self-hosted runner、Windows 修復。"
key_points:
  - "OpenTelemetry tool_decision 事件新增 classifier_verdict、permission_mode，及 OTEL_LOG_TOOL_DETAILS=1 時的 classifier_category，可區分 classifier 與 permission rule 的決策"
  - "切換到較小 context window 模型時，過長對話先由前一個模型摘要；並修復未經詢問就花費 credits 做摘要的情況"
  - "新增 CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS，無人值守模式遇到過遠的 usage limit 重置時直接結束請求"
tags: [claude-code, release-notes, opentelemetry, vim-mode, vscode]
topics: [agents.coding_agents, engineering.evals]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.301

Claude Code v2.1.301 發布。新增項目包含 CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS（無人值守 retry 模式遇到重置時間太遠的 usage limit 時直接結束請求）、vim mode 的 % 括號跳轉動作、claude-api skill 的 OpenTelemetry tracing 指引，以及 OpenTelemetry tool_decision 事件新增 classifier_verdict、permission_mode，並在 OTEL_LOG_TOOL_DETAILS=1 時提供 classifier_category，可區分 auto mode classifier 決策與 permission rule。修復包含：fable/best 模型別名在最新 Fable 模型對組織不可用時改為重試前一個 Fable 模型、Grep/Glob 搜尋程式意外失敗時誤報無結果、Read 工具把 .xlsm/.parquet/.epub/.heic 當文字讀取、切換到較小 context window 模型時可能未經詢問就花費 credits 做摘要、LLM gateway 回應模型名稱不同導致反覆 compaction 等。改進方面：切換到較小 context window 模型時，會先由前一個模型摘要過長對話。VS Code 新增 LaTeX 數學渲染與 usage-limit banner 的「Get more usage」連結。另有多項 mods 相關 API 調整與 self-hosted runner、Windows 修復。

### 重點
- OpenTelemetry tool_decision 事件新增 classifier_verdict、permission_mode，及 OTEL_LOG_TOOL_DETAILS=1 時的 classifier_category，可區分 classifier 與 permission rule 的決策
- 切換到較小 context window 模型時，過長對話先由前一個模型摘要；並修復未經詢問就花費 credits 做摘要的情況
- 新增 CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS，無人值守模式遇到過遠的 usage limit 重置時直接結束請求

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.301)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.301

What's changed 
 
 Added CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS so unattended retry mode ( CLAUDE_CODE_RETRY_WATCHDOG ) ends a request at a usage limit that resets too far away instead of waiting 
 Added OpenTelemetry tracing guidance to the claude-api skill, including setting up trace destinations with the ant CLI 
 Added the % motion to vim mode: jump to the matching bracket, alone or with d/c/y 
 Added rows to a mod's Input : a text field of several lines in the terminal, where Enter submits and Shift+Enter or a backslash before Enter starts a new line 
 Added classifier_verdict and permission_mode to OpenTelemetry tool_decision events, so auto mode classifier decisions can be told apart from permission rules 
 Added classifier_category to OpenTelemetry tool_decision events, naming the built-in rule a classifier block matched, when OTEL_LOG_TOOL_DETAILS=1 
 Fixed quitting removing a worktree made by a WorktreeCreate hook without asking when it may hold unpushed commits 
 Fixed the fable (and best ) model alias erroring on the Anthropic API when the newest Fable model is not available to your organization: Claude Code now retries once on the previous Fable model 
 Fixed a misleading "Please run /login" error when a full disk keeps the login from being refreshed; the error now names the disk and says to delete files 
 Fixed Grep and Glob reporting no matches when the search program failed unexpectedly before returning any results; they now return an error saying the search failed 
 Fixed workflow agents sometimes skipping their step, and the run still reporting success, after reading the harness note that their task text carries no user authority 
 Fixed artifact updates being refused where a PreToolUse hook covers Edit or Write; Claude now edits the file and then republishes instead of changing it in the publish call 
 Fixed skills and commands with very many or very long argument names stalling for seconds when invoked; only the first 64 names, each up to 64 characters, are now filled in 
 Fixed skills, commands and hooks using very large amounts of memory when their arguments fill many placeholders 
 Fixed stray characters such as &gt;0q covering the folder trust prompt, and &gt;4m before the shell prompt at exit, in terminals built on VTE older than 0.53 such as MATE Terminal on RHEL 8 
 Fixed stray GOK text appearing in the prompt at startup in some versions of iTerm2 
 Fixed switching to a model whose name contains application-inference-profile running your awsAuthRefresh command and delaying model-switch hooks when the provider is not Bedrock 
 Fixed sign-in refresh timeouts and unexpected sign-outs after a short command such as claude auth status or claude plugin list exited in the middle of a token refresh 
 Fixed a tool call cut off by a message sent mid-turn during its permission check being reported to the model as rejected by the user 
 Fixed a case where switching to a model with a smaller context window could spend usage credits on a summary by the previous model without asking first 
 Fixed conversations being compacted over and over, on a model you didn't pick, behind an LLM gateway whose responses name a different model than the one requested 
 Fixed vim mode sometimes staying in INSERT after Escape on a slow or busy machine 
 Fixed Esc discarding a typed AskUserQuestion answer in vim mode: the free-text field now supports vim NORMAL mode, and Esc cancels only from NORMAL 
 Fixed the Read tool reading binary files such as .xlsm, .parquet, .epub and .heic as text 
 Fixed a Markdown table with only a header row drawing nothing when too wide for the terminal, including in plans on the plan approval card 
 Fixed the /claude-api skill saying CMEK external-key endpoints aren't available on Claude Platform on AWS 
 Fixed skills no longer being listed to the model after using /rewind 
 Fixed the compaction row in a resumed session offering ctrl+o for history that is not loaded; it now says where the earlier messages are saved, and also shows in fullscreen 
 Fixed the "new task? /clear to save tokens" hint coming back right after you interrupt a response 
 Fixed the permission prompt for a plugin or skill hook's ask decision not showing which plugin or skill the hook comes from 
 Fixed /diff not noticing a conflicted cherry-pick or revert in reftable repositories when one of its git checks timed out or failed 
 Fixed workflow scripts asking for permission or being refused when read, edited or re-run after a Bash cd in the same session 
 Fixed dim text on the dark ANSI theme and 16-color terminals: faint inside filled boxes, not faint under selection and search highlights, and list descriptions dimmed like other secondary text 
 Fixed a mod's $.model.fork returning nothing-to-fork when called before the first response of a new Claude Code process had finished, as in claude -p runs and cloud sessions 
 Fullscreen mode: Fixed /compact and auto-compact briefly freezing the UI while the visible transcript is rebuilt 
 Self-hosted runner: Fixed sessions started from Slack being unable to find or attach a repository when managed settings restrict MCP servers; use deniedMcpServers to keep those tools off 
 Self-hosted runner: Fixed sessions being reported as having a deleted source branch, and not retried, when an unrelated setup or session failure quoted git's missing-ref wording 
 Self-hosted runner: Fixed the log promising a retry of a failed or declined session release for a session that is ending; repeated failures now show a count 
 Windows: Fixed stopped background PowerShell commands missing the closing [killed] line in their output file 
 Improved switching to a model with a smaller context window: a conversation too long for the new model is now summarized by the previous model first 
 Improved rendering performance while a long-running subagent works: its progress trail now updates incrementally instead of being reprocessed in full on every render 
 Improved artifacts: pages Claude writes now paint the band above a sticky header, so scrolled text no longer shows there in the mobile apps 
 Improved mods: in VS Code and the desktop and mobile apps, a tree drawn above the question dialog can now hold Markdown and up to 48 rows; the terminal keeps 12 plain rows 
 Changed a mod hook's .catch handler to run only when the hook throws or times out; events raised beneath the hook's own calls now skip that hook without asking its .catch 
 Changed a mod's $.env.set to resolve with {} once the variable is set or unset, or with { deny } saying why when the write is not made 
 [VSCode] Added LaTeX math rendering in Claude's responses, including $$ and multi-line \[ ... \] blocks and inline $...$ and \(...\) math 
 [VSCode] Added a "Get more usage" link to the usage-limit banner for Pro and Max plans in the VS Code and JetBrains panels 
 [VSCode] Fixed a conversation that crashes or freezes the panel being reopened on every reload 
 [VSCode] Fixed the chat panel slowing down during long thinking: it no longer re-parses the whole thinking text on every update 
 [VSCode] Fixed diagnostics showing "[object Object]" instead of the rule code (e.g. MD013) for some language servers 
 [VSCode] Fixed the native dictation audio module being loaded, to check microphone permission, where dictation is not offered (non-claude.ai sign-ins, remote windows)

</details>