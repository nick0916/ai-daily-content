---
id: inbox_0fa1585e
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-ruflo-releases-v3-61-1-rure-can-read-a-folder-you-allow-71c1]]"
title: "v3.61.1 — ruRE can read a folder you allow (console 0.48.0)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.61.1
source: ruflo-releases
published_at: 2026-10-24T04:58:52+00:00
fetched_at: 2026-10-25T01:14:28.962310+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo-console 0.48.0 讓 ruRE 頁面可讀取使用者明確允許的專案外資料夾。 **How** 新增 plugin 選項 rureFolders（name=/絕對路徑 配對）；樣本以 @name/sub/file 指稱該資料夾；絕對路徑、..、特殊字元，以及資料夾或其下任一路徑為連結者皆會被拒絕；修改此選項一律需使用者確認。 **What** 此版本隨 ruflo tui 出貨，ruRE 仍只解析不執行；CI 新增規定，plugin 變更時須提高 plugin.json 版本（#4447）。"
key_points:
  - "rureFolders 以 name=/絕對路徑 配對授權外部資料夾，樣本需以 @name 指稱"
  - "路徑檢查拒絕絕對路徑、..、特殊字元與符號連結，修改選項一律需使用者確認"
  - "CI 規定 plugin PR 在出貨檔案變動時須提高 plugin.json 版本 (#4447)；@claude-flow/plugins 的 #4451 不在本版本"
tags: [ruflo, file-access, permissions, plugin, ci]
topics: [security, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.61.1 — ruRE can read a folder you allow (console 0.48.0)

ruflo-console 0.48.0 讓 ruRE 頁面可讀取使用者明確允許的專案外資料夾。 **How** 新增 plugin 選項 rureFolders（name=/絕對路徑 配對）；樣本以 @name/sub/file 指稱該資料夾；絕對路徑、..、特殊字元，以及資料夾或其下任一路徑為連結者皆會被拒絕；修改此選項一律需使用者確認。 **What** 此版本隨 ruflo tui 出貨，ruRE 仍只解析不執行；CI 新增規定，plugin 變更時須提高 plugin.json 版本（#4447）。

### 重點
- rureFolders 以 name=/絕對路徑 配對授權外部資料夾，樣本需以 @name 指稱
- 路徑檢查拒絕絕對路徑、..、特殊字元與符號連結，修改選項一律需使用者確認
- CI 規定 plugin PR 在出貨檔案變動時須提高 plugin.json 版本 (#4447)；@claude-flow/plugins 的 #4451 不在本版本

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.61.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.61.1. No leaf package changed, so no standalone publishes. 
 Added 
 
 ruflo-console 0.48.0 (ADR-499): the ruRE page can read a folder outside the project that you allow. New plugin option rureFolders ( name=/absolute/folder pairs); a sample then names it as @name/sub/file . Absolute paths, .. and odd characters in a sample are still refused; the folder and every part below it must not be a link; and changing the option is an install-class write that always asks you first (Claude's console tools can only propose it at the full control level). ruRE still only parses. This is the version that ruflo tui ships, which is why it needs a CLI release. 
 
 Notes 
 
 CI: plugin pull requests now fail unless the plugin's plugin.json version rises when shipped files change ( #4447 ). 
 @claude-flow/plugins ( #4451 , registry caches no longer re-run a surviving plugin's register* methods) is not a CLI dependency and is not part of this release.

</details>