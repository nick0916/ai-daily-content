---
id: inbox_3afbde6d
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0145-codex-releases-0-168-0-147c]]"
title: "0.168.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.168.0
source: codex-releases
published_at: 2026-11-13T03:56:26+00:00
fetched_at: 2026-11-14T01:51:03.095437+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 0.168.0 新增並排側邊對話與模型供應商瀏覽，並支援音訊附件與動畫 GIF 生成。 **Why** 使用者在長時間對話中需要同時進行旁支討論，也需要在不同模型供應商間切換。 **How** 啟用 `features.tui_workspace` 後可在主對話旁開側邊對話窗格，可拖曳分隔線調整大小或以 leader z 縮放；模型供應商可在 Sessions → Model providers 選擇新對話的預設。 **What** OpenAI Codex 0.168.0（rust-v0.168.0）：新增音訊附件（使用音訊模型時可附錄音，已確認被拒的錄音後續回合會略過）、`features.image_generation_animation` 可生成/編輯動畫 GIF、tmux 內於 Ghostty/Kitty 顯示圖片預覽、`tui.notification_method = \"osc777\"` 終端通知。另修正歷史/續談依登入 ChatGPT 帳號過濾、steering 訊息在最終存檔時遺失、Windows 閒置本機 MCP server 佔用檔案 I/O 等問題，並在 `features.multi_agent` 被明確設定時警告改用 `agents.enabled`。"
key_points:
  - "`features.tui_workspace` 啟用並排側邊對話窗格，可拖曳調整與縮放"
  - "新增音訊附件支援；`features.image_generation_animation` 可生成或編輯動畫 GIF"
  - "`features.multi_agent` 明確設定時會警告，改用 `agents.enabled` 停用子代理工具"
tags: [codex, openai, release-notes, tui, multi-modal]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.168.0

OpenAI Codex 0.168.0 新增並排側邊對話與模型供應商瀏覽，並支援音訊附件與動畫 GIF 生成。

**Why** 使用者在長時間對話中需要同時進行旁支討論，也需要在不同模型供應商間切換。

**How** 啟用 `features.tui_workspace` 後可在主對話旁開側邊對話窗格，可拖曳分隔線調整大小或以 leader z 縮放；模型供應商可在 Sessions → Model providers 選擇新對話的預設。

**What** OpenAI Codex 0.168.0（rust-v0.168.0）：新增音訊附件（使用音訊模型時可附錄音，已確認被拒的錄音後續回合會略過）、`features.image_generation_animation` 可生成/編輯動畫 GIF、tmux 內於 Ghostty/Kitty 顯示圖片預覽、`tui.notification_method = "osc777"` 終端通知。另修正歷史/續談依登入 ChatGPT 帳號過濾、steering 訊息在最終存檔時遺失、Windows 閒置本機 MCP server 佔用檔案 I/O 等問題，並在 `features.multi_agent` 被明確設定時警告改用 `agents.enabled`。

### 重點
- `features.tui_workspace` 啟用並排側邊對話窗格，可拖曳調整與縮放
- 新增音訊附件支援；`features.image_generation_animation` 可生成或編輯動畫 GIF
- `features.multi_agent` 明確設定時會警告，改用 `agents.enabled` 停用子代理工具

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.168.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Browse model providers under Sessions → Model providers and choose the default for new chats. ( #59541 , #59722 ) 
 Enable features.tui_workspace to view a side conversation beside the main chat. Drag the divider to resize the panes or press leader z to zoom the focused pane. ( #58992 , #59527 , #59595 ) 
 Attach recordings when using an audio-capable model. Codex skips confirmed rejected recordings on later turns and uses clip duration to keep more short recordings in context. ( #59234 , #59268 ) 
 Enable features.image_generation_animation to generate or edit animated GIFs with optional frame count and timing controls. ( #59073 ) 
 Fullscreen Codex displays image previews and pets in tmux on Ghostty and Kitty with allow-passthrough all . ( #59579 , #59580 ) 
 Set tui.notification_method = "osc777" for terminal notifications. Approval notifications show longer command previews and distinguish terminal input from network access requests. ( #59256 ) 
 
 Bug Fixes 
 
 Local TUI history and resume pickers filter newly created threads by the signed-in ChatGPT account. ( #58918 ) 
 Open and resumed chats use their saved model provider after you change the default for new chats. ( #59503 ) 
 The TUI renders replies interrupted by tool calls as a single Markdown message and restores reasoning summaries when replaying a conversation. ( #59698 , #59700 ) 
 Steering messages reach running turns when sent during the final transcript save or after switching back to a long-running chat. ( #58877 , #58998 ) 
 Fuzzy file search gives filename matches more weight so matching parent directories are less likely to crowd them out. ( #59709 ) 
 Idle local MCP servers on Windows leave filesystem I/O available to the rest of Codex. ( #59726 ) 
 
 Documentation 
 
 The app-server reference covers listing model providers, creating custom gateways, and updating gateway, Bedrock, and GCP settings. ( #58845 , #58876 ) 
 
 Chores 
 
 Codex warns when features.multi_agent is explicitly configured and points to agents.enabled for disabling subagent tools. ( #59479 ) 
 Contributors can run Bazel CI jobs locally without BuildBuddy credentials. ( #59055 ) 
 
 Changelog 
 Full Changelog: rust-v0.167.0...rust-v0.168.0 
 
 #58766 Distinguish update handoffs in TUI startup telemetry @etraut-openai 
 #58767 Validate /fork before consuming the composer draft @etraut-openai 
 #58829 Accept agent follow-ups through native turn input delivery @won-openai 
 #58845 Add model provider discovery to the app server @alexsong-oai 
 #58876 Add model provider configuration writes to the app-server @alexsong-oai 
 #58877 Handle steers accepted during the final transcript flush @charliemarsh-oai 
 #58886 Preserve timestamp ties when paginating threads @jif-oai 
 #58890 Add a feature-gated account check for CLI thread resume @jif-oai 
 #58894 Support model catalog overrides for plugin guidance @goodman-oai 
 #58899 Add native patch support to direct Guardian review @swastik-oai 
 #58903 Support permission requests in direct Guardian review @swastik-oai 
 #58904 Add a standalone HTTP MCP server for the agent message board @jif-oai 
 #58908 Package the message board MCP connection as a plugin @jif-oai 
 #58909 Add an in-memory launcher for the message-board MCP server @jif-oai 
 #58918 Scope local history discovery to the current ChatGPT account @jif-oai 
 #58927 Fix live stream reflow at the allocated conversation width @fcoury-oai 
 #58931 Support direct Guardian review of patches invoked through exec_command @swastik-oai 
 #58933 Release message-board state before HTTP shutdown returns @jif-oai 
 #58935 Defer Guardian context trimming in elastic preparation @ioanbudea-OAI 
 #58936 Extract model-provider unit tests into separate files @ioanbudea-OAI 
 #58937 Verify queued network approval wakeups before polling again @seanh-oai 
 #58938 Skip attribution for direct MCP tool calls @victor-openai 
 #58939 Refine additional-context byte histogram buckets @akira-oai 
 #58940 Retire the daemon_auto_start feature flag @etraut-openai 
 #58945 Fix model selection after provider setup @etraut-openai 
 #58946 Preserve Guardian sender context for cloud deliveries with orbit IDs @felixxia-oai 
 #58950 Recover WebSocket transport after transient HTTP fallback @charliemarsh-oai 
 #58953 Support caller-owned sideband channels for realtime attachments @jiahao-oai 
 #58954 Add a thread-store builder with host cleanup support @felixxia-oai 
 #58955 Delete Guardian evidence boards when permanently deleting threads @felixxia-oai 
 #58956 Allow volatile World State sections to refresh after compaction @rhan-oai 
 #58957 Cache marketplace name mismatches during automatic upgrades @charliemarsh-oai 
 #58959 Recover inherited history from alternate rollout copies @charliemarsh-oai 
 #58960 Prefer indexed rollout paths when resolving ancestors @charliemarsh-oai 
 #58962 Preserve Guardian budget policy through review recovery @ioanbudea-OAI 
 #58963 Add host-owned turn admission to the agent runtime @rhan-oai 
 #58964 Stabilize and enable client tool output retention by default @jif-oai 
 #58966 Move protocol permissions tests into a separate file @viyatb-oai 
 #58969 Avoid unnecessary rendering during TUI history loading and insertion @etraut-openai 
 #58970 Keep automatic thread title saves off the TUI event loop @etraut-openai 
 #58971 Fix Escape handling in memory reset confirmation @imac-oai 
 #58973 Add opt-in MCP discovery for in-memory agent message boards @jif-oai 
 #58974 Bind final-message output before running sandboxed tools @viyatb-oai 
 #58975 Add usage accounting for host-owned agent runtimes @rhan-oai 
 #58978 Enable the segment heap on Windows CI runners @anp-oai 
 #58980 Record turn critical path metrics and trace fields @bkotsopoulos 
 #58983 Extend and bound exec-server session recovery @richardopenai 
 #58984 Allow hosts to restrict a thread's root-only capabilities @rhan-oai 
 #58986 Move agent message-board backend construction into the extension @jif-oai 
 #58988 Respect delivery boundaries for injected agent messages @won-openai 
 #58989 Keep HTTP fallback active for the rest of the session @charliemarsh-oai 
 #58990 Preserve modified Ctrl+C keys in active TUI views @imac-oai 
 #58992 Add opt-in side conversation panes to the TUI @fcoury-oai 
 #58996 Deliver environment hook decisions while output reads are queued @andrewgu-oai 
 #58998 Preserve steering when returning to a long-running turn @tamird 
 #59000 Allow hosted child threads to inherit a root session ID @rhan-oai 
 #59001 Test connection events against active environment selections @anp-oai 
 #59003 Preserve Guardian review framing under elastic context limits @ioanbudea-OAI 
 #59007 Add host cycling and saved defaults for new TUI conversations @bc-openai 
 #59009 Centralize filesystem permission resolution for sandbox enforcement @viyatb-oai 
 #59011 Add optional total token limits to elastic section configuration @ioanbudea-OAI 
 #59015 Make SQLite schema migrations safe for concurrent startup @dkovalenko-oai 
 #59016 Make observed thread metadata writes atomic and retryable @dkovalenko-oai 
 #59018 Add WebSocket connection metrics with reauthentication labels @bromano-oai 
 #59020 Preserve sandbox context in prepared MCP calls @sayan-oai 
 #59021 Allow concurrent readers of the installation ID @dkovalenko-oai 
 #59025 Remove strict third-party tool deferral in Code Mode Only @rishab-openai 
 #59028 Use prepared MCP owner permissions in Guardian reviews @sayan-oai 
 #59033 Add web search provider metadata and configuration @yitaoh-oai 
 #59034 Add model Search discovery to MCP bindings @yitaoh-oai 
 #59036 Resolve model-selected search providers with policy-aware fallback @yitaoh-oai 
 #59041 Expose assistant content token counts in completion notifications @aojiao-oai 
 #59043 Tie executor attachments to environment selection lifetimes @anp-oai 
 #59047 Decode live transcript updates in the cloud client @bc-openai 
 #59055 Run Bazel CI locally without BuildBuddy credentials @dkovalenko-oai 
 #59057 Tailor MCP doctor remediation to detected problems @etraut-openai 
 #59058 Classify daemon auto-start failures in TUI telemetry @etraut-openai 
 #59066 Add typed item lifecycle events to the cloud client @bc-openai 
 #59068 Enable Bedrock onboarding through the local daemon @etraut-openai 
 #59071 Enforce strict third-party tool deferral in Code Mode Only @rishab-openai 
 #59073 Add optional animated GIF output to image generation @Gan-Tu 
 #59075 Add paginated history reads to the cloud client @bc-openai 
 #59076 Clarify argument meanings in marketplace and guardian tests @fcoury-oai 
 #59082 Make native startup libraries available to Windows voice-host tests @fcoury-oai 
 #59107 Add opt-in reconsideration of Guardian denials @jif-oai 
 #59111 Normalize saved chat settings after model catalog refreshes @dpatel-oai 
 #59115 Preserve worker permissions across sibling-triggered reloads @jif-oai 
 #59118 Preserve Guardian denials when reconsideration times out @jif-oai 
 #59120 Allow dangerous-command review when sandbox approvals are disabled @jif-oai 
 #59124 Remove a redundant permission profile clone in exec policy tests @jif-oai 
 #59125 Add context to Guardian test setup failures @jif-oai 
 #59130 Add a shortcut to hide the focused side conversation pane @fcoury-oai 
 #59131 Clarify test failures and annotate a backend registration invariant @oh-openai 
 #59136 Parse Guardian review responses once @felixxia-oai 
 #59139 Route message-board notifications through agent mailboxes @jif-oai 
 #59154 Expose thread APIs for message board access @jif-oai 
 #59159 Move Guardian unit tests into their owning crates @felixxia-oai 
 #59161 Clarify token-count and screen-ownership arguments in tests @jif-oai 
 #59162 Move agent message board host integration to app-server @jif-oai 
 #59167 Move agent message board cleanup into the app server @jif-oai 
 #59177 Wire shared runtime authentication through threads and API clients @cooper-oai 
 #59192 Resolve saved Daybreak preferences against advertised model programs @jamy-OAI 
 #59201 Add cloud client message submission and turn interruption @bc-openai 
 #59208 Add shortcuts to focus the main composer and side conversation @fcoury-oai 
 #59217 Use the public managed-features constructor in the guardian config test @dylan-hurd-oai 
 #59219 Use Bazel's zstd library for zstd-sys @cayoub-oai 
 #59225 Revalidate Guardian denials when parent authorization changes @felixxia-oai 
 #59227 Preserve installer stderr when releasing the install lock @etraut-openai 
 #59228 Handle budget_reached as a terminal session budget error @yuning-oai 
 #59231 Fix test fixtures for Bazel sandboxes and Windows voice runtimes @dkovalenko-oai 
 #59232 Suppress macOS warnings in the V8 libc++ Bazel build @dkovalenko-oai 
 #59233 Use resolved filesystem permissions in Windows sandbox policies @viyatb-oai 
 #59234 Enable uploaded audio with durable rejection recovery @hung-oai 
 #59237 Budget retained file audio during remote compaction @hung-oai 
 #59238 Register the Guardian additional-context feature flag @akira-oai 
 #59239 Honor Guardian's additional-context setting for tool outputs @akira-oai 
 #59240 Mark deny-path parent directories created by the Windows MXC launcher @iceweasel-oai 
 #59242 Set seven-day garbage collection ages for Bazel caches @anp-oai 
 #59245 Expand per-turn critical path capture and split inference timing @taohong339 
 #59250 Expand Windows deny-read globs without invoking ripgrep @iceweasel-oai 
 #59251 Track automatic review overhead in critical-path durations @taohong339 
 #59253 Clarify TUI reconnect status for HTTP 429 stream errors @etraut-openai 
 #59254 Add stdin bearer authentication for exec-server registration @apanasenko-oai 
 #59255 Bind reusable backend clients to runtime authentication @cooper-oai 
 #59256 Add OSC 777 notifications and improve approval notification text @etraut-openai 
 #59257 Prese

[... truncated for safety ...]

</details>