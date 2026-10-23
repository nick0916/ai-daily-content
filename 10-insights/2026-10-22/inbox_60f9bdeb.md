---
id: inbox_60f9bdeb
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-ruflo-releases-v3-59-17-stop-advertising-a-dead-init-me-3415]]"
title: "v3.59.17 — stop advertising a dead init memory-config key"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.17
source: ruflo-releases
published_at: 2026-10-22T13:28:58+00:00
fetched_at: 2026-10-23T01:01:19.147352+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 RuFlo init 產生的設定檔中一個無效的記憶體路徑設定鍵。 **Why** 初始化設定檔列出了 runtime 不會讀取的 memory.persistPath，會誤導使用者。 **How** 移除該無效鍵，並在註解中指向實際控制儲存的 JSON 設定鍵。 **What** 對應 PR #4392；init 相關測試 4/4 通過。發布 PR 的 Test Suite 曾因既有不穩定測試 doctor-memory-driver-3321.test.ts 失敗一次，重跑後通過，程式碼未改。"
key_points:
  - "移除 init 產生的 .claude-flow/config.yaml 中無效的 memory.persistPath 鍵，註解改指向實際控制儲存的 JSON 設定鍵（#4392）"
  - "init-dual-native-2636-2637.test.ts 4/4 通過；版本一致性與 leaf-drift 審計通過"
  - "發布 PR 的 Test Suite 因既有不穩定測試 doctor-memory-driver-3321.test.ts 失敗一次，重跑通過，程式碼未改"
tags: [config-drift, init-config, memory-store, ruflo]
topics: [agents.frameworks]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.17 — stop advertising a dead init memory-config key

修正 RuFlo init 產生的設定檔中一個無效的記憶體路徑設定鍵。 **Why** 初始化設定檔列出了 runtime 不會讀取的 memory.persistPath，會誤導使用者。 **How** 移除該無效鍵，並在註解中指向實際控制儲存的 JSON 設定鍵。 **What** 對應 PR #4392；init 相關測試 4/4 通過。發布 PR 的 Test Suite 曾因既有不穩定測試 doctor-memory-driver-3321.test.ts 失敗一次，重跑後通過，程式碼未改。

### 重點
- 移除 init 產生的 .claude-flow/config.yaml 中無效的 memory.persistPath 鍵，註解改指向實際控制儲存的 JSON 設定鍵（#4392）
- init-dual-native-2636-2637.test.ts 4/4 通過；版本一致性與 leaf-drift 審計通過
- 發布 PR 的 Test Suite 因既有不穩定測試 doctor-memory-driver-3321.test.ts 失敗一次，重跑通過，程式碼未改

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 
 fix(init): stop advertising a memory path the runtime ignores ( #4392 ) — the init -generated .claude-flow/config.yaml no longer lists the dead memory.persistPath key; a comment now points at the real JSON config key that actually controls the store. 
 
 Verification 
 
 init-dual-native-2636-2637.test.ts : 4/4 passing against the built package. 
 audit-umbrella-version-lockstep.mjs , leaf-drift check, audit-leaf-versions-published.mjs : all clean. 
 v3 pnpm -r build : clean across all packages. 
 The release PR's own Test Suite (ubuntu-latest) job failed once on an unrelated pre-existing test ( doctor-memory-driver-3321.test.ts ); confirmed non-deterministic — the exact same source commit had passed that same job on #4392 's own CI run — and a rerun went green with no code changes. 
 
 🤖 Generated with RuFlo

</details>