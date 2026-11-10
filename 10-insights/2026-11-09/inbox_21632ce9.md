---
id: inbox_21632ce9
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-claude-code-releases-v2-1-321-9e12]]"
title: "v2.1.321"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.321
source: claude-code-releases
published_at: 2026-11-09T19:22:30+00:00
fetched_at: 2026-11-10T00:02:34.856780+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 2.1.321 把預設 Fable 模型換成新版，並修補大量權限與沙箱漏洞。 **Why** 過去 Bash 權限檢查、MCP OAuth 轉址、網路路徑檔案編輯等處有判斷錯誤，可能在沒提示的情況下寫檔或外洩憑證。 **How** 逐項修正權限判斷（路徑、cp/mv、唯讀指令沙箱）、限制 OAuth 轉址時不再送出 refresh token，並改善 fast mode 降級、遠端工作階段與 Remote Control 穩定性。 **What** Claude Code v2.1.321 新增 Claude Fable 5.2（claude-fable-5-2），成為預設 Fable 模型，1M context、$8/$40 每百萬 token，快取讀取 $0.20/Mtok；`claude remote-control` 新增 `--settings`；另修正 MCP OAuth 機密外洩、唯讀 Bash 指令繞過沙箱、NotebookEdit 覆寫首格等數十項問題。"
key_points:
  - "新增 Claude Fable 5.2（claude-fable-5-2）為預設 Fable 模型，1M context，$8/$40 per Mtok，cache 讀取 $0.20/Mtok"
  - "安全修正：MCP OAuth 被伺服器轉址時不再把 refresh token 等機密送到另一主機；唯讀 Bash 指令不再未經提示跑出沙箱；cp/mv 進目錄現在會套用 deny 規則與受保護檔案提示"
  - "fast mode 在 fast serving 被限流或失敗時，改為先以同模型標準速度重試；`claude remote-control` 新增 `--settings` 套用設定檔到每個工作階段"
tags: [claude-code, claude-fable-5-2, security-fix, mcp-oauth, release-notes]
topics: [agents.coding_agents, foundation_models.claude, security]
importance: 4
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.321

Claude Code 2.1.321 把預設 Fable 模型換成新版，並修補大量權限與沙箱漏洞。

**Why** 過去 Bash 權限檢查、MCP OAuth 轉址、網路路徑檔案編輯等處有判斷錯誤，可能在沒提示的情況下寫檔或外洩憑證。

**How** 逐項修正權限判斷（路徑、cp/mv、唯讀指令沙箱）、限制 OAuth 轉址時不再送出 refresh token，並改善 fast mode 降級、遠端工作階段與 Remote Control 穩定性。

**What** Claude Code v2.1.321 新增 Claude Fable 5.2（claude-fable-5-2），成為預設 Fable 模型，1M context、$8/$40 每百萬 token，快取讀取 $0.20/Mtok；`claude remote-control` 新增 `--settings`；另修正 MCP OAuth 機密外洩、唯讀 Bash 指令繞過沙箱、NotebookEdit 覆寫首格等數十項問題。

### 重點
- 新增 Claude Fable 5.2（claude-fable-5-2）為預設 Fable 模型，1M context，$8/$40 per Mtok，cache 讀取 $0.20/Mtok
- 安全修正：MCP OAuth 被伺服器轉址時不再把 refresh token 等機密送到另一主機；唯讀 Bash 指令不再未經提示跑出沙箱；cp/mv 進目錄現在會套用 deny 規則與受保護檔案提示
- fast mode 在 fast serving 被限流或失敗時，改為先以同模型標準速度重試；`claude remote-control` 新增 `--settings` 套用設定檔到每個工作階段

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.321)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added Claude Fable 5.2 ( claude-fable-5-2 ), now the default Fable model — 1M context, $8/$40 per Mtok with $0.20/Mtok cache reads 
 Added --settings to claude remote-control , which applies a settings file to every session it starts; if the file changes, no new session starts until you restart claude remote-control 
 Fixed MCP OAuth requests sending secrets such as refresh tokens to another host when a server redirected them 
 Fixed a case where a read-only Bash command ran outside the sandbox without a permission prompt 
 Fixed a case where Bash permission checks judged a file write from the wrong folder and didn't prompt 
 Fixed deny rules and protected-file prompts not applying to the file that a cp or mv into a directory writes 
 Fixed the "Draws from usage credits" note showing after a switch to Fable on Enterprise seats whose plan includes Fable 
 Fixed the fallback model sometimes declining a request or mentioning a stopped response when the first model was blocked before replying 
 Fixed claude mcp login printing a SEP-2352 issuer warning each time you sign in again to a server that Claude Code registered with 
 Fixed NotebookEdit deleting or overwriting a notebook's first cell when the call named no cell, on network paths (UNC shares, WSL folders, /net mounts) 
 Fixed Edit changing the first of several matches, replacing a whole file on an empty old_string , or editing a notebook as text, on network paths (UNC shares, WSL folders, /net mounts) 
 Fixed /config showing Manual as the default permission mode when new sessions start in auto mode; pressing Space on "Auto (default)" now saves Don't Ask, not Plan 
 Windows: Fixed FileChanged hooks stopping for paths set through watchPaths after the first shell command, when the session's working directory had a lowercase drive letter 
 Fixed --plugin-dir . and --plugin-dir ./builtin writing generated type files for Claude Code's built-in plugins into a builtin folder 
 Fixed context usage estimates overcounting tool definitions when exact token counts are unavailable 
 Fixed /compact showing twice in Remote Control on web and mobile 
 Fixed plugin auto-updates and /plugin marketplace updates downloading a plugin again for each worktree or folder of a repository 
 Fixed auto mode losing a background subagent's report that had started a turn when the conversation was compacted before Claude answered it 
 Fixed project skills, commands and agents staying missing after their folder was removed and came back mid-session, such as with git stash , including after entering a worktree 
 Fixed claude -p sometimes telling Claude that background commands get 30 minutes when they are stopped after 10 
 Fixed pkill , pgrep and pidwait in cloud sessions matching the session's own parent processes 
 Fixed Claude in Chrome and computer use server processes staying alive after their parent exits behind a proxy that stalls connections 
 Fixed a large hook output pointing Claude to a file that held another hook's output from the same tool call 
 Fixed apps that embed Claude Code getting their own PreToolUse hook's ask reason instead of another hook's when both asked 
 Fixed a PreToolUse hook's ask being lost when another hook's defer finished first and could not be honored 
 Fixed a rare crash on permission prompts and background tasks 
 Fixed project skills, commands and agents disappearing from the menu in SDK and desktop sessions after Claude entered a worktree 
 Fixed /desktop on macOS saying Claude Desktop is not installed when it is in ~/Applications 
 Fixed OpenTelemetry repository attributes ( vcs.* ) missing from Claude Desktop sessions that start on a pre-started process 
 Fixed WebFetch passing "No response from model" to Claude as page content when the model reading the page returned no text; the call now fails with a clear error 
 Fixed screen reader mode delaying the prompt at startup when the system clock moved back while Claude Code was starting 
 Fixed a command's panel sometimes not coming back after a dialog closed, leaving no panel or prompt on screen until the next redraw 
 Fixed a project's MCP server being disconnected after the first message in a Claude Desktop Code tab session when the desktop app has an MCP server or extension of the same name 
 Fixed a turn ending with "API Error: EPROTO: The TLS handshake failed" when the connection broke partway through a reply; the partial reply is kept or the request is retried, as before 2.1.302 
 Fixed high memory use in long sessions that repeatedly read single lines from large files 
 Fixed fast mode losing replies, switching models or retrying for minutes when fast serving is rate-limited, overloaded or failing; it now tries standard speed on the same model first 
 Fixed one request carrying far more background agent reports than intended after Claude was stopped while several were waiting 
 Fixed messages from a Claude Desktop Code tab session to your other sessions staying paused after you typed while Claude was still working 
 Fixed claude agents ignoring --permission-mode , --dangerously-skip-permissions , --model , --effort or --agent typed before agents when a flag such as --verbose was also on the line 
 Fixed a case where Remote Control showed as off with "login expired" in the desktop app while its connection was still up, because the app was briefly unable to hand over a sign-in token 
 Fixed a Remote Control message sent with "Queue for later" reaching Claude in the middle of the running turn 
 Fixed the git status given to Claude at session start reading as clean when git status failed; it now reads as unavailable 
 Fixed the git status given to Claude at session start showing the first listed file as staged when its changes were not staged 
 Fixed a hang or out-of-memory crash when a connector in a cloud session lists resources with very long names 
 Fixed Remote Control showing as connected after its connection closed for good while the session's history was still uploading 
 Fixed screen reader mode turning off when you return to a conversation from agent view 
 Fixed screen reader mode y/n questions taking as yes a stray "y" at the end of text typed as the question opened 
 Fixed cloud sessions telling Claude that a host is probably not allowed when it is allowed and the network proxy could not connect to it 
 Fixed an MCP server sometimes showing as connected with no tools after it was reconnected or the session's directory changed while its tools were still loading 
 Fixed Bash commands sometimes running in the wrong folder when Claude sent several at once and an earlier one changed folders 
 Fixed files Claude sends from cloud and Remote Control sessions failing at once when an upload gets an HTTP 507 from a proxy; the upload now gets a second try 
 Fixed new messages not being saved, and claude -p , SDK and VS Code sessions hanging, when memory ran out while the transcript was being read 
 Fixed sign-in, token refresh and logout waiting indefinitely when something on the network accepts the connection but never answers the TLS handshake 
 Fixed a sent file showing under a different name in the Claude apps when its name hid text-direction or control characters; Claude now refuses to send such a file 
 Fixed sub-agent progress summaries running a request to its end after the model replied with a tool call 
 Fixed Bash reads such as grep -r foo "$PWD/src" asking for permission when the same command with the path typed out runs without asking 
 Fixed Claude apps gateway refusing to start when a desktop setting holds a field newer than the gateway, such as a managed MCP server's oauth.omitResource ; it now warns and serves it 
 Fixed Bash commands coming back empty for zsh users whose .zshrc sets KSH_OPTION_PRINT 
 macOS: Fixed "Unable to read managed policy settings" at startup when a valid MDM profile was slow to read: the read is retried once, and a timeout is now reported as a timeout 
 Fixed agent view erasing another agent view's saved input text when it restarted for an update with nothing typed 
 Fixed remote sessions giving no reply after a restart when a UserPromptSubmit hook blocked a replayed permission answer; these hooks no longer run on that replay 
 Fixed claude remote-control accepting a y typed without Enter at its first-run question when the terminal's input ended 
 Fixed Claude Desktop not showing spend limit warnings behind a Claude apps gateway whose policy has no code: rules 
 Fixed fullscreen sessions with some plugins ending with an error when a tool result that had got shorter scrolled off the top of the screen 
 Fixed prompt suggestions making extra API requests when the model replied with a tool call 
 Fixed PreToolUse mcp_tool hooks on stdio and HTTP MCP servers being skipped when their answer was over 16 MiB; the tool call is now refused 
 Fixed skill and command names holding a Bamum letter that some fonts draw as blank: they are now refused 
 Fixed claude -p on Linux exiting 0 in silence when a full NFS export or a used-up NFS quota lost transcript lines: it now prints an error and, in text and json output, exits 1 
 Fixed background agents being reported as stopped by the user, and refused a resume, when a service interrupted a cloud session and nobody pressed Stop 
 Fixed NotebookEdit reporting success to hooks and telemetry when the edit failed, for example when the notebook changed while the permission prompt was open 
 Fixed a blank screen or no answer at startup, and empty claude mcp list output, when a stored MCP sign-in record was null 
 Fixed the Artifact tool telling Claude to add filters when an artifact's database collection is too large to sort; it now says to read the collection page by page and sort the results 
 Fixed a restarted cloud session dropping a message with a large image when the restart came before Claude's first reply to it 
 Fixed a restarted cloud session leaving a subagent's message to the main conversation unanswered 
 Fixed Claude not being told when you stop or pause a running workflow, so it no longer says the workflow is still running 
 Improved the /model picker: "More models" is now an unnumbered row below every other, and older models open under it without renumbering the rest 
 Gateway: Improved spend limits on a busy replica, which now skips fewer checks and records spend sooner 
 Improved the Claude apps gateway's sign-in limit messages in Claude Code and on the /device page: they no longer name gateway settings, which the gateway's own log still names 
 Improved claude install and the install scripts: they finish 2 to 4 seconds sooner 
 Improved how soon a Remote Control session whose process crashed can pick up a new message 
 Windows: Improved startup and first-command time by finding programs on PATH without starting a helper process 
 Improved auto mode in headless sessions, the desktop app and VS Code: reports from background subagents that wait together are answered in one model call, as in the terminal 
 Improved the agent view's row for a claude --bg --worktree session that couldn't set up its worktree: it now shows the error from its beginning, not an internal tag or its last 200 characters 
 Improved the messages shown when an artifact is in another organization: /login is offered only if it's one of yours, and Claude now says where a copy may be after an account move 
 Improved sessions with more images than fit in one request: Claude is told whether it has already seen a dropped image, and repeat reads of an unchanged image are limited 
 Improved claude remote-control 's messages for an unanswered first-run question: each now says what to do next 
 Improved start-up time by loading trusted TLS certificates faster 
 Improved Claude apps gateway error messages to show the gateway's address without any user name or password 
 Improved the Claude apps gateway's spend limit error: the reset now shows in your local time, such as "resets 4pm (America/Los_An

[... truncated for safety ...]

</details>