---
id: inbox_a573e54b
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-infoq-main-yelp-combines-native-and-server-driven-u-34e1]]"
title: "Yelp Combines Native and Server-Driven UI for Its AI Assistant"
url: https://www.infoq.com/news/2026/11/yelp-assistant-hybrid-ui/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-06T14:25:00+00:00
fetched_at: 2026-11-07T01:46:05.644398+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把手機原生控制元件和伺服器驅動的畫面渲染混搭，讓 App 介面不用發版就能更新。 **Why** 原生 App 每次改 UI 都要等新版上架，AI 助理的對話介面需要更快迭代。 **How** CHAOS 框架把 view 設定與對話資料分離，由後端驅動聊天互動，同時保留原生控制元件。 **What** Yelp 在 AI Assistant 採用 CHAOS 框架，可不經 app 發版更新 UI；原文也討論跨平台挑戰，以及該架構在 Biz Ask Anything pilot 的重用。"
key_points:
  - "CHAOS 框架將 view 設定與對話資料分離"
  - "後端驅動聊天互動，UI 更新無需新 app 版本"
  - "架構重用於 Biz Ask Anything pilot，並討論跨平台挑戰"
tags: [yelp, server-driven-ui, ai-assistant, chaos-framework, mobile]
topics: [product_and_org.product, engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Yelp Combines Native and Server-Driven UI for Its AI Assistant

把手機原生控制元件和伺服器驅動的畫面渲染混搭，讓 App 介面不用發版就能更新。

**Why** 原生 App 每次改 UI 都要等新版上架，AI 助理的對話介面需要更快迭代。

**How** CHAOS 框架把 view 設定與對話資料分離，由後端驅動聊天互動，同時保留原生控制元件。

**What** Yelp 在 AI Assistant 採用 CHAOS 框架，可不經 app 發版更新 UI；原文也討論跨平台挑戰，以及該架構在 Biz Ask Anything pilot 的重用。

### 重點
- CHAOS 框架將 view 設定與對話資料分離
- 後端驅動聊天互動，UI 更新無需新 app 版本
- 架構重用於 Biz Ask Anything pilot，並討論跨平台挑戰

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/yelp-assistant-hybrid-ui/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Yelp combines native mobile controls with server-driven conversation rendering in its AI Assistant using the CHAOS framework. The architecture separates view configuration from conversation data, supports backend-driven chat interactions, and enables faster UI updates without new app releases. Yelp also discusses cross-platform challenges and reuse for its Biz Ask Anything pilot. By Leela Kumili

</details>