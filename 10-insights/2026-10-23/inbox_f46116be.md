---
id: inbox_f46116be
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-gitnexus-releases-rc-48f108a58a99c06ba21b9af5652597ee7e56f-ef60]]"
title: "rc/48f108a58a99c06ba21b9af5652597ee7e56f81d: docs: simplify guides and verify receiver gaps (#3694)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F48f108a58a99c06ba21b9af5652597ee7e56f81d
source: gitnexus-releases
published_at: 2026-10-23T08:06:03+00:00
fetched_at: 2026-10-24T03:56:02.636748+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 GitNexus 文件整理成「路線圖只談未來、細節另外連結」。 **How** 以新的量測結果刷新基線與各語言清單，並執行先前被排除的 C++、Rust、PHP、Dart、Vue 寫法。 **What** 路線圖限縮為未來工作與驗收條件；編輯器、CLI、MCP、部署與 wiki 說明移到連結指南並保留命令範例；新增 receiver 缺口盤點，暴露 Dart await 的錯誤 owner 邊；呼叫丟失計數維持不變。"
key_points:
  - "路線圖只保留未來工作與驗收條件，細節指南以連結取代，並修正過時的 onboarding 說明"
  - "新增各語言 ingestion 缺口盤點，並檢查精確 declaration ID"
  - "暴露 Dart await 的錯誤 owner 邊；call-drop 計數維持不變"
tags: [documentation, roadmap, language-coverage, receiver-resolution, code-intelligence]
topics: [engineering.architecture, engineering.evals]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/48f108a58a99c06ba21b9af5652597ee7e56f81d: docs: simplify guides and verify receiver gaps (#3694)

把 GitNexus 文件整理成「路線圖只談未來、細節另外連結」。 **How** 以新的量測結果刷新基線與各語言清單，並執行先前被排除的 C++、Rust、PHP、Dart、Vue 寫法。 **What** 路線圖限縮為未來工作與驗收條件；編輯器、CLI、MCP、部署與 wiki 說明移到連結指南並保留命令範例；新增 receiver 缺口盤點，暴露 Dart await 的錯誤 owner 邊；呼叫丟失計數維持不變。

### 重點
- 路線圖只保留未來工作與驗收條件，細節指南以連結取代，並修正過時的 onboarding 說明
- 新增各語言 ingestion 缺口盤點，並檢查精確 declaration ID
- 暴露 Dart await 的錯誤 owner 邊；call-drop 計數維持不變

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F48f108a58a99c06ba21b9af5652597ee7e56f81d)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

docs: align resolution architecture and roadmap 
 
 
 docs: add language ingestion gap inventories 
 
 
 test: audit receiver gap targets and coverage 
 
 
 Check exact declaration IDs, expose the Dart await wrong-owner edge, and execute previously excluded C++, Rust, PHP, Dart and Vue shapes. Refresh the baseline and all language inventories from fresh measurements; call-drop counts remain unchanged. 
 
 docs: focus roadmap and shorten project README 
 
 Keep the resolution roadmap limited to future work and acceptance criteria. Move detailed editor, CLI, MCP, deployment and wiki instructions into linked guides, preserve their command examples, and correct stale onboarding claims. 
 
 docs: correct setup and audit descriptions 
 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>