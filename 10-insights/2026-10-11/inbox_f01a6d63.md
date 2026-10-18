---
id: inbox_f01a6d63
date: 2026-10-11
source_ref: "[[00-inbox/2026-10-11/0256-ruflo-releases-v3-56-5-graph-header-sniff-keeps-sqlite-e450]]"
title: "v3.56.5 — graph header sniff keeps SQLite locks"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.5
source: ruflo-releases
published_at: 2026-10-11T02:13:43+00:00
fetched_at: 2026-10-18T03:20:23.511250+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.56.5，是單一修正的 patch，僅影響 @claude-flow/cli。問題出在 graph-edge-writer 的加密 header 探測（sniff）會關閉原始 DB 檔案描述子（file descriptor），導致仍在使用中的 SQLite POSIX 鎖被釋放；現在改為在有界的子行程（bounded child process）中讀取 header，不再動到原本的 fd（#4044，修正 #4040）。發布的套件為 @claude-flow/cli、claude-flow、ruflo 3.56.5（latest、alpha、v3alpha），自 3.56.4 起沒有任何 leaf 套件變更。實務意義：POSIX 鎖的特性是關閉同一檔案的任一 fd 就會釋放該行程對該檔案的所有鎖，因此在同一行程內另開 fd 探測 header 可能破壞 SQLite 的並行保護，影響同時使用該 DB 的使用者（此段為對機制的推論，原文僅說明會 drop live SQLite POSIX locks）。"
key_points:
  - "graph-edge-writer 的加密 header 探測不再關閉原始 DB fd，避免丟失 SQLite POSIX 鎖（#4044，修正 #4040）"
  - "header 改在有界子行程中讀取；發布 cli、claude-flow、ruflo 3.56.5，無 leaf 套件變更"
tags: [ruflo, sqlite, posix-locks, patch-release]
topics: [agents.coding_agents, engineering.architecture]
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.5 — graph header sniff keeps SQLite locks

Ruflo 發布 v3.56.5，是單一修正的 patch，僅影響 @claude-flow/cli。問題出在 graph-edge-writer 的加密 header 探測（sniff）會關閉原始 DB 檔案描述子（file descriptor），導致仍在使用中的 SQLite POSIX 鎖被釋放；現在改為在有界的子行程（bounded child process）中讀取 header，不再動到原本的 fd（#4044，修正 #4040）。發布的套件為 @claude-flow/cli、claude-flow、ruflo 3.56.5（latest、alpha、v3alpha），自 3.56.4 起沒有任何 leaf 套件變更。實務意義：POSIX 鎖的特性是關閉同一檔案的任一 fd 就會釋放該行程對該檔案的所有鎖，因此在同一行程內另開 fd 探測 header 可能破壞 SQLite 的並行保護，影響同時使用該 DB 的使用者（此段為對機制的推論，原文僅說明會 drop live SQLite POSIX locks）。

### 重點
- graph-edge-writer 的加密 header 探測不再關閉原始 DB fd，避免丟失 SQLite POSIX 鎖（#4044，修正 #4040）
- header 改在有界子行程中讀取；發布 cli、claude-flow、ruflo 3.56.5，無 leaf 套件變更

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: one fix in @claude-flow/cli. 
 
 The graph-edge-writer encryption-header sniff no longer closes the raw DB file descriptor, which dropped live SQLite POSIX locks; the header is read in a bounded child process ( #4044 , fixes #4040 ). 
 
 Published: @claude-flow/cli, claude-flow, ruflo 3.56.5 (latest, alpha, v3alpha). No leaf package changed since 3.56.4.

</details>