---
id: inbox_d96f0525
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-gitnexus-releases-rc-0e7b3d6fad9ba57e05c1af90874374586953c-cb57]]"
title: "rc/0e7b3d6fad9ba57e05c1af90874374586953c489: fix(mcp): report cross-function explain lines 1-based (#3635)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F0e7b3d6fad9ba57e05c1af90874374586953c489
source: gitnexus-releases
published_at: 2026-10-20T07:54:52+00:00
fetched_at: 2026-10-21T00:12:18.778354+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 GitNexus 跨函式 explain 回報的行號與編輯器一致，改為 1-based。 **Why** 跨函式分析的 source、sink 與 hops 行號直接沿用 tree-sitter 的 0-based 座標，比函式宣告行在編輯器中少一行，且與同一回應中的 intra-procedural 結果不一致。 **How** 對 source.line、sink.line、hops[].line 套用既有的 toDisplayLine 轉換（與 context、query、impact 相同），並在回應說明中註明這些為宣告行。 **What** GitNexus 修正 PR #3635，對應 issue #3491；整合測試以 fixture 驗證 source.ts 第 7 行的 handle 與 sink.ts 第 6 行的 runIt。"
key_points:
  - "source.line、sink.line、hops[].line 原為 tree-sitter 0-based，現經 toDisplayLine 轉為 1-based"
  - "回應說明改為註明這些行號是宣告行"
  - "整合測試斷言精確行號：source.ts 第 7 行 handle、sink.ts 第 6 行 runIt"
tags: [mcp, line-numbering, bug-fix, tree-sitter, code-analysis]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/0e7b3d6fad9ba57e05c1af90874374586953c489: fix(mcp): report cross-function explain lines 1-based (#3635)

讓 GitNexus 跨函式 explain 回報的行號與編輯器一致，改為 1-based。

**Why** 跨函式分析的 source、sink 與 hops 行號直接沿用 tree-sitter 的 0-based 座標，比函式宣告行在編輯器中少一行，且與同一回應中的 intra-procedural 結果不一致。

**How** 對 source.line、sink.line、hops[].line 套用既有的 toDisplayLine 轉換（與 context、query、impact 相同），並在回應說明中註明這些為宣告行。

**What** GitNexus 修正 PR #3635，對應 issue #3491；整合測試以 fixture 驗證 source.ts 第 7 行的 handle 與 sink.ts 第 6 行的 runIt。

### 重點
- source.line、sink.line、hops[].line 原為 tree-sitter 0-based，現經 toDisplayLine 轉為 1-based
- 回應說明改為註明這些行號是宣告行
- 整合測試斷言精確行號：source.ts 第 7 行 handle、sink.ts 第 6 行 runIt

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F0e7b3d6fad9ba57e05c1af90874374586953c489)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(mcp): report cross-function explain lines 1-based 
 
 The interprocedural branch of explain passed the endpoints' and hops' 
graph startLine through unchanged. Those are 0-based (tree-sitter rows), 
so every cross-function source, sink and hop sat one line above the 
function's declaration in an editor, while the intra-procedural findings 
of the same response were already 1-based. source.line, sink.line and 
hops[].line now go through toDisplayLine like context, query and impact 
( #2377 ), and the response note says these are declaration lines. 
 The interproc integration block asserts the exact fixture lines: handle on 
line 7 of source.ts, runIt on line 6 of sink.ts. 
 Fixes #3491 
 
 fix(review): remove repaired accuracy allowance 
 
 
 Co-authored-by: Gergő Magyar gergomagyar@icloud.com 
Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>