---
id: inbox_ddf0e71c
date: 2026-10-19
source_ref: "[[00-inbox/2026-10-19/0206-gitnexus-releases-rc-47d63a0601eebfff6e69588d3cd8c3c1b0680-fed0]]"
title: "rc/47d63a0601eebfff6e69588d3cd8c3c1b06801ee: chore(vendor): update tree-sitter-dart to 1.0.0-g0038280 (#3633)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F47d63a0601eebfff6e69588d3cd8c3c1b06801ee
source: gitnexus-releases
published_at: 2026-10-19T14:41:34+00:00
fetched_at: 2026-10-20T02:13:07.478839+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "升級 tree-sitter-dart 並改用原生 extension type 解析，以避免相容性改寫遺失結構。 **Why** 舊的相容性改寫會遺失 generic extension body 與 implements 子句。 **How** 直接捕捉 parser 的原生節點，並註冊成員所有權，同時重新整理 Dart capture fingerprint。 **What** tree-sitter-dart 升級至 1.0.0-g0038280 並重建 native prebuilds（#3633）；另修正 WAL recovery 測試 fixture 的 checkpoint regression，並要求 blocked write 必須以實際錯誤碼退出，而非接受 subprocess timeout。"
key_points:
  - "改用 tree-sitter-dart 1.0.0-g0038280 的原生 extension type 節點，取代會遺失 generic body 與 implements 的改寫"
  - "Dart capture fingerprint 重新整理，並移除 preprocessing fixture 中的 Dart 清單"
  - "WAL recovery fixture 改為僅在封鎖寫入時強制 one-byte checkpoint，並要求實際錯誤退出"
tags: [tree-sitter, dart, parser, grammar-upgrade, wal]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/47d63a0601eebfff6e69588d3cd8c3c1b06801ee: chore(vendor): update tree-sitter-dart to 1.0.0-g0038280 (#3633)

升級 tree-sitter-dart 並改用原生 extension type 解析，以避免相容性改寫遺失結構。

**Why** 舊的相容性改寫會遺失 generic extension body 與 implements 子句。

**How** 直接捕捉 parser 的原生節點，並註冊成員所有權，同時重新整理 Dart capture fingerprint。

**What** tree-sitter-dart 升級至 1.0.0-g0038280 並重建 native prebuilds（#3633）；另修正 WAL recovery 測試 fixture 的 checkpoint regression，並要求 blocked write 必須以實際錯誤碼退出，而非接受 subprocess timeout。

### 重點
- 改用 tree-sitter-dart 1.0.0-g0038280 的原生 extension type 節點，取代會遺失 generic body 與 implements 的改寫
- Dart capture fingerprint 重新整理，並移除 preprocessing fixture 中的 Dart 清單
- WAL recovery fixture 改為僅在封鎖寫入時強制 one-byte checkpoint，並要求實際錯誤退出

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F47d63a0601eebfff6e69588d3cd8c3c1b06801ee)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

chore(vendor): update tree-sitter-dart to 1.0.0-g0038280 
 
 
 chore(vendor): rebuild native prebuilds (tree-sitter-dart) 
 
 
 Built by https://github.com/abhigyanpatwari/GitNexus/actions/runs/39212887661 
 
 fix(dart): use native extension type parsing 
 
 The upgraded grammar parses extension types directly. The compatibility 
rewrite loses generic extension bodies and implements clauses, so capture 
the native nodes and register their member ownership instead. 
 Refresh the Dart capture fingerprint after comparing the old grammar and 
emitter over the same fixture corpus. Keep the scaling budget unchanged. 
 Refs #3633 
 
 chore(vendor): rebuild native prebuilds (tree-sitter-dart) 
 
 Built by https://github.com/abhigyanpatwari/GitNexus/actions/runs/39239767139 
 
 fix: repair Dart parity and checkpoint regressions 
 
 Remove Dart from the preprocessing fixture inventory after retiring its 
hook. Use the parsed body boundary when reading extension-type heritage 
so named-record representations retain their implements clauses. 
 Seed the WAL recovery fixture with the normal checkpoint threshold, then 
force one-byte checkpoints only for the deliberately blocked write. 
Require an actual error exit instead of accepting a subprocess timeout. 
 Refs #3633 
 
 chore(vendor): rebuild native prebuilds (tree-sitter-dart) 
 
 Built by https://github.com/abhigyanpatwari/GitNexus/actions/runs/39248441688 
 
 Co-authored-by: gitnexus-release-bot[bot] &lt;gitnexus-release-bot[bot]@users.noreply.github.com&gt; 
Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>