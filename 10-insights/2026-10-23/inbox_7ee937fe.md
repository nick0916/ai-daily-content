---
id: inbox_7ee937fe
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-ruflo-releases-v3-60-0-rure-reverse-engineering-tools-c-3954]]"
title: "v3.60.0 — ruRE reverse-engineering tools, console page, security fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.60.0
source: ruflo-releases
published_at: 2026-10-23T17:27:43+00:00
fetched_at: 2026-10-24T03:56:49.936215+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 工具的失敗不再被當成成功，並補上安全漏洞與新的唯讀逆向分析工具。 **Why** 原文多項修正指向同一問題：多個工具在操作失敗時仍回報成功，且 MCP session id 可被猜測。 **How** 新增六個只解析檔案、不執行檔案的 MCP 工具，並修正成功判斷與 session id 的產生方式。 **What** RuFlo v3.60.0 新增 rure_extract_asar、rure_analyze_binary 等六個 MCP 工具，ruflo-console 0.45.0 加入 ruRE 頁面；neural_compress 的 prune 會刪光所有 pattern 卻回報成功，現已拒絕執行；MCP session id 改用 crypto.randomUUID()。"
key_points:
  - "新增六個唯讀逆向工具（rure_extract_asar、rure_analyze_js_app、rure_analyze_binary 等），解析檔案不執行，字串經 AIDefence 掃描；已知缺口是 .asar 暫存資料夾未清理，且可讀取任何程序可讀的路徑。"
  - "多個「假成功」修正：neural_compress 的 prune 會刪除所有 pattern 仍回報成功；github_pr_manage 在 gh 失敗時仍回報成功；daa_agent_adapt 把 performanceScore: 0 記成 0.8 的成功。"
  - "安全修正：agentbbs 的 room id 可含 ..，導致 room log 路徑逃出 .agentbbs；MCP session id 原本由計數器、時間戳與六個 Math.random() 字元組成，現改用 crypto.randomUUID()。"
tags: [ruflo, mcp, reverse-engineering, silent-failure, security]
topics: [agents.mcp, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.60.0 — ruRE reverse-engineering tools, console page, security fixes

讓 AI 工具的失敗不再被當成成功，並補上安全漏洞與新的唯讀逆向分析工具。

**Why** 原文多項修正指向同一問題：多個工具在操作失敗時仍回報成功，且 MCP session id 可被猜測。

**How** 新增六個只解析檔案、不執行檔案的 MCP 工具，並修正成功判斷與 session id 的產生方式。

**What** RuFlo v3.60.0 新增 rure_extract_asar、rure_analyze_binary 等六個 MCP 工具，ruflo-console 0.45.0 加入 ruRE 頁面；neural_compress 的 prune 會刪光所有 pattern 卻回報成功，現已拒絕執行；MCP session id 改用 crypto.randomUUID()。

### 重點
- 新增六個唯讀逆向工具（rure_extract_asar、rure_analyze_js_app、rure_analyze_binary 等），解析檔案不執行，字串經 AIDefence 掃描；已知缺口是 .asar 暫存資料夾未清理，且可讀取任何程序可讀的路徑。
- 多個「假成功」修正：neural_compress 的 prune 會刪除所有 pattern 仍回報成功；github_pr_manage 在 gh 失敗時仍回報成功；daa_agent_adapt 把 performanceScore: 0 記成 0.8 的成功。
- 安全修正：agentbbs 的 room id 可含 ..，導致 room log 路徑逃出 .agentbbs；MCP session id 原本由計數器、時間戳與六個 Math.random() 字元組成，現改用 crypto.randomUUID()。

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.60.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Minor release: @claude-flow/cli , claude-flow , ruflo 3.60.0, with @claude-flow/hooks 3.0.2 and @claude-flow/mcp 3.1.2 published standalone. Backward-compatible additions (six new reverse-engineering MCP tools, a ruRE page in the console) plus security and correctness fixes. The 3.59.x patch releases are not itemised here; this lists what changed since 3.59.17. 
 Added 
 
 ruRE: static reverse engineering (ruflo-rure 0.4.2, ADR-0001..0005 of the plugin). Six read-only MCP tools — rure_extract_asar , rure_analyze_js_app , rure_find_feature , rure_analyze_binary (ELF, PE, Mach-O), rure_analyze_dotnet (metadata only) and rure_analyze_evm (bytecode inventory) — that parse a file and never run it. Every string taken from the analyzed file passes the AIDefence gate; results say screened: false when the scanner is unavailable. New dependency: @electron/asar . Known gaps: EVM and P/Invoke handling validated on built fixtures only; the .asar scratch folder is not cleaned up; the tools read any path the process can read. 
 ruflo-console 0.45.0: a ruRE page in the TOOLS group (ADR-494) with a row per tool, a project-relative sample field, and results cleaned of terminal escapes. The tools are needed in the CLI: on 3.59.17 and older the rows say to update. 
 agentic-qe-fleet marketplace pin moved to v3.15.12 ( #4419 ). 
 
 Fixed 
 
 Security : agentbbs accepted .. in a room id, letting a room log path escape .agentbbs ( #4416 ). 
 Security ( @claude-flow/mcp 3.1.2): MCP session ids were a counter, a timestamp and six Math.random() characters, so they were guessable; they now use crypto.randomUUID() ( #4418 ). 
 neural_compress with method: "prune" deleted every stored neural pattern and reported success, because pattern usage is never recorded; it now refuses and leaves the store untouched ( #4428 , #4423 ). 
 github_pr_manage merge/close and github_issue_track update/close reported success when gh failed or no record matched, and PR actions ignored owner / repo ; they now fail with gh 's error and pass --repo ( #4425 , #4424 ). 
 daa_agent_adapt recorded performanceScore: 0 , and an omitted score, as a 0.8 success; 0 is now a failure, an omitted score records none, and an out-of-range score is rejected ( #4427 , #4426 ). 
 The bridge search looked at only the newest 1000 rows, hiding older ones; the window is back to 10000 and configurable with CLAUDE_FLOW_SEARCH_WINDOW ( #4405 , #4397 ). 
 The cost-tracker Stop hook stored its record in the session's project instead of CLAUDE_FLOW_CWD ( #4407 ), and doctor could not read the version of a claude.cmd shim on Windows ( #4408 ) ( #4397 ). 
 The AgentDB embedder rescue applied only to the first store in a process ( #4421 ). 
 transport use slim , agent publish and swarm join now report "not configured" when the installed AGNTCY SDK lacks the function they call, instead of failing at the call site ( #4409 , #4376 ). 
 update all honours --dry-run ( #4398 ). 
 WorkerDaemon kept two timers for a worker enabled twice ( #4412 ). In @claude-flow/hooks 3.0.2: an explicit stop is no longer undone by a pending auto-restart ( #4413 ), a duplicate cluster is counted once ( #4415 ), and fallback embeddings no longer block the event loop for up to 10 s ( #4422 ). 
 ruflo-ai-team 's annotation-review.md missed two tools ( #4394 ); the federation peer's standalone TLS lock moved to patched rustls, webpki and quinn-proto ( #4414 ). 
 
 Packages 
 
 @claude-flow/cli , claude-flow , ruflo 3.60.0 
 @claude-flow/hooks 3.0.2 and @claude-flow/mcp 3.1.2 (standalone) 
 
 Also fixed on the way to this release: the CLI's startup update check treated any older registry version with a higher patch number as an update and auto-installed it (a downgrade); an update must now be strictly newer ( #4432 ). 
 Install: npx ruflo@latest . Console: claude plugin marketplace update ruflo &amp;&amp; claude plugin update ruflo-console@ruflo , then restart Claude Code. 
 🤖 Generated with RuFlo

</details>