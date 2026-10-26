---
id: inbox_544b5e7d
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-ruflo-releases-v3-59-1-npx-ruflo-tui-mouse-clicking-on-f771]]"
title: "v3.59.1 — npx ruflo tui: mouse clicking on by default"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.1
source: ruflo-releases
published_at: 2026-10-20T17:26:30+00:00
fetched_at: 2026-10-21T00:12:51.012073+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 `npx ruflo tui` 的滑鼠點擊預設開啟，解決使用者點擊無反應的問題。 **Why** 滑鼠功能自 ADR-489 起為 opt-in，只有一次性啟動提示，使用者常反映點擊沒有作用。 **How** 預設啟用 mouse，若終端機的 SGR 滑鼠回報與原生文字選取衝突，可用 --no-mouse 關閉。 **What** v3.59.1 發布 @claude-flow/cli、claude-flow、ruflo 三個 npm 套件（latest、alpha、v3alpha dist-tag 已驗證）；main 分支另有 ruflo-core 的 witness 簽章金鑰功能（RUFLO_WITNESS_SEED / --public-key），但不屬於此次 npm 發布。"
key_points:
  - "npx ruflo tui 的滑鼠點擊預設開啟，點頂部分頁名稱或滾輪即可操作"
  - "--no-mouse 保留給與原生文字選取衝突的終端機（#4328）"
  - "ruflo-core 的 witness manifest 支援外部簽章金鑰，舊的 commit-derived seed 改標為 self-attested（#4201、#4326）"
tags: [ruflo, tui, mouse-support, npm-release, witness-signing]
topics: [agents.frameworks, security]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.1 — npx ruflo tui: mouse clicking on by default

讓 `npx ruflo tui` 的滑鼠點擊預設開啟，解決使用者點擊無反應的問題。

**Why** 滑鼠功能自 ADR-489 起為 opt-in，只有一次性啟動提示，使用者常反映點擊沒有作用。

**How** 預設啟用 mouse，若終端機的 SGR 滑鼠回報與原生文字選取衝突，可用 --no-mouse 關閉。

**What** v3.59.1 發布 @claude-flow/cli、claude-flow、ruflo 三個 npm 套件（latest、alpha、v3alpha dist-tag 已驗證）；main 分支另有 ruflo-core 的 witness 簽章金鑰功能（RUFLO_WITNESS_SEED / --public-key），但不屬於此次 npm 發布。

### 重點
- npx ruflo tui 的滑鼠點擊預設開啟，點頂部分頁名稱或滾輪即可操作
- --no-mouse 保留給與原生文字選取衝突的終端機（#4328）
- ruflo-core 的 witness manifest 支援外部簽章金鑰，舊的 commit-derived seed 改標為 self-attested（#4201、#4326）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 npx ruflo tui : mouse clicking is now on by default — click a page name in the top bar, scroll with the wheel. --mouse had been opt-in since ADR-489 with only a one-time startup notice ( #4305 ), but users kept reporting that clicking did nothing. --no-mouse remains available for terminals where SGR mouse reporting fights native text selection ( #4328 ). 
 
 Published 
 
 @claude-flow/cli@3.59.1 , claude-flow@3.59.1 , ruflo@3.59.1 — latest / alpha / v3alpha dist-tags all verified on the live registry. 
 
 Also on main (not part of this npm publish) 
 
 plugins/ruflo-core : witness manifests support an optional external signing key ( RUFLO_WITNESS_SEED / --public-key ) for real authenticity; the legacy commit-derived seed is now labeled self-attested rather than presented as authorship proof ( #4201 , #4326 ). Ships via the ruflo-core plugin's own distribution, not this release.

</details>