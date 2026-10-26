---
id: inbox_59a3f47a
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-9-toml-cve-removal-windows-console-af69]]"
title: "v3.59.9 — toml CVE removal, Windows console path fixes, darwin 0.12.1 pickup"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.9
source: ruflo-releases
published_at: 2026-10-21T16:35:10+00:00
fetched_at: 2026-10-21T23:46:35.271285+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "移除未使用的 toml 依賴以消除高風險 CVE，並修正 console 在 Windows 的路徑處理問題。 **Why** toml 套件有未修補的高風險 CVE，但實際解析器其實是 @iarna/toml，因此移除屬於死碼清除，無功能變動。 **How** 以跨平台的 isAbsolutePath 檢查取代只判斷開頭斜線的邏輯，並修正路徑重組時多出前導斜線的問題。 **What** ADR、匯出與 transcript 儲存的專案資料夾查找原本拒絕 Windows 磁碟機代號與 UNC 路徑，現已支援（#4357、#4358）；@metaharness/darwin 升級至 0.12.1（#4359）。"
key_points:
  - "移除未使用的 toml 依賴（含未修補的高風險 CVE），實際解析器 @iarna/toml 不受影響"
  - "新增跨平台 isAbsolutePath 檢查，支援磁碟機代號與 UNC 路徑，console 更新至 0.44.7"
  - "@metaharness/darwin 升至 0.12.1，納入上游 metaharness#424 的 contrastive-deadline 修正"
tags: [ruflo, security, cve, windows-paths, dependency-cleanup]
topics: [security, engineering.architecture]
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.9 — toml CVE removal, Windows console path fixes, darwin 0.12.1 pickup

移除未使用的 toml 依賴以消除高風險 CVE，並修正 console 在 Windows 的路徑處理問題。

**Why** toml 套件有未修補的高風險 CVE，但實際解析器其實是 @iarna/toml，因此移除屬於死碼清除，無功能變動。

**How** 以跨平台的 isAbsolutePath 檢查取代只判斷開頭斜線的邏輯，並修正路徑重組時多出前導斜線的問題。

**What** ADR、匯出與 transcript 儲存的專案資料夾查找原本拒絕 Windows 磁碟機代號與 UNC 路徑，現已支援（#4357、#4358）；@metaharness/darwin 升級至 0.12.1（#4359）。

### 重點
- 移除未使用的 toml 依賴（含未修補的高風險 CVE），實際解析器 @iarna/toml 不受影響
- 新增跨平台 isAbsolutePath 檢查，支援磁碟機代號與 UNC 路徑，console 更新至 0.44.7
- @metaharness/darwin 升至 0.12.1，納入上游 metaharness#424 的 contrastive-deadline 修正

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.9)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 
 Security : removed the unused toml dependency (unpatched high-severity CVEs) from @claude-flow/cli , root, and @claude-flow/codex — @iarna/toml was already the actual parser in use, so this was dead-code removal with zero functional change ( #4357 ). 
 ruflo-console : fixed three related Windows path bugs — the ADR/export/transcript-save project-folder lookup rejected Windows drive-letter and UNC paths ( C:\... , \\server\share ) because the guard only checked for a leading / . Fixed with a proper cross-platform isAbsolutePath check, plus a path-reconstruction fix that no longer mangles a drive/UNC prefix with a bogus leading / ( #4358 , console 0.44.7). 
 Dependency pickup : @metaharness/darwin bumped to 0.12.1 , picking up the upstream contrastive-deadline fix from ruvnet/metaharness#424 (published as part of this release cycle since the upstream merge hadn't been version-bumped yet) ( #4359 ). 
 
 Notes 
 
 Full test suite showed pre-existing, unrelated intermittent flakiness in this release's worktree ( commands.test.ts ordering flake — matches tracked #4307 ; embeddings-init-skipped-download-3376.test.ts traced to pnpm workspace-sibling symlink non-determinism for @claude-flow/embeddings , unrelated to either merged change). Neither touches @claude-flow/embeddings . 
 
 Verification 
 
 node scripts/audit-leaf-versions-published.mjs — all 4 non-bundled leaves (cli-core 3.7.5, neural 3.0.0, shared 3.0.5, memory 3.0.8) confirmed published. 
 pnpm -r build clean across all 24 v3 workspace packages. 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) confirmed on the live npm registry at 3.59.9, latest / alpha / v3alpha dist-tags updated. 
 
 🤖 Generated with RuFlo

</details>