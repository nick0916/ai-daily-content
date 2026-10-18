---
id: inbox_fb21f961
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-codex-releases-0-163-0-8d12]]"
title: "0.163.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.163.0
source: codex-releases
published_at: 2026-10-15T21:33:06+00:00
fetched_at: 2026-10-18T03:03:22.641316+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex（source 為 codex-releases，url 為 github.com/openai/codex）發布 0.163.0。新功能包含：/config 可跨類別搜尋偏好並即時套用設定、回應進行中可送出 follow-up 即時 steer（interrupt 也會停止進行中的 Code Mode cells 及其巢狀 tool calls）、/keymap 可設定 leader key（預設 Ctrl+X，語音靜音改為 F9）、/daemon 可重啟受管理的背景伺服器，以及獨立的唯讀工具（skill、memory、對話歷史查詢）可平行執行。Daybreak 對符合資格的帳號預設啟用，codex exec 也可在伺服器開放時以 OpenAI API key 選用。安全與修復方面：resume 已存檔 thread 會還原權限與網路核准；network proxy 在 DNS 查詢前先檢查授權、拒絕重複 Host header、並防止 credential alias 繞過 inspection hooks；另修正 Windows/WSL 貼上與本地/遠端指令輸出的問題。文件更新了 GPT-6 系列的遷移指引（reasoning、tool use、data residency），並釐清 Linux sandbox 以 bubblewrap 做檔案系統隔離、seccomp 做 syscall 過濾；Chores 方面不再內建 patched zsh，改用標準 shell executor，使用已退役 shell flags 的設定會收到遷移通知。changelog 另可見 sandbox integrity 檢查（bubblewrap、macOS Seatbelt 後端）與 Windows MXC sandbox 等工作，但原文在中途截斷，完整清單無法確定。"
key_points:
  - "預設啟用 instant interrupts 與 Code Mode 中斷（#51812、#51835），回應中途可直接 steer，並同步停止 Code Mode cells 與巢狀 tool calls"
  - "network proxy 強化：DNS 查詢前先授權檢查、拒絕重複 Host header、防止 credential alias 繞過 inspection hooks（#51650、#52661、#53506）"
  - "移除內建 patched zsh 改用標準 shell executor，使用舊 shell flags 的設定會收到遷移通知（#52160、#52213）"
tags: [openai-codex, release-notes, sandbox, code-mode, network-proxy]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.163.0

OpenAI Codex（source 為 codex-releases，url 為 github.com/openai/codex）發布 0.163.0。新功能包含：/config 可跨類別搜尋偏好並即時套用設定、回應進行中可送出 follow-up 即時 steer（interrupt 也會停止進行中的 Code Mode cells 及其巢狀 tool calls）、/keymap 可設定 leader key（預設 Ctrl+X，語音靜音改為 F9）、/daemon 可重啟受管理的背景伺服器，以及獨立的唯讀工具（skill、memory、對話歷史查詢）可平行執行。Daybreak 對符合資格的帳號預設啟用，codex exec 也可在伺服器開放時以 OpenAI API key 選用。安全與修復方面：resume 已存檔 thread 會還原權限與網路核准；network proxy 在 DNS 查詢前先檢查授權、拒絕重複 Host header、並防止 credential alias 繞過 inspection hooks；另修正 Windows/WSL 貼上與本地/遠端指令輸出的問題。文件更新了 GPT-6 系列的遷移指引（reasoning、tool use、data residency），並釐清 Linux sandbox 以 bubblewrap 做檔案系統隔離、seccomp 做 syscall 過濾；Chores 方面不再內建 patched zsh，改用標準 shell executor，使用已退役 shell flags 的設定會收到遷移通知。changelog 另可見 sandbox integrity 檢查（bubblewrap、macOS Seatbelt 後端）與 Windows MXC sandbox 等工作，但原文在中途截斷，完整清單無法確定。

### 重點
- 預設啟用 instant interrupts 與 Code Mode 中斷（#51812、#51835），回應中途可直接 steer，並同步停止 Code Mode cells 與巢狀 tool calls
- network proxy 強化：DNS 查詢前先授權檢查、拒絕重複 Host header、防止 credential alias 繞過 inspection hooks（#51650、#52661、#53506）
- 移除內建 patched zsh 改用標準 shell executor，使用舊 shell flags 的設定會收到遷移通知（#52160、#52213）

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.163.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Open /config to search preferences across categories, change supported settings immediately, and see which changes require a restart. ( #52990 , #53429 ) 
 Send a follow-up while Codex is responding to steer it immediately. Interrupting a turn also stops active Code Mode cells and their nested tool calls. ( #51812 , #51835 ) 
 Configure a leader key in /keymap . The default is Ctrl+X , shortcut hints stay open until you choose or cancel, and voice mute moves to F9 . ( #52273 ) 
 Restart a managed background server from /daemon . Codex warns about work the restart could interrupt, then reconnects automatically. ( #53173 ) 
 Codex can run independent read-only tools in parallel, including skill, memory, and conversation-history lookups. ( #52245 ) 
 Daybreak is enabled by default for eligible accounts. codex exec can also select it with an OpenAI API key when the server offers access. ( #53701 , #53717 ) 
 
 Bug Fixes 
 
 Resuming a saved thread restores its permissions and network approvals, while respecting explicit overrides and current managed policy. ( #53150 , #53419 , #53424 ) 
 The network proxy now checks permission before a DNS lookup, rejects duplicate Host headers, and prevents credential aliases from bypassing inspection hooks. ( #51650 , #52661 , #53506 ) 
 Return to an existing side conversation with /side after switching threads. Answers to pending prompts also go back to the thread that asked. ( #52184 , #53436 ) 
 On Windows, Ctrl+V and Shift+Insert paste text as well as images. On WSL, repeated pastes reuse the clipboard reader, and copy attempts time out instead of hanging. ( #53224 , #52967 , #53453 ) 
 Local commands finish promptly when a child keeps an output pipe open. Remote commands preserve late-arriving output so the final poll can still collect it. ( #52652 , #53331 , #53622 ) 
 codex exec no longer prints the same file diff again after an unrelated command. ( #53444 ) 
 
 Documentation 
 
 Updated the bundled OpenAI Docs guidance for migrations to the GPT-6 family, including model-specific reasoning, tool use, and data residency considerations. ( #51768 ) 
 Clarified how the Linux sandbox uses bubblewrap for filesystem isolation and seccomp for syscall filtering. ( #52610 ) 
 
 Chores 
 
 Codex now uses its standard shell executor and no longer bundles a patched zsh . Configurations using the retired shell flags receive a migration notice. ( #52160 , #52213 ) 
 Reduced Linux and macOS release package size by stripping symbols from packaged binaries while preserving them in the original build outputs. ( #52178 ) 
 
 Changelog 
 Full Changelog: rust-v0.162.0...rust-v0.163.0 
 
 #51539 Add completion-aware realtime attachment and session-scoped detach @zahan-oai 
 #51547 Add a Windows MXC sandbox opt-out @iceweasel-oai 
 #51556 Complete dynamic tool lifecycles on cancellation @mikelam-oai 
 #51575 Expose package assembly helpers and support gzip DotSlash artifacts @bolinfest 
 #51595 Add thread ID exclusions to thread/list @btraut-openai 
 #51602 Distinguish thread listing failures from exhausted history @btraut-openai 
 #51611 Signal abandonment of unanswered MCP elicitations @nicksteele-oai 
 #51627 Stabilize Guardian snapshot prefixes by separating assistant context @jif-oai 
 #51642 Fix retained context handling for typed section content @jif-oai 
 #51650 Require hostname authorization before proxy DNS lookups @jif-oai 
 #51651 Persist Guardian review failures for reports across restarts @jif-oai 
 #51652 Record telemetry for AGENTS.md changes made by apply_patch @jif-oai 
 #51678 Move Windows sandbox tests into a dedicated integration binary @jif-oai 
 #51683 Roll back stale Guardian reviews before reusing reviewer history @olliem-oai 
 #51689 Wait for helper completion in HTTP header cancellation tests @jif-oai 
 #51690 Add a feature flag for Code Mode tool description ordering @swastik-oai 
 #51704 Honor tool-description-first ordering in Code Mode @swastik-oai 
 #51710 Fix a discovery race in the external auth refresh test @jgershen-oai 
 #51734 Load persisted sender context for Guardian reviews @jif-oai 
 #51755 Reuse MCP handler metadata for cache comparisons @owenlin0 
 #51761 Reduce tool metadata cloning in the code-mode runtime @akira-oai 
 #51768 Expand OpenAI Docs migration guidance to the GPT-6 model family @kkahadze-oai 
 #51775 Prevent recursive Tokio tracing in telemetry and SQLite logs @zbarsky-openai 
 #51786 Preserve sandbox overrides across execution requests @iceweasel-oai 
 #51794 Advertise Ultrafast for GPT-6.1 Sol on Amazon Bedrock @celia-oai 
 #51800 Remove duplicate field initializers in extension registry tests @anp-oai 
 #51808 Preserve diagnostic reasons for MCP user verification failures @berkdeniz-oai 
 #51812 Enable instant interrupts by default @pakrym-oai 
 #51819 Migrate the MXC sandbox to the 1.0.0 SDK @iceweasel-oai 
 #51822 Avoid sharing violations when repairing Windows runtime ACLs @johnl-oai 
 #51823 Share MCP binding tool metadata with prepared calls @owenlin0 
 #51828 Add policy-based file contents integrity checks @iceweasel-oai 
 #51831 Add MXC sandbox integrity dependency and policy preparation @iceweasel-oai 
 #51835 Enable code mode interruption by default @won-openai 
 #51840 Add a bubblewrap backend for sandbox integrity checks @iceweasel-oai 
 #51841 Add a macOS Seatbelt backend for sandbox integrity @iceweasel-oai 
 #51842 Add a sandbox integrity runner with outcome and timing metrics @iceweasel-oai 
 #51843 Run sandbox integrity checks before commands and filesystem operations @iceweasel-oai 
 #51847 Preserve Cargo package names in Bazel Rust builds @dkovalenko-oai 
 #51848 Align Bazel release builds with Cargo and fix platform compatibility @dkovalenko-oai 
 #51849 Fix package smoke tests for Cargo and Bazel debug symbols @dkovalenko-oai 
 #51850 Add Bazel release staging archives @dkovalenko-oai 
 #51855 Add Bazel support to the Codex package build action @dkovalenko-oai 
 #51856 Build Bazel release artifacts alongside Cargo artifacts @dkovalenko-oai 
 #51857 Add an app-server prompt prefix compatibility test @jif-oai 
 #51865 Use readable plugin mentions without suppressing same-name skills @canvrno-oai 
 #51866 Preserve line breaks and links in multiline async questions @pash-openai 
 #51868 Record tool registration metrics for each sampling request @akira-oai 
 #51872 Keep global app-server config independent of the launch directory @etraut-openai 
 #51884 Add experimental prediction forks that inherit parent context @liame-oai 
 #51890 Add the missing mxc-sdk UTF-8 resource patch for Bazel @iceweasel-oai 
 #51892 Preserve tool call completeness when recorded arguments are truncated @ningyi-oai 
 #51893 Record metrics for incremental tool updates @akira-oai 
 #51895 Report specific reasons for WebSocket continuation failures @pakrym-oai 
 #51896 Preserve native errors in Windows sandbox ACL diagnostics @alishobeiri-oai 
 #51897 Use a dedicated matcher for network domain policies @rafael-oai 
 #51908 Honor the user input setting for asynchronous questions @mandal-OAI 
 #51930 Support model-specific function description prefixes @tz-openai 
 #51963 Attribute compaction analytics to the correct voice session @reia-oai 
 #51974 Log Windows sandbox availability and backend selection @iceweasel-oai 
 #52034 Preserve agent state when unloading idle multi-agent v2 children @jif-oai 
 #52040 Add regression coverage for cancelled agent reloads @jif-oai 
 #52048 Cover instant interruption in steered-input persistence tests @jif-oai 
 #52061 Run Guardian conversation classifiers concurrently and preserve action order @felixxia-oai 
 #52062 Add scenario coverage for worker context across idle eviction @jif-oai 
 #52065 Require assessment text in the Guardian parser @ioanbudea-OAI 
 #52081 Fix idle cleanup for disconnected multi-agent v2 children @jif-oai 
 #52119 Expose originating tool call metadata in command environments @leo-oai 
 #52160 Remove the patched zsh shell execution backend @jif-oai 
 #52164 Make environment context date and timezone configurable @surajs-oai 
 #52176 Show AWS GovCloud guidance at startup and remember acknowledgment @jackz100 
 #52177 Set a User-Agent for package archive downloads @bolinfest 
 #52178 Strip symbols from source-built release package binaries @bolinfest 
 #52182 Expose a verified sandbox launcher to local MCP servers @bolinfest 
 #52183 Add optional descriptions to agent message board channels @jif-oai 
 #52184 Preserve side conversations across thread navigation @etraut-openai 
 #52193 Enforce managed MXC requirements on Windows @iceweasel-oai 
 #52195 Track source attribution for individual context parts @tz-openai 
 #52200 Allow plugin toggles while searching and preserve filters on refresh @fcoury-oai 
 #52203 Expose Codex lifecycle status in iTerm2 sessions @fcoury-oai 
 #52213 Stop bundling patched zsh in Codex packages @jif-oai 
 #52215 Enforce application network policy in standalone MCP commands @lsingh-oai 
 #52220 Add configurable default plugin activation policy @stevenlee-oai 
 #52223 Enforce application network policy for daemon updates @jackz100 
 #52225 Fix config rebuild call in the Windows MXC preference test @virajrai-oai 
 #52226 Include foreground activity in iTerm2 session status @fcoury-oai 
 #52228 Honor API-key feature gates in TUI Daybreak selection @julee-oai 
 #52234 Support request IDs in exec-server WebSocket handshakes @mattj-openai 
 #52235 Recover gRPC code-mode sessions after missing-session errors @surajs-oai 
 #52241 Preserve subagent capabilities independently of forked history @anp-oai 
 #52245 Enable parallel execution for read-only tools @zamoshchin-openai 
 #52250 Add opt-in Guardian trust for orchestrator connector identities @ankushg 
 #52256 Normalize formatting in docs, web assets, and sample scripts @anp-oai 
 #52268 Preserve large arguments in executed tool call metadata @ningyi-oai 
 #52270 Enable text selection in the fullscreen TUI footer @fcoury-oai 
 #52273 Add configurable persistent leader shortcuts to the TUI @fcoury-oai 
 #52274 Add structured tracing for Guardian reviews and background scoring @ioanbudea-OAI 
 #52277 Preserve UTF-8 byte semantics in network domain matching @rafael-oai 
 #52278 Honor custom OTLP metrics exporters when analytics is disabled @jackz100 
 #52288 Remove duplicate field initializers from extension registry tests @anp-oai 
 #52295 Emit one developer notice per incremental namespace update batch @akira-oai 
 #52299 Make Bazel release jobs advisory @anp-oai 
 #52302 Add opt-in credential masking for proxied sandboxed sessions @winston-openai 
 #52304 Persist remote-control RPC preferences in managed daemon settings @etraut-openai 
 #52325 Track history initialization in Responses turn metadata @anp-oai 
 #52329 Remove per-content source attribution metadata @anp-oai 
 #52330 Clamp wrapped source ranges before remapping terminal hyperlinks @bc-openai 
 #52337 Add durable thread read state with revision-checked updates @btraut-openai 
 #52350 Expose experimental durable thread read state in the app server @btraut-openai 
 #52363 Expand realtime v3 voice support @jacksonmoody-oai 
 #52381 Preserve per-session routing for gRPC code mode @cassirer-openai 
 #52384 Notify subscribers when thread read state changes @btraut-openai 
 #52395 Add experimental app-server thread read-state updates @btraut-openai 
 #52418 Avoid an extra blank quote line when pasting text with a trailing newline @bc-openai 
 #52535 Add opt-in history prefix preservation for full agent forks @jif-oai 
 #52557 Forward clipboard copies to the terminal in Herdr sessions @fcoury-oai 
 #52568 Expose message board permissions and structured denials @jif-oai 
 #52591 Fix races in remote environment and session replacement tests @jif-oai 
 #52608 Upgrade hyper to 1.11.1 and test connection closure @jif-oai 
 #52610 Align Linux sandbox names and docs with bubblewrap and seccomp @bolinfest 
 #52621 Ad

[... truncated for safety ...]

</details>