---
id: inbox_54b14f7e
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-infoq-architecture-article-server-side-dpop-and-token-excha-09cd]]"
title: "Article: Server-Side DPoP and Token Exchange in Spring Security 7"
url: https://www.infoq.com/articles/spring-security-7-server-side-dpop-token-exchange/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-10-15T09:00:00+00:00
fetched_at: 2026-10-18T03:15:04.844404+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇 InfoQ 文章（作者 Dhruv Agnihotri）說明 Spring Authorization Server 現已併入 Spring Security 7，Maven coordinates 不變，因此升級僅需調整版本號。文章為伺服器端指南，涵蓋啟用 DPoP 與 RFC 8693 Token Exchange。一個重要提醒是：7.1 的應用程式可能在未呼叫 .dPoP() 時悄悄停止強制執行 DPoP。文章並示範如何結合兩者，產生範圍縮小、具 sender-constrained 特性的 token，用於 service-to-service 與 agentic 呼叫。對使用 Spring 的後端團隊，特別是讓 agent 呼叫內部服務的場景，這是檢查 token 綁定是否真的生效的實用提醒。"
key_points:
  - "Spring Authorization Server 併入 Spring Security 7，Maven coordinates 不變，升級為版本號調整"
  - "7.1 應用若未呼叫 .dPoP()，可能悄悄停止強制執行 DPoP"
  - "結合 DPoP 與 RFC 8693 Token Exchange，產生縮限範圍、sender-constrained 的 token 供 service-to-service 與 agentic 呼叫"
tags: [spring-security-7, dpop, token-exchange, rfc-8693, agent-auth]
topics: [security, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Server-Side DPoP and Token Exchange in Spring Security 7

這篇 InfoQ 文章（作者 Dhruv Agnihotri）說明 Spring Authorization Server 現已併入 Spring Security 7，Maven coordinates 不變，因此升級僅需調整版本號。文章為伺服器端指南，涵蓋啟用 DPoP 與 RFC 8693 Token Exchange。一個重要提醒是：7.1 的應用程式可能在未呼叫 .dPoP() 時悄悄停止強制執行 DPoP。文章並示範如何結合兩者，產生範圍縮小、具 sender-constrained 特性的 token，用於 service-to-service 與 agentic 呼叫。對使用 Spring 的後端團隊，特別是讓 agent 呼叫內部服務的場景，這是檢查 token 綁定是否真的生效的實用提醒。

### 重點
- Spring Authorization Server 併入 Spring Security 7，Maven coordinates 不變，升級為版本號調整
- 7.1 應用若未呼叫 .dPoP()，可能悄悄停止強制執行 DPoP
- 結合 DPoP 與 RFC 8693 Token Exchange，產生縮限範圍、sender-constrained 的 token 供 service-to-service 與 agentic 呼叫

**原文：** [infoq-architecture](https://www.infoq.com/articles/spring-security-7-server-side-dpop-token-exchange/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Spring Authorization Server now lives inside Spring Security 7 under the same Maven coordinates, so the upgrade is a version bump. This server-side guide covers enabling DPoP and RFC 8693 Token Exchange, explains why 7.1 apps can silently stop enforcing DPoP until they call .dPoP(), and shows how to combine both into narrowed, sender-constrained tokens for service-to-service and agentic calls. By Dhruv Agnihotri

</details>