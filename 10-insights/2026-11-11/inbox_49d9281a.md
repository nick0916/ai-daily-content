---
id: inbox_49d9281a
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-infoq-main-angular-s-typescript-7-powered-compiler-bbaf]]"
title: "Angular's TypeScript 7-Powered Compiler Enters Beta with Rust-Based Preprocessor"
url: https://www.infoq.com/news/2026/11/angular-compiler-rust-typescript/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-11T07:06:00+00:00
fetched_at: 2026-11-12T02:59:23.373920+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Angular 用 Rust 重寫編譯器的分析階段，讓建置更快。 **Why** TypeScript 7.0 移除了 Transformer API，而 ngc 依賴它，需要新的做法。 **How** 新的編譯器預處理器 ngp 以 Oxc 用 Rust 重寫分析階段，取代 ngc 對 Transformer API 的依賴。 **What** Angular 的 TypeScript 7 編譯器進入 beta；早期 benchmark 顯示冷啟動建置快 2 到 3 倍。預期在 Angular 22 的 minor 版本採用，在此之前正式建置應繼續用 ngc。"
key_points:
  - "ngp 以 Rust 與 Oxc 重寫 Angular 編譯分析階段，取代 TypeScript 7.0 已移除的 Transformer API"
  - "早期 benchmark：冷啟動建置快 2x 到 3x"
  - "預計 Angular 22 minor 版本採用，正式建置暫用 ngc"
tags: [angular, rust, oxc, typescript-7, compiler]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Angular's TypeScript 7-Powered Compiler Enters Beta with Rust-Based Preprocessor

Angular 用 Rust 重寫編譯器的分析階段，讓建置更快。

**Why** TypeScript 7.0 移除了 Transformer API，而 ngc 依賴它，需要新的做法。

**How** 新的編譯器預處理器 ngp 以 Oxc 用 Rust 重寫分析階段，取代 ngc 對 Transformer API 的依賴。

**What** Angular 的 TypeScript 7 編譯器進入 beta；早期 benchmark 顯示冷啟動建置快 2 到 3 倍。預期在 Angular 22 的 minor 版本採用，在此之前正式建置應繼續用 ngc。

### 重點
- ngp 以 Rust 與 Oxc 重寫 Angular 編譯分析階段，取代 TypeScript 7.0 已移除的 Transformer API
- 早期 benchmark：冷啟動建置快 2x 到 3x
- 預計 Angular 22 minor 版本採用，正式建置暫用 ngc

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/angular-compiler-rust-typescript/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The Angular team has introduced ngp, a compiler preprocessor that rewrites the analysis stage in Rust using Oxc. It replaces ngc's dependence on the Transformer API, which TypeScript 7.0 removed. An early benchmark showed 2x to 3x faster cold builds. Adoption is expected in an Angular 22 minor release; production builds should stay on ngc until then. By Daniel Curtis

</details>