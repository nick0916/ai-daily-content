---
id: inbox_d1ae4f27
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2347-infoq-main-vitest-5-prioritises-performance-with-a-5665]]"
title: "Vitest 5: Prioritises Performance with a Shared Vite Server, Trace View, and Stricter Test Defaults"
url: https://www.infoq.com/news/2026/11/vite-5-release/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-03T16:47:00+00:00
fetched_at: 2026-11-03T23:53:22.412281+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "測試框架 Vitest 5 發布，主打速度提升並把預設值改得更嚴格。 **What** Vitest 5.0 回報在多數設定下快 8-25%，VM pools 最高快 53%；新增 vitest doctor 指令、Browser Mode Trace View 與 vi.when。預設更嚴格：clearMocks 預設為 true，未 await 的非同步斷言會失敗；需要 Vite 6.4 以及 Node.js 22.12 以上。"
key_points:
  - "效能：多數設定快 8-25%，VM pools 最高快 53%"
  - "新功能：vitest doctor 指令、Browser Mode Trace View、vi.when"
  - "破壞性預設：clearMocks 為 true、未 await 的非同步斷言會失敗；需 Vite 6.4+ 與 Node.js 22.12+"
tags: [vitest, testing, javascript, vite, release]
topics: [engineering.evals]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Vitest 5: Prioritises Performance with a Shared Vite Server, Trace View, and Stricter Test Defaults

測試框架 Vitest 5 發布，主打速度提升並把預設值改得更嚴格。

**What** Vitest 5.0 回報在多數設定下快 8-25%，VM pools 最高快 53%；新增 vitest doctor 指令、Browser Mode Trace View 與 vi.when。預設更嚴格：clearMocks 預設為 true，未 await 的非同步斷言會失敗；需要 Vite 6.4 以及 Node.js 22.12 以上。

### 重點
- 效能：多數設定快 8-25%，VM pools 最高快 53%
- 新功能：vitest doctor 指令、Browser Mode Trace View、vi.when
- 破壞性預設：clearMocks 為 true、未 await 的非同步斷言會失敗；需 Vite 6.4+ 與 Node.js 22.12+

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/vite-5-release/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Vitest 5.0 focuses on speed, with reported gains of 8 to 25 percent in most setups and up to 53 percent in VM pools. It adds a vitest doctor command, Browser Mode Trace View, and vi.when. Defaults are stricter: clearMocks is true and unawaited async assertions fail. It requires Vite 6.4 and Node.js 22.12 or newer. By Daniel Curtis

</details>