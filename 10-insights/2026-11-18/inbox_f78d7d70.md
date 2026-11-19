---
id: inbox_f78d7d70
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-codex-releases-0-170-0-13ee]]"
title: "0.170.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.170.0
source: codex-releases
published_at: 2026-11-18T03:45:39+00:00
fetched_at: 2026-11-19T08:17:39.689664+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Codex 命令列工具的例行更新，新增即時語音通話並修補多項沙箱與連線問題。 **What** OpenAI Codex rust-v0.170.0 新增 TUI 的 WebRTC 即時語音通話協商、OpenTelemetry HTTP exporter 自動刷新認證標頭，以及實驗性的跨環境同名 MCP server 支援。修正項目包括過大的 WebSocket 請求改直接退回 HTTP、MCP OAuth 憑證競態、Windows 檔案替換與沙箱權限保留、子執行緒遺失沙箱限制等，並更新沙箱文件說明 permission profiles 與檔案系統規則。"
key_points:
  - "新增 TUI 內 WebRTC 即時語音通話協商（#61172）與 OTLP HTTP exporter 自動刷新認證標頭（#61028）"
  - "實驗性支援跨環境使用同名 MCP server（#60905），並修正 MCP OAuth 在取消、登入、登出時的憑證競態"
  - "沙箱相關修正：權限更新與子執行緒不再遺失既有沙箱限制，Windows 沙箱權限可保留；文件新增 permission profiles 說明"
tags: [openai-codex, codex-cli, mcp, sandbox, webrtc]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.170.0

Codex 命令列工具的例行更新，新增即時語音通話並修補多項沙箱與連線問題。

**What** OpenAI Codex rust-v0.170.0 新增 TUI 的 WebRTC 即時語音通話協商、OpenTelemetry HTTP exporter 自動刷新認證標頭，以及實驗性的跨環境同名 MCP server 支援。修正項目包括過大的 WebSocket 請求改直接退回 HTTP、MCP OAuth 憑證競態、Windows 檔案替換與沙箱權限保留、子執行緒遺失沙箱限制等，並更新沙箱文件說明 permission profiles 與檔案系統規則。

### 重點
- 新增 TUI 內 WebRTC 即時語音通話協商（#61172）與 OTLP HTTP exporter 自動刷新認證標頭（#61028）
- 實驗性支援跨環境使用同名 MCP server（#60905），並修正 MCP OAuth 在取消、登入、登出時的憑證競態
- 沙箱相關修正：權限更新與子執行緒不再遺失既有沙箱限制，Windows 沙箱權限可保留；文件新增 permission profiles 說明

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.170.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Added WebRTC negotiation for realtime voice calls in the TUI. ( #61172 ) 
 Added automatically refreshed authentication headers for OpenTelemetry HTTP exporters. ( #61028 ) 
 Added experimental support for using identically named MCP servers across environments. ( #60905 ) 
 
 Bug Fixes 
 
 Oversized WebSocket requests now fall back to HTTP without unnecessary retries. ( #60840 , #60841 ) 
 Fixed MCP OAuth credential races during cancellation, login, and logout. ( #60849 , #60981 ) 
 Improved automatic reconnection for Cloud conversations and preserved active recovery turns when clients reconnect. ( #60969 , #61014 ) 
 Fixed Windows file replacement, sandbox permission preservation, and runtime registration recovery. ( #60872 , #60943 , #60944 ) 
 Fixed permission updates and child threads losing existing sandbox restrictions. ( #60936 , #61134 ) 
 Removed duplicate file search results and fixed thread search snippets for queries containing whitespace. ( #60845 , #60846 ) 
 
 Documentation 
 
 Updated sandbox documentation to explain permission profiles and filesystem rules. ( #61133 ) 
 
 Changelog 
 Full Changelog: rust-v0.169.0...rust-v0.170.0 
 
 #60770 Derive history and notes tool schemas from typed requests @euroelessar 
 #60771 Preserve model-facing ID allocations in saved history @euroelessar 
 #60773 Resolve saved Daybreak choices for each subagent turn @sayan-oai 
 #60784 Centralize synchronous Guardian reviewer selection @felixxia-oai 
 #60839 Preserve retained assistant revisions across rollout replay @euroelessar 
 #60840 Fall back to HTTP immediately for oversized WebSocket requests @charliemarsh-oai 
 #60841 Honor advertised WebSocket message size limits @charliemarsh-oai 
 #60842 Make TUI thread titles resilient to generation failures @etraut-openai 
 #60845 Deduplicate file search results from overlapping roots @etraut-openai 
 #60846 Fix thread search snippets for whitespace-containing queries @etraut-openai 
 #60848 Enable incremental tool declarations by default for GCP @akira-oai 
 #60849 Protect MCP OAuth persistence from stale credential writes @mzeng-openai 
 #60871 Wait for the in-process initialization handshake to finish @goodman-oai 
 #60872 Fix Windows atomic writes and refresh build maintenance @zm-oai 
 #60882 Stabilize tracing in the cancellation timing test @bc-openai 
 #60897 Use the Responses API for issue label suggestions @GrantBirki 
 #60898 Include bundled bubblewrap in the root metadata test fixture @sayan-oai 
 #60904 Version answer display instructions and restrict unsupported payloads @psachdeva-oai 
 #60905 Keep same-named MCP servers separate across environments @sayan-oai 
 #60914 Reserve Guardian context budget for selected Code Mode exec results @felixxia-oai 
 #60929 Preserve Command Center task ownership across backend switches @bc-openai 
 #60936 Preserve legacy sandbox templates in TUI permission conversions @ioanbudea-OAI 
 #60942 Preserve thread-local model ID state across replay and compaction @euroelessar 
 #60943 Preserve file permissions during repeated Windows sandbox setup @zm-oai 
 #60944 Reconcile Windows runtime registration after service privilege errors @zm-oai 
 #60948 Report biometric type in user verification responses @bdavis-oai 
 #60962 Refactor shortcut overlay binding construction @bc-openai 
 #60964 Validate the issue labeler's API key before sending requests @GrantBirki 
 #60969 Reconnect idle Cloud conversations after transient stream loss @bc-openai 
 #60972 Lowercase service tier names in the model status line @bc-openai 
 #60977 Preserve allocated response item IDs in requests @euroelessar 
 #60981 Make reactive MCP OAuth refreshes cancellation-safe @mzeng-openai 
 #61014 Preserve active recovery turns when clients reconnect @apanasenko-oai 
 #61017 Record reasoning replay removal metrics @akira-oai 
 #61018 Extract HTTP headers helper execution into a shared crate @abhinav-oai 
 #61028 Add refreshable headers for OTLP HTTP exporters @abhinav-oai 
 #61129 Simplify non-curated plugin cache refreshes @smurching-oai 
 #61133 Use permission profiles in sandbox tests and documentation @ioanbudea-OAI 
 #61134 Normalize permission updates at session settings admission @ioanbudea-OAI 
 #61136 Compare resume sandbox overrides using permission profile labels @ioanbudea-OAI 
 #61138 Centralize filesystem helper sandbox preparation @viyatb-oai 
 #61141 Preserve multiline status lines in unfocused chat panes @fcoury-oai 
 #61144 Remove the legacy sandbox policy setter from Config @ioanbudea-OAI 
 #61153 Fix code-mode session admission retries for proxy HTTP 503 responses @seanh-oai 
 #61156 Ignore Hickory DNSSEC advisories while DNSSEC is disabled @swastik-oai 
 #61163 Reuse Guardian reviewer history for direct reviews @swastik-oai 
 #61167 Refactor TUI sidebar layout and focus handling around panels @fcoury-oai 
 #61172 Negotiate realtime voice calls in the TUI @zahan-oai

</details>