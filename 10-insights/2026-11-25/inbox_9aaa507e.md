---
id: inbox_9aaa507e
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0052-infoq-main-rust-1-100-ships-the-never-type-after-te-4bd0]]"
title: "Rust 1.100 Ships the Never Type after Ten Years and Five Failed Attempts"
url: https://www.infoq.com/news/2026/11/rust-1-100-never-types/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-25T07:29:00+00:00
fetched_at: 2026-11-27T00:59:38.365567+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Rust 終於正式支援「never type」，用來表示永遠不會回傳的運算。 **What** Rust 1.100.0（2026-11-12 發布）歷經十年、五次失敗嘗試後穩定 never type（!），並讓 Infallible 成為其別名。此版本也穩定 allocator API 核心、新增 DropGuard，Cargo 新增可選的依賴冷卻期（dependency cooldown）設定。有評論指出 allocator 設計仍缺少 inline storage 支援。"
key_points:
  - "Rust 1.100.0 穩定 never type（!），Infallible 成為其別名"
  - "穩定 allocator API 核心並新增 DropGuard"
  - "Cargo 新增 opt-in 依賴冷卻期設定；allocator 仍缺 inline storage 支援"
tags: [rust, never-type, cargo, allocator-api, release]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Rust 1.100 Ships the Never Type after Ten Years and Five Failed Attempts

Rust 終於正式支援「never type」，用來表示永遠不會回傳的運算。

**What** Rust 1.100.0（2026-11-12 發布）歷經十年、五次失敗嘗試後穩定 never type（!），並讓 Infallible 成為其別名。此版本也穩定 allocator API 核心、新增 DropGuard，Cargo 新增可選的依賴冷卻期（dependency cooldown）設定。有評論指出 allocator 設計仍缺少 inline storage 支援。

### 重點
- Rust 1.100.0 穩定 never type（!），Infallible 成為其別名
- 穩定 allocator API 核心並新增 DropGuard
- Cargo 新增 opt-in 依賴冷卻期設定；allocator 仍缺 inline storage 支援

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/rust-1-100-never-types/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Rust 1.100.0, released 12 November 2026, stabilises the never type (!) after ten years of work and makes Infallible an alias for it. The release also stabilises the core of the allocator API, adds DropGuard, and gives Cargo an opt-in dependency cooldown setting. Some critics note the allocator design still lacks inline storage support. By Daniel Curtis

</details>