---
id: inbox_19be912b
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2336-claude-code-releases-v2-1-307-2fb9]]"
title: "v2.1.307"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.307
source: claude-code-releases
published_at: 2026-10-21T22:17:02+00:00
fetched_at: 2026-10-21T23:40:58.152154+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版主要在補強穩定性與可觀測性：新增安全事件遙測，並修掉一堆 MCP、壓縮與雲端 session 的錯誤。 **Why** Claude Code 越來越常在雲端、self-hosted runner、無頭模式與桌面 app 中運行，睡眠、鎖定 keychain、連線中斷等邊角情況會造成 MCP 失敗、重複呼叫或對話狀態遺失。 **How** 新增 `claude_code.safety_event` OpenTelemetry 事件，記錄被權限規則、auto mode、安全檢查、hook 或 sandbox 攔截、詢問或退回的每次 tool call；HTTP MCP 工具呼叫在連線中斷時只重試唯讀或冪等的工具；無法解析的 tool call 會先重試最多 2 次才結束該回合。 **What** Claude Code v2.1.307 新增 `/claude-api api-version`，可將 Claude API 程式碼遷移到 API 版本 2026-10-21。修正 `CLAUDE_CODE_DISABLE_1M_CONTEXT` 搭配 `opus[1m]` 別名時的 model-not-found、macOS 鎖定 keychain 時 MCP 顯示需要驗證、電腦睡眠造成 MCP 逾時，以及部分 \"Autocompact is thrashing\" 錯誤；Agent SDK 的 `setModel()` 等待時間由 5 秒延長到 15 秒。Self-hosted runner 的 checkout hook 預設 30 分鐘後停止（可用 `--checkout-hook-timeout-min` 調整，設 0 為不限制），另有多項 VSCode 與 Code Review 更新（新增 `@claude review stop`/`off`/`pause`）。"
key_points:
  - "新增 `claude_code.safety_event` OpenTelemetry 事件，涵蓋權限規則、auto mode、安全檢查、hook、sandbox 攔截/詢問/退回的每次 tool call，利於稽核"
  - "HTTP MCP 工具呼叫於連線中斷時改為只重試唯讀或冪等工具，避免寫入類工具被送出兩次；無法解析的 tool call 最多重試 2 次"
  - "新增 `/claude-api api-version` 遷移至 API 版本 2026-10-21；Self-hosted runner checkout hook 預設 30 分鐘逾時，可用 `--checkout-hook-timeout-min` 調整"
tags: [claude-code, release-notes, mcp, opentelemetry, self-hosted-runner]
topics: [agents.coding_agents, agents.mcp, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.307

Claude Code 這版主要在補強穩定性與可觀測性：新增安全事件遙測，並修掉一堆 MCP、壓縮與雲端 session 的錯誤。 **Why** Claude Code 越來越常在雲端、self-hosted runner、無頭模式與桌面 app 中運行，睡眠、鎖定 keychain、連線中斷等邊角情況會造成 MCP 失敗、重複呼叫或對話狀態遺失。 **How** 新增 `claude_code.safety_event` OpenTelemetry 事件，記錄被權限規則、auto mode、安全檢查、hook 或 sandbox 攔截、詢問或退回的每次 tool call；HTTP MCP 工具呼叫在連線中斷時只重試唯讀或冪等的工具；無法解析的 tool call 會先重試最多 2 次才結束該回合。 **What** Claude Code v2.1.307 新增 `/claude-api api-version`，可將 Claude API 程式碼遷移到 API 版本 2026-10-21。修正 `CLAUDE_CODE_DISABLE_1M_CONTEXT` 搭配 `opus[1m]` 別名時的 model-not-found、macOS 鎖定 keychain 時 MCP 顯示需要驗證、電腦睡眠造成 MCP 逾時，以及部分 "Autocompact is thrashing" 錯誤；Agent SDK 的 `setModel()` 等待時間由 5 秒延長到 15 秒。Self-hosted runner 的 checkout hook 預設 30 分鐘後停止（可用 `--checkout-hook-timeout-min` 調整，設 0 為不限制），另有多項 VSCode 與 Code Review 更新（新增 `@claude review stop`/`off`/`pause`）。

### 重點
- 新增 `claude_code.safety_event` OpenTelemetry 事件，涵蓋權限規則、auto mode、安全檢查、hook、sandbox 攔截/詢問/退回的每次 tool call，利於稽核
- HTTP MCP 工具呼叫於連線中斷時改為只重試唯讀或冪等工具，避免寫入類工具被送出兩次；無法解析的 tool call 最多重試 2 次
- 新增 `/claude-api api-version` 遷移至 API 版本 2026-10-21；Self-hosted runner checkout hook 預設 30 分鐘逾時，可用 `--checkout-hook-timeout-min` 調整

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.307)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added /claude-api api-version to move Claude API code to API version 2026-10-21 
 Added the claude_code.safety_event OpenTelemetry event for each tool call a permission rule, auto mode, a safety check, a hook or the sandbox stopped, prompted or sent back 
 Fixed requests failing with a model-not-found error when CLAUDE_CODE_DISABLE_1M_CONTEXT is set and the model is an alias with the [1m] suffix, such as opus[1m] 
 Fixed the prompt-caching-scope beta header being sent behind custom ANTHROPIC_BASE_URL gateways and on Foundry, where it has no effect 
 Fixed MCP servers showing "needs authentication" in claude -p on macOS while the login keychain was locked; they now say why, and the next run after an unlock connects without a new sign-in 
 Fixed MCP servers being reported as timed out, and staying failed in headless runs, when a macOS or Linux computer went to sleep while they were connecting 
 Fixed HTTP MCP tool calls being sent twice when the connection closed mid-call; only read-only or idempotent tools are now retried 
 Fixed a turn sometimes starting without an SDK MCP server's latest tools when a background task was running 
 Fixed some "Autocompact is thrashing" errors in turns that read many PDF pages, images or other large tool results 
 Fixed /autocompact in cloud sessions going back to the default window after the session restarted 
 Fixed a conversation cleared with /clear sometimes coming back when a cloud or self-hosted runner session restarted 
 Fixed CLAUDE_STREAM_FIRST_BYTE_TIMEOUT_MS being ignored in Claude apps gateway sessions 
 Fixed telemetry from Claude Desktop sessions behind a Claude apps gateway being rejected when OTEL_EXPORTER_OTLP_HEADERS is set 
 Fixed /permissions &gt; Recently denied not showing the denied shell command, and auto mode's local classifier ignoring an approval from there when it checks a retried command; approving a row now names the command, not its description 
 Fixed /help and the / command menu showing long model-facing descriptions for bundled skills such as /claude-api instead of their short descriptions 
 Fixed subagent transcripts recording placeholder token usage and an empty stop reason for streamed responses 
 Fixed model switches through the Agent SDK's setModel() , and apps built on it, being refused when the API took more than 5 seconds to confirm the model; Claude Code now waits up to 15 seconds 
 Fixed a background command stopped through a connected app (such as the desktop app archiving an idle session) being reported to Claude as stopped by the user; the notice now names its output file 
 Fixed WebFetch in Cowork cloud sessions reporting a tool error when a site answered with a 4xx status or a robots.txt refusal; it is now a normal result, as in local sessions 
 Fixed write tools on a directly configured GitHub MCP server showing a form that closed without creating anything in the desktop app's Code tab 
 Fixed Artifact tool reads failing with a connection reset when the server had closed a reused connection 
 Self-hosted runner: Fixed sessions with --use-anthropic-git-proxy committing a .claude/settings.local.json left in the clone by an earlier session 
 Self-hosted runner: Fixed archiving or requeueing a session, or stopping the runner, during its checkout hook leaving the hook's processes running and the runner's slot held 
 Improved recovery from unparseable tool calls: Claude Code now retries the call up to twice before ending the turn with an error 
 Improved fork subagents launched together: each is now told which launch is its own, so forks are much less likely to try to start each other's work 
 Improved browser sign-in: the success page now appears as soon as sign-in completes, without waiting for your account profile to load 
 Improved web search errors in cloud and self-hosted runner sessions: a search refused with a 403 that gives a reason now shows that reason instead of a generic "Authentication error" 
 Improved the time to the first reply in cloud sessions when one of the desktop app's MCP servers can't connect 
 Improved Remote Control connect time for sessions whose transcript contains large pasted images or PDF reads 
 Changed the notice Claude gets when the WebSearch budget is used up to also tell it not to query search engines in a browser or through computer use 
 Changed the axScreenReader setting and CLAUDE_AX_SCREEN_READER in a settings env block to apply only from user, managed or --settings settings (since 2.1.305) 
 Self-hosted runner: Changed checkout hooks to be stopped after 30 minutes by default, failing the session's setup; if yours needs longer, raise --checkout-hook-timeout-min or set it to 0 
 Self-hosted runner: Changed the certificate file built for Anthropic-managed git to filter its trusted certificates as the CLI does; a [runner:warn] line gives the number left out 
 [VSCode] Added a notice on the microphone button when voice dictation stops by itself (15 seconds without recognized speech, or the 2-minute limit), saying why and that the text so far is kept 
 [VSCode] Fixed a long prompt expanded with Show more covering the whole chat panel: a pinned prompt is now capped at 40% of the panel and scrolls 
 [VSCode] Fixed part of a list item or table cell with LaTeX math pasting as a new list or table in rich text editors 
 [VSCode] Fixed dictation failing behind a TLS-inspecting proxy when NODE_EXTRA_CA_CERTS is set only in ~/.claude/settings.json ; it now also follows CLAUDE_CODE_CERT_STORE 
 [VSCode] Changed the "still open somewhere else" notice to also cover a Claude process left over from an extension restart, which usually ends on its own within about 10 minutes 
 [VSCode] Changed voice dictation to filter its trusted certificates as the CLI does 
 [VSCode] Changed the extension's own requests to filter their trusted certificates as the CLI does, and to trust the NODE_EXTRA_CA_CERTS file named in the environment or in user settings 
 [Cloud sessions] Fixed the repository picker saying "No repositories match" while a search was still running; it now shows "Searching..." until the results arrive 
 [Cloud sessions] Fixed the "Waiting for a runner" status on self-hosted environments being cut off; with on-demand runners it now counts up from your last message and shows failed attempts 
 [Code Review] Added @claude review stop (also off and pause ) to Code Review, ending an @claude review always subscription on a pull request without starting a new review

</details>