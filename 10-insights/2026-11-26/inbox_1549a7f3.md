---
id: inbox_1549a7f3
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-infoq-main-mock-service-worker-releases-v3-0-with-e-0abf]]"
title: "Mock Service Worker Releases v3.0 with ESM-Only Build, Socket-Based Interception and GraphQL Subs"
url: https://www.infoq.com/news/2026/11/mock-service-worker-v3/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-26T06:59:00+00:00
fetched_at: 2026-11-27T00:59:20.241903+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "API mock 工具 MSW 發布 3.0，改為純 ESM 並在更底層攔截網路請求。 **What** Mock Service Worker 3.0 僅提供 ESM、需 Node.js 22 以上，套件大小由 416KB 降至 234KB。新增 GraphQL subscription 支援、依協定分開的 entrypoints 與實驗性的 defineNetwork API；Node.js 端的攔截改在 TCP 與 TLS 層。部分使用者回報，因新攔截到 OPTIONS preflight 請求，導致測試失敗。"
key_points:
  - "ESM-only、需 Node.js 22+，套件大小 416KB → 234KB"
  - "新增 GraphQL subscription 支援、protocol-specific entrypoints、實驗性 defineNetwork API"
  - "Node.js 攔截下沉到 TCP/TLS 層；有使用者回報 OPTIONS preflight 被攔截導致測試失敗"
tags: [mock-service-worker, msw, testing, nodejs, graphql]
topics: [product_and_org.product]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Mock Service Worker Releases v3.0 with ESM-Only Build, Socket-Based Interception and GraphQL Subs

API mock 工具 MSW 發布 3.0，改為純 ESM 並在更底層攔截網路請求。

**What** Mock Service Worker 3.0 僅提供 ESM、需 Node.js 22 以上，套件大小由 416KB 降至 234KB。新增 GraphQL subscription 支援、依協定分開的 entrypoints 與實驗性的 defineNetwork API；Node.js 端的攔截改在 TCP 與 TLS 層。部分使用者回報，因新攔截到 OPTIONS preflight 請求，導致測試失敗。

### 重點
- ESM-only、需 Node.js 22+，套件大小 416KB → 234KB
- 新增 GraphQL subscription 支援、protocol-specific entrypoints、實驗性 defineNetwork API
- Node.js 攔截下沉到 TCP/TLS 層；有使用者回報 OPTIONS preflight 被攔截導致測試失敗

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/mock-service-worker-v3/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Mock Service Worker 3.0 is now ESM-only, requires Node.js 22 or later, and cuts package size from 416KB to 234KB. It adds GraphQL subscription support, protocol-specific entrypoints, and an experimental defineNetwork API. Node.js interception now works at the TCP and TLS level. Some users report test failures from newly intercepted OPTIONS preflight requests. By Daniel Curtis

</details>