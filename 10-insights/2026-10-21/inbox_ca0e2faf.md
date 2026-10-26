---
id: inbox_ca0e2faf
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-gitnexus-releases-rc-2b111f4488ed5f94e79e529a3c94bc96202d1-1bfb]]"
title: "rc/2b111f4488ed5f94e79e529a3c94bc96202d1700: fix(docker): verify bundled FTS artifacts (#3669)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2b111f4488ed5f94e79e529a3c94bc96202d1700
source: gitnexus-releases
published_at: 2026-10-21T17:27:30+00:00
fetched_at: 2026-10-21T23:45:46.280224+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "改用執行期路徑驗證 FTS 打包產物，不再依賴 CDN 下載。 **Why** 線上 ARM64 CDN 產物含有 core 0.21.1 沒有的符號，導致載入失敗。 **How** 透過 runtime path resolver 驗證打包內的產物，並保留強制性的原生 LOAD 檢查，且不需下載。 **What** ARM64 模擬環境重現了 CDN 失敗；打包產物可正常載入、建立 FTS 索引並回應查詢。47 個聚焦測試與兩項 TypeScript 檢查通過，完整本地測試仍在執行中。"
key_points:
  - "線上 ARM64 CDN 重建產物含 core 0.21.1 缺少的符號，ARM64 模擬可重現失敗"
  - "改為透過 runtime path resolver 驗證打包產物，保留強制性原生 LOAD 檢查，不做下載"
  - "打包產物可載入、建立 FTS 索引並回應查詢；47 個聚焦測試與兩項 TypeScript 檢查通過"
tags: [gitnexus, docker, fts, arm64, artifact-verification]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/2b111f4488ed5f94e79e529a3c94bc96202d1700: fix(docker): verify bundled FTS artifacts (#3669)

改用執行期路徑驗證 FTS 打包產物，不再依賴 CDN 下載。

**Why** 線上 ARM64 CDN 產物含有 core 0.21.1 沒有的符號，導致載入失敗。

**How** 透過 runtime path resolver 驗證打包內的產物，並保留強制性的原生 LOAD 檢查，且不需下載。

**What** ARM64 模擬環境重現了 CDN 失敗；打包產物可正常載入、建立 FTS 索引並回應查詢。47 個聚焦測試與兩項 TypeScript 檢查通過，完整本地測試仍在執行中。

### 重點
- 線上 ARM64 CDN 重建產物含 core 0.21.1 缺少的符號，ARM64 模擬可重現失敗
- 改為透過 runtime path resolver 驗證打包產物，保留強制性原生 LOAD 檢查，不做下載
- 打包產物可載入、建立 FTS 索引並回應查詢；47 個聚焦測試與兩項 TypeScript 檢查通過

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2b111f4488ed5f94e79e529a3c94bc96202d1700)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The live ARM64 CDN artifact was rebuilt with a symbol absent from core 
0.21.1. Verify the packaged artifact through the runtime path resolver 
instead, retaining a mandatory native LOAD gate without a download. 
 ARM64 emulation reproduces the CDN failure; the bundled artifact loads, 
builds an FTS index, and answers a query. 47 focused tests and both 
TypeScript checks pass. Full local suite is still running. 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>