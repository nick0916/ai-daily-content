---
id: inbox_38a0adf0
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0100-substack-bytebytego-ep230-rag-vs-agentic-rag-5a51]]"
title: "EP230: RAG vs Agentic RAG"
url: https://blog.bytebytego.com/p/ep230-rag-vs-agentic-rag
source: substack-bytebytego
published_at: 2026-10-24T15:30:37+00:00
fetched_at: 2026-10-25T01:08:09.035633+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ByteByteGo 第 230 期電子報，用簡短圖解說明 RAG 與 Agentic RAG 的差異，並補充 OAuth／OIDC 與 Linux 目錄結構。 **Why** 傳統 RAG 依固定的檢索流程，答案品質取決於檢索到的內容是否準確。 **How** Agentic RAG 讓 agent 依任務挑選工具（文件、API、資料庫、網路），檢查證據是否足夠，不足就調整搜尋或換工具，直到證據充足才交給 LLM 生成答案。 **What** 本期另說明：OAuth 2.0 負責授權（Slack 不經手 Google 密碼，以 authorization code 換 access_token），OIDC 架在其上負責驗證身分（額外回傳簽章過的 JWT id_token）。最後介紹 Linux 目錄結構，例如 bin、etc、var、home。"
key_points:
  - "RAG 為單次、預先定義的檢索；Agentic RAG 為迴圈式：選工具、取證據、判斷證據是否足夠、必要時調整搜尋"
  - "OAuth 回答「你能存取什麼」，OIDC 回答「你是誰」；OIDC 在 access_token 之外多回傳 id_token（簽章 JWT）"
  - "Linux 目錄：bin 放基本指令、etc 放系統設定、var 放執行中會變動的資料（如 log）、home 放各使用者目錄"
tags: [rag, agentic-rag, oauth, oidc, system-design]
topics: [engineering.rag, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## EP230: RAG vs Agentic RAG

ByteByteGo 第 230 期電子報，用簡短圖解說明 RAG 與 Agentic RAG 的差異，並補充 OAuth／OIDC 與 Linux 目錄結構。

**Why** 傳統 RAG 依固定的檢索流程，答案品質取決於檢索到的內容是否準確。

**How** Agentic RAG 讓 agent 依任務挑選工具（文件、API、資料庫、網路），檢查證據是否足夠，不足就調整搜尋或換工具，直到證據充足才交給 LLM 生成答案。

**What** 本期另說明：OAuth 2.0 負責授權（Slack 不經手 Google 密碼，以 authorization code 換 access_token），OIDC 架在其上負責驗證身分（額外回傳簽章過的 JWT id_token）。最後介紹 Linux 目錄結構，例如 bin、etc、var、home。

### 重點
- RAG 為單次、預先定義的檢索；Agentic RAG 為迴圈式：選工具、取證據、判斷證據是否足夠、必要時調整搜尋
- OAuth 回答「你能存取什麼」，OIDC 回答「你是誰」；OIDC 在 access_token 之外多回傳 id_token（簽章 JWT）
- Linux 目錄：bin 放基本指令、etc 放系統設定、var 放執行中會變動的資料（如 log）、home 放各使用者目錄

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/ep230-rag-vs-agentic-rag)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Build for the long run. (Sponsored) Long-running agents need endurance. They must endure waiting for users, and weather tool failures. They must take each new jump in model intelligence in stride. Inngest makes long-running agents durable, observable and improvable over time. Check out their generous free tier and a sleek local dev server for testing your workflows. Build for the long run with Inngest This week&#8217;s system design refresher: Top 5 AI Building Blocks Every Engineer Should Know (Youtube Video) RAG vs Agentic RAG OAuth (authorization) + OIDC (authentication layer) Understanding the Linux Directory Structure Top 5 AI Building Blocks Every Engineer Should Know RAG vs Agentic RAG RAG is a technique that combines information retrieval with an LLM to generate answers. Here is how RAG works at a high level: A user asks a question to the application. The retrieval system fetches the relevant information from a knowledge base. The application adds that information to the prompt. The LLM uses that context to generate an answer. RAG usually follows a predefined retrieval process. The quality of its results depends on the accuracy of the retrieved context. Agentic RAG follows a different approach. Instead of retrieving once, an agent can repeatedly fetch and evaluate information until it has enough evidence to generate an answer. Here is how it typically works: An agent selects the right tools based on the task. Those tools can search documents, APIs, databases, or the web. The fetched evidence is then checked if it is sufficient for the task. If it is not, the agent can adjust its search or choose a different tool. Once sufficient evidence is achieved, LLM uses that context to generate an answer. Thank You, Open Source Maintainers (Sponsored) Open source is the foundation of nearly everything we build, and the maintainers behind it make it possible. The good news: the movement to support them is growing. Two years ago, the Open Source Pledge set out to make paying maintainers the norm. Today, 37 member companies have paid $8.4M to maintainers and foundations, and every new member adds to that momentum. See how Sentry put $1M to work this year, or join the Pledge and be part of what&#8217;s next. Learn more OAuth (authorization) + OIDC (authentication layer) If you want to show Google Calendar events inside your Slack channel, it will require permission to read your calendar. How would you let Slack access your calendar without giving Slack your Google password? This is where OAuth 2.0 comes into the picture. Slack basically never sees your Google password. It lets an app access a protected resource on your behalf without knowing your credentials. Basically OAuth 2.0 handles authorization. In Slack&#8217;s case, it will send you to Google&#8217;s authorization server, where you will login and give Slack permission to access your calendar. Google gives you the authorization code, and Slack will exchange that code for access_token. If Slack also wants to authenticate the identity of the person requesting the access to Google Calendar, you will need OIDC for that. The OIDC handles authentication and sits on top of OAuth 2.0. OAuth answers what you&#8217;re allowed to touch, while OIDC answers who you are. In addition to the access_token returned by the authorization server, this time, it will also send an id_token, a signed JWT which basically tells Slack who just signed in. Understanding the Linux Directory Structure The linux directory structure starts with the root directory "/". Let&#8217;s navigate to the directory structure of linux. The kernel image and bootloader files are stored in the "boot" directory. Your hard disk partitions and device related files are located in the &#8220;dev&#8221; directory. All your programs and libraries are stored in "bin", "sbin", "usr", and "lib" directories. Like, your installed software is located in the "usr" directory. Ever wondered where ls, cp, and cat commands are? "bin" is the directory that holds those essential commands. System-wide configuration goes in "etc", and "var" holds data that changes as the system runs, which is where you'll find your logs. If you have a USB drive, it gets mounted in &#8220;bin&#8221; folder. For any external drive that you want to mount temporarily on your linux machine, "media" is the directory for it. If you have multiple user accounts, "home" is the directory for each user in your linux system.

</details>