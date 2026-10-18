---
id: inbox_a5e6b2f0
date: 2026-10-11
source_ref: "[[00-inbox/2026-10-11/0256-ruflo-releases-v3-56-4-plugin-trust-and-helper-security-4eed]]"
title: "v3.56.4 — plugin-trust and helper security hardening, MCP/task fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.4
source: ruflo-releases
published_at: 2026-10-11T01:08:38+00:00
fetched_at: 2026-10-18T03:20:52.718024+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo（npm 套件 @claude-flow/cli、claude-flow、ruflo）發布 v3.56.4 patch 版，重點是 plugin 信任機制與 helper 的安全強化，同時修正 MCP／task 與 Node 24 相容性問題。安全面包含：全零的 placeholder registry trust anchor 不再被視為可信（#3948）、plugins upgrade 不再繞過 install gate（#3951）、plugin/helper 搜尋路徑止於 node_modules（#3986）、session helper 路徑與 module-root 強化（#3949）、helper CLI 改由 helper root 執行且不再對 HELPER_ROOT 做 shell 插值（#3990）、user-level settings 固定使用 home helpers（#3952）、task_assign 拒絕 proto id（#3967）。修正面包含 Node 24 下 better-sqlite3 abort（#3955）、agentic-flow root import 會執行其 CLI（#3958）、MCP resource cache 過期寫入被隔離（#4019）、security scan 程式碼 pattern 誤報（#3999），另有多項 MCP/task/CLI 修正。效能上 graph path search 約快 94 倍（#3977）。使用 Ruflo 的開發者與 agent 編排團隊，特別是會載入第三方 plugin 的情境，建議升級。"
key_points:
  - "Plugin 供應鏈防護：全零 placeholder registry trust anchor 不再背書（#3948）、plugins upgrade 不再繞過 install gate（#3951）、plugin/helper locator 止於 node_modules（#3986）"
  - "Helper 與 task 強化：helper CLI 從 helper root 執行並移除 HELPER_ROOT 的 shell 插值（#3990）、task_assign 拒絕 proto id（#3967，屬 prototype pollution 類防護）"
  - "相容性與效能：修正 Node 24 better-sqlite3 abort（#3955）；graph path search 約快 94 倍（#3977）"
tags: [ruflo, claude-flow, plugin-trust, supply-chain-security, mcp]
topics: [security, agents.frameworks, agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.4 — plugin-trust and helper security hardening, MCP/task fixes

Ruflo（npm 套件 @claude-flow/cli、claude-flow、ruflo）發布 v3.56.4 patch 版，重點是 plugin 信任機制與 helper 的安全強化，同時修正 MCP／task 與 Node 24 相容性問題。安全面包含：全零的 placeholder registry trust anchor 不再被視為可信（#3948）、plugins upgrade 不再繞過 install gate（#3951）、plugin/helper 搜尋路徑止於 node_modules（#3986）、session helper 路徑與 module-root 強化（#3949）、helper CLI 改由 helper root 執行且不再對 HELPER_ROOT 做 shell 插值（#3990）、user-level settings 固定使用 home helpers（#3952）、task_assign 拒絕 proto id（#3967）。修正面包含 Node 24 下 better-sqlite3 abort（#3955）、agentic-flow root import 會執行其 CLI（#3958）、MCP resource cache 過期寫入被隔離（#4019）、security scan 程式碼 pattern 誤報（#3999），另有多項 MCP/task/CLI 修正。效能上 graph path search 約快 94 倍（#3977）。使用 Ruflo 的開發者與 agent 編排團隊，特別是會載入第三方 plugin 的情境，建議升級。

### 重點
- Plugin 供應鏈防護：全零 placeholder registry trust anchor 不再背書（#3948）、plugins upgrade 不再繞過 install gate（#3951）、plugin/helper locator 止於 node_modules（#3986）
- Helper 與 task 強化：helper CLI 從 helper root 執行並移除 HELPER_ROOT 的 shell 插值（#3990）、task_assign 拒絕 proto id（#3967，屬 prototype pollution 類防護）
- 相容性與效能：修正 Node 24 better-sqlite3 abort（#3955）；graph path search 約快 94 倍（#3977）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: plugin-trust and helper security fixes, MCP/task fixes, Node 24 sqlite fix. 
 Published: @claude-flow/cli, claude-flow, ruflo 3.56.4 (latest, alpha, v3alpha); leaves memory 3.0.4, integration 3.0.1, plugins 3.0.2, mcp 3.1.1, security 3.0.4. 
 Security: placeholder (all-zero) registry trust anchor no longer vouches ( #3948 ); plugins upgrade no longer bypasses the install gate ( #3951 ); plugin/helper locators stop at node_modules ( #3986 ); session helper path and module-root hardening ( #3949 ); helper CLI runs from the helper root, no shell interpolation of HELPER_ROOT ( #3990 ); user-level settings pin home helpers ( #3952 ); task_assign rejects proto ids ( #3967 ). 
Fixes: Node 24 better-sqlite3 abort ( #3955 ); agentic-flow root import runs its CLI ( #3958 ); MCP resource cache stale writes fenced ( #4019 ); security scan code-pattern false positives ( #3999 ); MCP/task/CLI fixes #3975 #3974 #3970 #3969 #3968 #3980 #3947 ; graph path search ~94x faster ( #3977 ). 
 Full list: CHANGELOG.md.

</details>