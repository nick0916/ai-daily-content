---
id: inbox_bd265470
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-infoq-main-node-js-brings-debounce-throttle-and-pkc-533b]]"
title: "Node.js Brings Debounce, Throttle, and PKCS#12 Parsing Into Core Modules"
url: https://www.infoq.com/news/2026/11/nodejs-debounce-throttle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-14T08:03:00+00:00
fetched_at: 2026-11-15T01:29:47.318808+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Node.js 把常用的防抖、節流工具直接內建，少裝幾個第三方套件。 **Why** 這些功能過去要靠使用者端的第三方依賴，內建後可減少部分依賴。 **What** Node.js 26.10.0 新增 util.debounce()、util.throttle()、util.markPromiseAsHandled()，以及可讀取 .p12 與 .pfx 的 crypto.parsePKCS12()，並把實驗性的 Virtual File System 擴及 node:ffi。Node.js 26 現已進入 Active LTS。"
key_points:
  - "Node.js 26.10.0 新增 util.debounce()、util.throttle()、util.markPromiseAsHandled()"
  - "新增 crypto.parsePKCS12() 解析 .p12 / .pfx 憑證包"
  - "實驗性 Virtual File System 擴展到 node:ffi；Node.js 26 成為 Active LTS"
tags: [nodejs, javascript, runtime, lts, pkcs12]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Node.js Brings Debounce, Throttle, and PKCS#12 Parsing Into Core Modules

Node.js 把常用的防抖、節流工具直接內建，少裝幾個第三方套件。

**Why** 這些功能過去要靠使用者端的第三方依賴，內建後可減少部分依賴。

**What** Node.js 26.10.0 新增 util.debounce()、util.throttle()、util.markPromiseAsHandled()，以及可讀取 .p12 與 .pfx 的 crypto.parsePKCS12()，並把實驗性的 Virtual File System 擴及 node:ffi。Node.js 26 現已進入 Active LTS。

### 重點
- Node.js 26.10.0 新增 util.debounce()、util.throttle()、util.markPromiseAsHandled()
- 新增 crypto.parsePKCS12() 解析 .p12 / .pfx 憑證包
- 實驗性 Virtual File System 擴展到 node:ffi；Node.js 26 成為 Active LTS

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/nodejs-debounce-throttle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Node.js 26.10.0 adds util.debounce() and util.throttle(), plus util.markPromiseAsHandled(), to the core library. It also introduces crypto.parsePKCS12() for reading .p12 and .pfx bundles, and extends the experimental Virtual File System to node:ffi. The additions reduce the need for some userland dependencies. Node.js 26 is now Active LTS. By Daniel Curtis

</details>