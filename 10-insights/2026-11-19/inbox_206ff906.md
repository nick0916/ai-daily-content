---
id: inbox_206ff906
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0105-infoq-main-netwasm-0-10-speeds-up-c-on-webassembly-5f89]]"
title: "NetWasm 0.10 Speeds Up C# on WebAssembly, Now Faster Than Mono AOT"
url: https://www.infoq.com/news/2026/11/NetWasm-0-10-Faster/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-19T09:00:00+00:00
fetched_at: 2026-11-20T01:11:25.789146+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 C# 提前編譯成 WebAssembly 的工具，這一版跑得比 Mono AOT 更快。 **How** NetWasm 0.10 系列重做了例外處理、bounds-check 消除、SIMD 與除法。 **What** NetWasm 是 C# 到 WebAssembly 的 AOT 編譯器；在超過 2000 個 benchmark 案例中，專案自述執行時間為 Mono AOT WASI build 的 0.41 倍。"
key_points:
  - "NetWasm 0.10：重做例外處理、bounds-check 消除、SIMD、除法"
  - "2000+ benchmark 案例，執行時間為 Mono AOT WASI build 的 0.41 倍（專案自述）"
tags: [netwasm, webassembly, csharp, aot, benchmark]
topics: [engineering.inference]
importance: 1
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## NetWasm 0.10 Speeds Up C# on WebAssembly, Now Faster Than Mono AOT

把 C# 提前編譯成 WebAssembly 的工具，這一版跑得比 Mono AOT 更快。

**How** NetWasm 0.10 系列重做了例外處理、bounds-check 消除、SIMD 與除法。

**What** NetWasm 是 C# 到 WebAssembly 的 AOT 編譯器；在超過 2000 個 benchmark 案例中，專案自述執行時間為 Mono AOT WASI build 的 0.41 倍。

### 重點
- NetWasm 0.10：重做例外處理、bounds-check 消除、SIMD、除法
- 2000+ benchmark 案例，執行時間為 Mono AOT WASI build 的 0.41 倍（專案自述）

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/NetWasm-0-10-Faster/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Summary: NetWasm, an ahead-of-time compiler from C# to WebAssembly, has reworked exception handling, bounds-check elimination, SIMD and division in its 0.10 series. Across more than 2000 benchmark cases, the project reports running in 0.41 times the time of Mono AOT’s WASI build. By Edin Kapić

</details>