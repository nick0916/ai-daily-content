---
id: inbox_65da54d4
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-10-windows-adr-indexing-daemon-and-ee38]]"
title: "v3.59.10 — Windows ADR indexing, daemon and init flag-key fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.10
source: ruflo-releases
published_at: 2026-10-21T18:16:25+00:00
fetched_at: 2026-10-21T23:46:35.270768+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 Windows 上 ADR 索引找不到任何檔案的問題，並修正 daemon 與 init 的旗標被忽略。 **Why** findAdrs() 以寫死的正斜線路徑比對，而 Windows 上 join() 產生反斜線，因此會靜默地找到 0 筆 ADR。 **How** 新增與分隔符號無關的 isAdrPath() 正規表達式，parseAdr() 在所有平台都回報 POSIX 格式的相對路徑。 **What** daemon start 的 --max-cpu-load、--min-free-memory、--no-distill 與 init 的 --no-signup 原本都被忽略，現已修正（#4330、#4349、#4353）。"
key_points:
  - "findAdrs() 的寫死正斜線比對在 Windows 上靜默找到 0 筆 ADR，改用 isAdrPath() 解決"
  - "測試用的 npx fallback 在 Windows 無法直接啟動 npx.cmd，改由 node 執行 npx-cli.js"
  - "新增 windows-paths-2413、daemon-start-flag-keys、init-no-signup 三組回歸測試"
tags: [ruflo, windows, path-handling, adr, cli-flags]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.10 — Windows ADR indexing, daemon and init flag-key fixes

修正 Windows 上 ADR 索引找不到任何檔案的問題，並修正 daemon 與 init 的旗標被忽略。

**Why** findAdrs() 以寫死的正斜線路徑比對，而 Windows 上 join() 產生反斜線，因此會靜默地找到 0 筆 ADR。

**How** 新增與分隔符號無關的 isAdrPath() 正規表達式，parseAdr() 在所有平台都回報 POSIX 格式的相對路徑。

**What** daemon start 的 --max-cpu-load、--min-free-memory、--no-distill 與 init 的 --no-signup 原本都被忽略，現已修正（#4330、#4349、#4353）。

### 重點
- findAdrs() 的寫死正斜線比對在 Windows 上靜默找到 0 筆 ADR，改用 isAdrPath() 解決
- 測試用的 npx fallback 在 Windows 無法直接啟動 npx.cmd，改由 node 執行 npx-cli.js
- 新增 windows-paths-2413、daemon-start-flag-keys、init-no-signup 三組回歸測試

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.10)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 
 ruflo-adr : fixed ADR indexing on Windows — findAdrs() matched /docs/adr/ with a hardcoded forward-slash path check, which silently found zero ADRs on Windows ( join() yields backslashes there). Added isAdrPath() with a separator-agnostic regex, and parseAdr() now reports a POSIX-shaped, repo-relative path on every platform. Also fixed the npx fallback used by its own tests: Windows ships npx.cmd , which spawnSync cannot launch without a shell — resolveNpxCli() now runs npm's npx-cli.js directly with node ( #4330 , #2413 ). 
 daemon : ruflo daemon start --max-cpu-load , --min-free-memory , and --no-distill were silently ignored — the command read the raw kebab-case flag keys ( ctx.flags['max-cpu-load'] ), but the CLI parser stores them camelCased ( maxCpuLoad ) or as a boolean ( distill: false for --no-distill ). Fixed to read the keys the parser actually produces ( #4349 ). 
 init : ruflo init --no-signup was silently ignored for the same reason — the parser turns it into signup: false , which the enrollment-prompt check never read ( #4353 ). 
 
 Verification 
 
 node scripts/audit-umbrella-version-lockstep.mjs — all three packages at 3.59.10, ruflo pins @claude-flow/cli correctly. 
 node scripts/audit-leaf-versions-published.mjs — all 4 non-bundled leaves (cli-core 3.7.5, neural 3.0.0, shared 3.0.5, memory 3.0.8) confirmed published. 
 pnpm -r build clean across all 24 v3 workspace packages. 
 New regression tests from #4330 / #4349 / #4353 pass ( windows-paths-2413.test.mjs , daemon-start-flag-keys.test.ts , init-no-signup.test.ts ). 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) confirmed on the live npm registry at 3.59.10, latest / alpha / v3alpha dist-tags updated. 
 
 🤖 Generated with RuFlo

</details>