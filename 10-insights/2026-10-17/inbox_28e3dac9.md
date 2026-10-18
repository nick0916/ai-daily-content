---
id: inbox_28e3dac9
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-gitnexus-releases-rc-bd20dde8254e39d2f551e42d84672e53dc1b5-2517]]"
title: "rc/bd20dde8254e39d2f551e42d84672e53dc1b5864: fix(taint): report inline and factory handler flows (#3612)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fbd20dde8254e39d2f551e42d84672e53dc1b5864
source: gitnexus-releases
published_at: 2026-10-17T20:22:58+00:00
fetched_at: 2026-10-18T03:18:46.227769+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus rc 標籤 rc/bd20dde8… 收錄 PR #3612「fix(taint): report inline and factory handler flows」，屬 U8 工作單元，關聯 issue #3489。修正讓 taint 分析能涵蓋 inline handler 與 factory 回傳的 handler：將 expression-handler 的 CFG summary 對應到不同的 graph function，同時不改變既有匿名 owner 的 identity，具名 function expression 則保持在其 lexical scope 內私有。CI 以 codec-safe 的產生顯示名稱保留位置式 function identity，驗證持久化的 hop 連續性，並移除先前針對 inline-flow 的準確度寬容值。測試也釘住 callback 的 capture，並明確保留「captured-closure」限制；另新增拒絕所有外層 factory source 的測試，且 native inline 證明測試在所有 OS 上執行。實務意義是 taint 追蹤對 Express 式 inline callback 與 HOC/factory 寫法的漏報減少，但 captured closure 仍是已知限制。"
key_points:
  - "PR #3612（U8，關聯 #3489）：將 expression-handler CFG summary 對應到獨立 graph function，不改變既有匿名 owner identity"
  - "移除 inline-flow 準確度寬容值，並驗證持久化 hop 連續性"
  - "仍保留 captured-closure 限制；inline 證明測試擴及所有 OS"
tags: [gitnexus, taint-analysis, cfg, inline-handler, static-analysis]
topics: [security, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/bd20dde8254e39d2f551e42d84672e53dc1b5864: fix(taint): report inline and factory handler flows (#3612)

GitNexus rc 標籤 rc/bd20dde8… 收錄 PR #3612「fix(taint): report inline and factory handler flows」，屬 U8 工作單元，關聯 issue #3489。修正讓 taint 分析能涵蓋 inline handler 與 factory 回傳的 handler：將 expression-handler 的 CFG summary 對應到不同的 graph function，同時不改變既有匿名 owner 的 identity，具名 function expression 則保持在其 lexical scope 內私有。CI 以 codec-safe 的產生顯示名稱保留位置式 function identity，驗證持久化的 hop 連續性，並移除先前針對 inline-flow 的準確度寬容值。測試也釘住 callback 的 capture，並明確保留「captured-closure」限制；另新增拒絕所有外層 factory source 的測試，且 native inline 證明測試在所有 OS 上執行。實務意義是 taint 追蹤對 Express 式 inline callback 與 HOC/factory 寫法的漏報減少，但 captured closure 仍是已知限制。

### 重點
- PR #3612（U8，關聯 #3489）：將 expression-handler CFG summary 對應到獨立 graph function，不改變既有匿名 owner identity
- 移除 inline-flow 準確度寬容值，並驗證持久化 hop 連續性
- 仍保留 captured-closure 限制；inline 證明測試擴及所有 OS

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fbd20dde8254e39d2f551e42d84672e53dc1b5864)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(taint): cover inline and returned handlers (U8) 
 
 Join expression-handler CFG summaries to distinct graph functions without changing existing anonymous-owner identities. Keep named function expressions private to their lexical scope. 
 Related: #3489 
 
 fix(ci): encode inline handler taint paths (U8) 
 
 Use codec-safe generated display names while preserving positional function identity. Verify persisted hop continuity and remove the repaired inline-flow accuracy allowance. 
 
 
 fix: keep anonymous names unbound (U8) 
 
 
 test: pin inline callback captures (U8) 
 
 
 ci: run inline taint guard (U8) 
 
 
 test: align inline handler contracts (U8) 
 
 
 Pin callback-owned call edges while preserving nested callable IDs and module-level HOC attribution. Assert repaired inline flows and the retained captured-closure limitation. 
 
 ci: run native inline proofs on all OSes (U8) 
 
 Register real-worker identity/CFG and persisted explain cases on the existing Windows/macOS matrix. Charge explicit scheduling estimates without changing watchdogs or runtime behavior. 
 
 test(taint): reject all enclosing factory sources 
 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>