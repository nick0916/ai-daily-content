---
id: inbox_74651bf8
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-infoq-main-ngrx-22-resource-extensions-and-dynamic-fec9]]"
title: "NgRx 22: Resource Extensions and Dynamic Deep Signals for Angular"
url: https://www.infoq.com/news/2026/10/ngrx-22-angular/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-23T08:08:00+00:00
fetched_at: 2026-10-24T03:51:55.073479+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "NgRx 22 讓 Angular 的 resource 在重新載入時保留舊值，且出錯時不再丟例外。 **What** NgRx 22 新增實驗性的 resource extensions，使 value() 在 reload 期間保留、錯誤時不再 throw；另有針對 union types 的 dynamic deep signals、SignalStoreFeatureType 工具與 ESLint v10 支援。升級需 Angular 22 與 TypeScript 6.0，多數 breaking changes 有自動 migration。"
key_points:
  - "resource extensions（實驗性）：value() 在 reload 時保留，錯誤時不再 throw"
  - "新增 union types 的 dynamic deep signals 與 SignalStoreFeatureType 工具"
  - "需 Angular 22 與 TypeScript 6.0；支援 ESLint v10；多數 breaking changes 有自動 migration"
tags: [ngrx, angular, signals, typescript, release]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## NgRx 22: Resource Extensions and Dynamic Deep Signals for Angular

NgRx 22 讓 Angular 的 resource 在重新載入時保留舊值，且出錯時不再丟例外。 **What** NgRx 22 新增實驗性的 resource extensions，使 value() 在 reload 期間保留、錯誤時不再 throw；另有針對 union types 的 dynamic deep signals、SignalStoreFeatureType 工具與 ESLint v10 支援。升級需 Angular 22 與 TypeScript 6.0，多數 breaking changes 有自動 migration。

### 重點
- resource extensions（實驗性）：value() 在 reload 時保留，錯誤時不再 throw
- 新增 union types 的 dynamic deep signals 與 SignalStoreFeatureType 工具
- 需 Angular 22 與 TypeScript 6.0；支援 ESLint v10；多數 breaking changes 有自動 migration

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/ngrx-22-angular/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

NgRx 22 adds experimental resource extensions that change Angular's resource behavior, so value() is retained during reloads and no longer throws on errors. It also introduces dynamic deep signals for union types, a SignalStoreFeatureType utility, and ESLint v10 support. Upgrading requires Angular 22 and TypeScript 6.0, and most breaking changes have automated migrations. By Daniel Curtis

</details>