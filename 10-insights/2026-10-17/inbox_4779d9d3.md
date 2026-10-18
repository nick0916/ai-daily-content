---
id: inbox_4779d9d3
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-gitnexus-releases-rc-c8629f1b6ce4036f8222617fb07270e84c6a7-9483]]"
title: "rc/c8629f1b6ce4036f8222617fb07270e84c6a713e: fix(storage): preserve published graph on rebuild failure (#3613)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fc8629f1b6ce4036f8222617fb07270e84c6a713e
source: gitnexus-releases
published_at: 2026-10-17T17:45:11+00:00
fetched_at: 2026-10-18T03:18:46.227546+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus rc 標籤 rc/c8629f1b… 收錄 PR #3613「fix(storage): preserve published graph on rebuild failure」，屬 U1 工作單元。核心修正是重建（rebuild）失敗時保留已發布的 graph，不被半成品覆蓋；相關變更包括保留已完成的 recovery archive、在讀取 cache 前保留 quarantine。CI 新增 staged publication benchmark guard，並宣告 WAL replay probe 的決定性：有界 recovery 讀取會 drain 並丟棄 rows，只觀察 WAL replay 是否成功，既有 21 項 query-determinism 檢查通過。另有跨平台測試（含 Windows 增量 recovery 驗證），並將 POSIX 測試排除於 Windows 預估之外。共同作者為 Gergo Magyar。實務意義是 graph 索引採「先 staged 再發布」，失敗時可回復到上一個可用版本。"
key_points:
  - "PR #3613（U1）：rebuild 失敗時保留已發布 graph，並保留完成的 recovery archive 與 quarantine"
  - "WAL replay probe 只觀察 replay 成功，既有 21 項 query-determinism 檢查通過"
  - "新增 staged publication benchmark guard 與 Windows/跨平台 publication 測試"
tags: [gitnexus, storage, wal-replay, crash-recovery, ci]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/c8629f1b6ce4036f8222617fb07270e84c6a713e: fix(storage): preserve published graph on rebuild failure (#3613)

GitNexus rc 標籤 rc/c8629f1b… 收錄 PR #3613「fix(storage): preserve published graph on rebuild failure」，屬 U1 工作單元。核心修正是重建（rebuild）失敗時保留已發布的 graph，不被半成品覆蓋；相關變更包括保留已完成的 recovery archive、在讀取 cache 前保留 quarantine。CI 新增 staged publication benchmark guard，並宣告 WAL replay probe 的決定性：有界 recovery 讀取會 drain 並丟棄 rows，只觀察 WAL replay 是否成功，既有 21 項 query-determinism 檢查通過。另有跨平台測試（含 Windows 增量 recovery 驗證），並將 POSIX 測試排除於 Windows 預估之外。共同作者為 Gergo Magyar。實務意義是 graph 索引採「先 staged 再發布」，失敗時可回復到上一個可用版本。

### 重點
- PR #3613（U1）：rebuild 失敗時保留已發布 graph，並保留完成的 recovery archive 與 quarantine
- WAL replay probe 只觀察 replay 成功，既有 21 項 query-determinism 檢查通過
- 新增 staged publication benchmark guard 與 Windows/跨平台 publication 測試

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fc8629f1b6ce4036f8222617fb07270e84c6a713e)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(storage): preserve published graph on rebuild failure (U1) 
 
 
 test(storage): strengthen publication review coverage (U1) 
 
 
 test(storage): align publication evidence (U1) 
 
 
 fix(storage): retain completed recovery archives 
 
 
 fix(storage): preserve quarantines before cache reads 
 
 
 ci: run staged publication benchmark guard 
 
 
 fix(ci): declare WAL replay probe determinism 
 
 
 Document that the bounded recovery read drains and discards its rows. Only WAL replay success is observed; row identity and query behavior are unchanged. The existing 21 query-determinism checks pass. 
 
 
 test(storage): cover publication across platforms 
 
 
 test(ci): exclude POSIX suite from Windows estimates 
 
 
 test: allow native publication retry to finish 
 
 
 test: verify Windows incremental recovery 
 
 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>