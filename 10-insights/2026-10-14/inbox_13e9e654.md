---
id: inbox_13e9e654
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-ruflo-releases-v3-56-10-tui-pictures-and-looks-mcp-proj-fff7]]"
title: "v3.56.10 — TUI pictures and looks, MCP project cwd and daemon fixes, memory and analyze fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.10
source: ruflo-releases
published_at: 2026-10-14T16:33:28+00:00
fetched_at: 2026-10-18T03:19:47.139415+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo（ruvnet/ruflo；@claude-flow/cli、claude-flow、ruflo）於 2026-10-14 發布 3.56.10 patch 版本（latest、alpha、v3alpha），CLI 固定使用 @claude-flow/memory 3.0.5 與 @claude-flow/cli-core 3.7.3，並精確綁定 shared/security/codex 3.0.5；#4178 變更了簽章 helper 並已重簽。新增 ruflo tui 可繪製 console 的圖像、外觀與動畫（console 0.44.x），選項包括 --look bbs|orbital|plain、--fps、--anim、--pictures、--boot 與 --view；終端機回報 0 欄時以預設大小繪製。變更：ruflo init 的 v3 implementation skills 改為 opt-in（--full 才加入）。修正涵蓋：MCP server 在 session 專案中啟動並忽略指向家目錄或檔案系統根目錄的 CLAUDE_FLOW_CWD、清除重複或殭屍 daemon、每個 MCP session 只有一個 node 程序（#3987–#3989）；記憶體搜尋預設門檻校準並提供 near-miss 提示、memory_export 同時讀取 CLI store 與 AgentDB、TieredMemoryStore 可召回多詞與自然語言查詢；失敗的工具結果會被記錄、hooks 從專案根目錄執行；無效 gate 與不支援的步驟 fail closed；agent health 改由實際執行結果推導；analyze 依 diff 內容與 commit 主旨分類，加密路徑標為安全敏感；安全掃描能偵測 import 之後的插值 exec 呼叫，且 npm audit 失敗時回報 \"could not scan\" 而非誤報乾淨。@claude-flow/browser 為獨立套件，這次未重新發布。"
key_points:
  - "新增 ruflo tui：--look bbs|orbital|plain、--fps、--anim、--pictures、--boot、--view（console 0.44.x，#4182、#4188）"
  - "MCP/daemon 修正：忽略指向家目錄或根目錄的 CLAUDE_FLOW_CWD、停止重複/殭屍 daemon、每個 MCP session 一個 node 程序（#3987–#3989）"
  - "安全掃描：npm audit 失敗改回報 \"could not scan\" 而非乾淨結果（#4154）；偵測 import 後的插值 exec 呼叫（#4166）；invalid gate fail closed（#4164）"
tags: [ruflo, claude-flow, tui, mcp-server, memory, fail-closed]
topics: [agents.frameworks, agents.mcp, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.10 — TUI pictures and looks, MCP project cwd and daemon fixes, memory and analyze fixes

Ruflo（ruvnet/ruflo；@claude-flow/cli、claude-flow、ruflo）於 2026-10-14 發布 3.56.10 patch 版本（latest、alpha、v3alpha），CLI 固定使用 @claude-flow/memory 3.0.5 與 @claude-flow/cli-core 3.7.3，並精確綁定 shared/security/codex 3.0.5；#4178 變更了簽章 helper 並已重簽。新增 ruflo tui 可繪製 console 的圖像、外觀與動畫（console 0.44.x），選項包括 --look bbs|orbital|plain、--fps、--anim、--pictures、--boot 與 --view；終端機回報 0 欄時以預設大小繪製。變更：ruflo init 的 v3 implementation skills 改為 opt-in（--full 才加入）。修正涵蓋：MCP server 在 session 專案中啟動並忽略指向家目錄或檔案系統根目錄的 CLAUDE_FLOW_CWD、清除重複或殭屍 daemon、每個 MCP session 只有一個 node 程序（#3987–#3989）；記憶體搜尋預設門檻校準並提供 near-miss 提示、memory_export 同時讀取 CLI store 與 AgentDB、TieredMemoryStore 可召回多詞與自然語言查詢；失敗的工具結果會被記錄、hooks 從專案根目錄執行；無效 gate 與不支援的步驟 fail closed；agent health 改由實際執行結果推導；analyze 依 diff 內容與 commit 主旨分類，加密路徑標為安全敏感；安全掃描能偵測 import 之後的插值 exec 呼叫，且 npm audit 失敗時回報 "could not scan" 而非誤報乾淨。@claude-flow/browser 為獨立套件，這次未重新發布。

### 重點
- 新增 ruflo tui：--look bbs|orbital|plain、--fps、--anim、--pictures、--boot、--view（console 0.44.x，#4182、#4188）
- MCP/daemon 修正：忽略指向家目錄或根目錄的 CLAUDE_FLOW_CWD、停止重複/殭屍 daemon、每個 MCP session 一個 node 程序（#3987–#3989）
- 安全掃描：npm audit 失敗改回報 "could not scan" 而非乾淨結果（#4154）；偵測 import 後的插值 exec 呼叫（#4166）；invalid gate fail closed（#4164）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.10 (latest, alpha, v3alpha). The CLI pins @claude-flow/memory 3.0.5 ( #4183 ) and @claude-flow/cli-core 3.7.3 ( #3987 ), both published earlier, plus shared 3.0.5, security 3.0.5 and codex 3.0.5 exactly. Signed helpers changed in #4178 and were re-signed there. 
 Added 
 
 ruflo tui draws the console's pictures, looks and motion (console 0.44.x, #4182 , #4188 ): --look bbs|orbital|plain , --fps , --anim , --pictures , --boot , and any console view with --view . It draws at the default size when the terminal reports 0 columns ( #4160 , @martinvlad ). 
 
 Changed 
 
 ruflo init : the v3 implementation skills are opt-in ( --full adds them), like agents.v3 ( #4140 , #4139 , @z4forzubair ). 
 
 Fixed 
 
 MCP server and daemons : the server starts in the session project and ignores a CLAUDE_FLOW_CWD that names the home directory or a filesystem root ( cli-core 3.7.3); user-level claims resolve through os.homedir() on Windows; duplicate or zombie daemons per workspace are stopped ( #3987 , @socrates6969 ). Trajectory counts persist across processes and daemon jobs feed learning ( #3988 , @socrates6969 ). One node process per MCP session, with node:http and the security barrel kept off the startup path ( #3989 , @socrates6969 ). 
 Console reads the project on Windows (a drive path is absolute) ( #4177 , #4175 ). Neural data dir resolves through the project cwd; stored worker error text is capped. 
 Hooks and core : failed tool outcomes are recorded, hooks run from the project root, telemetry stays off the tool path ( #4178 ). 
 Memory : calibrated default search threshold with near-miss hints ( #4184 , #4129 ); memory_export reads the CLI store as well as AgentDB ( #4186 , #4148 ); the AgentDB directory is created before the bridge opens it ( #4155 , #4132 , @martinvlad ); TieredMemoryStore recalls multi-word and natural-language queries ( memory 3.0.5, #4183 , #4152 ). 
 Intelligence : long memories recalled for short route prompts ( #4172 , @rudycelekli ); SONA reinforces the nearest pattern for near-identical tasks ( #4185 , #4134 ); AIDefence learns missed threats and autopilot learning loads ( #4187 , #4147 , #4146 ). 
 Workflow and agents : invalid gates and unsupported steps fail closed ( #4164 ); agent health derives from observed execution outcomes ( #4167 ) ( @rudycelekli ). 
 Analyze : classification from diff content and commit subjects, safe Git revision ranges, encryption paths flagged security-sensitive, accurate reviewer-role docs ( #4165 , #4162 , #4169 , #4163 , @rudycelekli ). 
 Security scan : interpolated exec calls after imports are detected ( #4166 , @rudycelekli ); a failed npm audit reports "could not scan" instead of a clean tree ( #4154 , #4124 , @martinvlad ). 
 Clear "not installed" message for @ruvector/rvagent-wasm ; only new patterns are counted ( #4179 , #3979 ). Skills, plugin contracts and ruvector/neural/kg surfaces ( #4181 ). 
 
 Notes 
 
 @claude-flow/browser (agent-browser bump, #4130 ) is a standalone package outside this train and was not republished. 
 
 Thanks 
 @rudycelekli , @martinvlad , @proffesor-for-testing , @ronmikailov , @z4forzubair , @socrates6969 , @nicholas-ruest and @pacphi for the fixes and reports across 3.56.6 to 3.56.10.

</details>