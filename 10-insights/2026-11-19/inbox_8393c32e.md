---
id: inbox_8393c32e
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0812-infoq-main-discord-rewrites-desktop-and-mobile-clie-3404]]"
title: "Discord Rewrites Desktop and Mobile Clients in Rust Using Zed's GPU-Accelerated Rendering Framework"
url: https://www.infoq.com/news/2026/11/discord-rust-rewrite-gpui-zed/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-19T03:12:00+00:00
fetched_at: 2026-11-19T08:18:32.247410+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Discord 把桌面與手機 App 從 Electron／React Native 改寫成 Rust，直接用 GPU 繪圖，換取更省記憶體、更快開啟。 **Why** 跨平台框架多了好幾層抽象，吃記憶體也拖慢開機，影響聊天、語音與串流體驗。 **How** 拿掉抽象層，直接利用裝置 GPU 與原生手機 view，並以跨平台共用的 Rust 核心取代原本的框架；桌面端使用 Zed 的 GPU 加速渲染框架 GPUI。 **What** Discord CTO Stanislav Vishnevskiy 宣布此重寫計畫，涵蓋桌面與手機 client。早期結果顯示 RAM 用量與開機時間明顯下降，但原文未提供具體數字。"
key_points:
  - "Discord 桌面與手機 client 從 Electron、React Native 改寫為 Rust"
  - "移除抽象層，直接使用 GPU、原生手機 view，並共用跨平台 Rust 核心"
  - "早期結果顯示 RAM 與開機時間明顯下降（原文無具體數字）"
tags: [discord, rust, electron, gpui, zed, client-rewrite]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Discord Rewrites Desktop and Mobile Clients in Rust Using Zed's GPU-Accelerated Rendering Framework

Discord 把桌面與手機 App 從 Electron／React Native 改寫成 Rust，直接用 GPU 繪圖，換取更省記憶體、更快開啟。

**Why** 跨平台框架多了好幾層抽象，吃記憶體也拖慢開機，影響聊天、語音與串流體驗。

**How** 拿掉抽象層，直接利用裝置 GPU 與原生手機 view，並以跨平台共用的 Rust 核心取代原本的框架；桌面端使用 Zed 的 GPU 加速渲染框架 GPUI。

**What** Discord CTO Stanislav Vishnevskiy 宣布此重寫計畫，涵蓋桌面與手機 client。早期結果顯示 RAM 用量與開機時間明顯下降，但原文未提供具體數字。

### 重點
- Discord 桌面與手機 client 從 Electron、React Native 改寫為 Rust
- 移除抽象層，直接使用 GPU、原生手機 view，並共用跨平台 Rust 核心
- 早期結果顯示 RAM 與開機時間明顯下降（原文無具體數字）

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/discord-rust-rewrite-gpui-zed/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Discord’s CTO Stanislav Vishnevskiy recently announced rewriting its desktop and mobile clients in Rust, moving away from Electron and React Native. The project eliminates layers of abstraction to directly leverage the device’s GPU, native mobile views, and a Rust core shared across platforms. Early results hint at a significant reduction in RAM usage and boot time for chat, voice, and streaming. By Bruno Couriol

</details>