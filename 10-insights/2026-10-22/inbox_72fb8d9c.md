---
id: inbox_72fb8d9c
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-ruflo-releases-v3-59-13-claims-cwd-global-cli-hook-fixe-b42a]]"
title: "v3.59.13 — claims cwd + global-CLI hook fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.13
source: ruflo-releases
published_at: 2026-10-22T02:10:37+00:00
fetched_at: 2026-10-23T01:01:29.591926+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓工具寫入正確的狀態位置，並讓 hook 呼叫釘住的那一份程式，而非 registry 上最新的版本。 **Why** 從子目錄啟動 MCP server 時，claims 會寫到錯的 store；hook 若 fallback 到 npx，會跟著 registry 的最新版走。 **How** claims 改用 getProjectCwd() 解析專案路徑；hook-handler.cjs 先檢查 npm global prefix、PATH 上的 ruflo/claude-flow 與 ~/.npm-global，找不到才 fallback 到 npx @claude-flow/cli。 **What** ruflo v3.59.13 修兩項 bug（#3210、#3368、#4368）；SessionStart 改用已安裝的全域版本。官方表示版本 lockstep 與 leaf 版本審計通過，3 個相關測試檔 35/35 通過。"
key_points:
  - "claims 持久化改用 getProjectCwd()，取代原本的 resolve(CLAUDE_DIR)，子目錄啟動的 claims-aware MCP server 不再漏掉 CLAUDE_FLOW_CWD 而寫錯 store（#3210）"
  - "hook-handler.cjs 依序檢查 npm global prefix、PATH 上的 ruflo / claude-flow、~/.npm-global，才 fallback 到 npx @claude-flow/cli（#3368、#4368）"
  - "SessionStart 刷新改用釘選的全域安裝，不再使用跟著 registry 最新版走的 npx 快取副本；驗證項目為 audit 腳本通過與 35/35 測試通過"
tags: [ruflo, claude-flow, mcp, hooks, patch-release]
topics: [agents.mcp, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.13 — claims cwd + global-CLI hook fixes

讓工具寫入正確的狀態位置，並讓 hook 呼叫釘住的那一份程式，而非 registry 上最新的版本。 **Why** 從子目錄啟動 MCP server 時，claims 會寫到錯的 store；hook 若 fallback 到 npx，會跟著 registry 的最新版走。 **How** claims 改用 getProjectCwd() 解析專案路徑；hook-handler.cjs 先檢查 npm global prefix、PATH 上的 ruflo/claude-flow 與 ~/.npm-global，找不到才 fallback 到 npx @claude-flow/cli。 **What** ruflo v3.59.13 修兩項 bug（#3210、#3368、#4368）；SessionStart 改用已安裝的全域版本。官方表示版本 lockstep 與 leaf 版本審計通過，3 個相關測試檔 35/35 通過。

### 重點
- claims 持久化改用 getProjectCwd()，取代原本的 resolve(CLAUDE_DIR)，子目錄啟動的 claims-aware MCP server 不再漏掉 CLAUDE_FLOW_CWD 而寫錯 store（#3210）
- hook-handler.cjs 依序檢查 npm global prefix、PATH 上的 ruflo / claude-flow、~/.npm-global，才 fallback 到 npx @claude-flow/cli（#3368、#4368）
- SessionStart 刷新改用釘選的全域安裝，不再使用跟著 registry 最新版走的 npx 快取副本；驗證項目為 audit 腳本通過與 35/35 測試通過

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.13)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 
 fix(claims): anchor MCP claims store to project cwd ( #3210 ) — claims persistence now resolves via getProjectCwd() instead of a raw resolve(CLAUDE_DIR) , matching every other file-backed MCP tool. A claims-aware MCP server launched in a subdirectory no longer misses CLAUDE_FLOW_CWD and silently writes to the wrong store. 
 fix(hooks): resolve globally-installed ruflo before falling back to npx ( #3368 , #4368 ) — hook-handler.cjs now checks npm's global prefix, ruflo / claude-flow on PATH, and ~/.npm-global before falling back to npx @claude-flow/cli . SessionStart refreshes now use the pinned global install instead of a second npx-cached copy that follows the registry's latest. 
 
 Verification 
 
 audit-umbrella-version-lockstep.mjs and audit-leaf-versions-published.mjs : both clean. 
 claims-project-cwd-3178.test.ts , hook-handler-global-cli.test.ts , helper-signing.test.ts : 35/35 passing against the built package. 
 Both source PRs went fully green in CI independently before merge. 
 
 🤖 Generated with RuFlo

</details>