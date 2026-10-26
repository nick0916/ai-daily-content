---
id: inbox_bf1bb74d
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-ruflo-releases-v3-58-1-cwe-22-fix-cli-parser-fix-tokeno-2b7e]]"
title: "v3.58.1 — CWE-22 fix, CLI parser fix, TokenOptimizer fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.58.1
source: ruflo-releases
published_at: 2026-10-20T08:29:54+00:00
fetched_at: 2026-10-21T00:12:51.012829+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修補 Ruflo hooks_codemod 的路徑越界漏洞（CWE-22），避免工具讀寫專案目錄以外的檔案。 **Why** resolveTargets() 以未錨定的字串前綴判斷路徑是否在專案內，名稱以專案目錄開頭的兄弟目錄（如 cwd-staging）會被誤判為專案內。 **How** 兩處呼叫改為以路徑分隔符為邊界比對，與程式庫中既有的 isWithinPrefix() 做法一致。 **What** v3.58.1 另修正 CommandParser.parse() 把非首次出現的 `--` 當成旗標結束符、吞掉查詢字串的問題，並修正 TokenOptimizer 呼叫不存在的 editCode 方法；後者以 @claude-flow/integration@3.0.2 獨立發布。"
key_points:
  - "路徑包含檢查用 abs.startsWith(cwd) 會被 sibling 目錄繞過，改為路徑分隔符邊界比對（#4312 / #4313）"
  - "CommandParser 會把非首次出現的 `--` 吞掉，現在保留為 positional（#4310 / #4314）"
  - "TokenOptimizer 初始化誤用未實例化的 AgentBooster 類別，改用 getAgentBooster() 工廠（#4311 / #4315）"
tags: [path-traversal, cwe-22, security-fix, command-parser, prefix-check]
topics: [security, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.58.1 — CWE-22 fix, CLI parser fix, TokenOptimizer fix

修補 Ruflo hooks_codemod 的路徑越界漏洞（CWE-22），避免工具讀寫專案目錄以外的檔案。

**Why** resolveTargets() 以未錨定的字串前綴判斷路徑是否在專案內，名稱以專案目錄開頭的兄弟目錄（如 cwd-staging）會被誤判為專案內。

**How** 兩處呼叫改為以路徑分隔符為邊界比對，與程式庫中既有的 isWithinPrefix() 做法一致。

**What** v3.58.1 另修正 CommandParser.parse() 把非首次出現的 `--` 當成旗標結束符、吞掉查詢字串的問題，並修正 TokenOptimizer 呼叫不存在的 editCode 方法；後者以 @claude-flow/integration@3.0.2 獨立發布。

### 重點
- 路徑包含檢查用 abs.startsWith(cwd) 會被 sibling 目錄繞過，改為路徑分隔符邊界比對（#4312 / #4313）
- CommandParser 會把非首次出現的 `--` 吞掉，現在保留為 positional（#4310 / #4314）
- TokenOptimizer 初始化誤用未實例化的 AgentBooster 類別，改用 getAgentBooster() 工廠（#4311 / #4315）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.58.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

[3.58.1] - 2026-10-20 
 Patch release: @claude-flow/cli , claude-flow , ruflo 3.58.1. Bug fixes only. 
 Fixed 
 
 Security : hooks_codemod 's resolveTargets() path-containment check used an unanchored abs.startsWith(cwd) string-prefix comparison — a sibling directory merely starting with the project directory's name (e.g. cwd -staging) passed containment, letting this live, CLAUDE.md-recommended tool read and write outside the project root (CWE-22). Anchored both call sites at a path-separator boundary, matching the already-correct isWithinPrefix() pattern used elsewhere in this codebase ( #4312 / #4313 ). 
 CommandParser.parse() flipped parsingFlags = false on every literal -- token it saw, not just the first — a later -- supplied as an ordinary operand (e.g. a search query of exactly -- ) was silently swallowed instead of being kept as a positional ( #4310 / #4314 ). 
 TokenOptimizer.optimizedEdit() called agentBooster.editCode() , a method that has never existed on agentic-flow/agent-booster 's real exports; a separate bug in the same file's initialize() picked the un-instantiated AgentBooster class instead of calling the package's getAgentBooster() factory. Published standalone as @claude-flow/integration@3.0.2 ( #4311 / #4315 ). 
 CI reliability: scripts/__tests__/probe-mod-guards.test.mjs (a node:test file) was never categorized into either the vitest-baseline or vitest-excluded list, causing an intermittent, unrelated "no test suite found" failure on PRs that don't touch it ( #4316 ). 
 
 Added 
 
 ruflo-console 0.44.6: the compact nav's menu, groups, search and page tabs are now separated by a dim │ bar instead of just a gap ( #3664 ).

</details>