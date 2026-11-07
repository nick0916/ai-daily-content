---
id: inbox_b5d5353a
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-infoq-main-aws-ships-continuum-for-code-vulnerabili-c89c]]"
title: "AWS Ships Continuum for Code Vulnerabilities"
url: https://www.infoq.com/news/2026/11/aws-continuum-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-06T10:00:00+00:00
fetched_at: 2026-11-07T01:46:05.648686+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 的服務會在沙箱真的執行攻擊來證明漏洞可被利用，再自動開修補 PR。 **Why** 傳統掃描誤報多，團隊難分辨哪些漏洞真的有風險。 **How** 在 sandbox 中執行真實 exploit 驗證可利用性，確認後以 pull request 提出修復。 **What** AWS Continuum for code vulnerabilities 於兩個 region 正式 GA；定價依處理的 finding 與程式碼行數計費。實務人員在問，什麼條件下才值得讓它自行合併修復。"
key_points:
  - "在沙箱以真實 exploit 驗證漏洞可利用性，再開 PR 修復"
  - "GA 於兩個 region；依 finding 數與程式碼行數計費"
  - "社群關切是否該讓它自動 merge 修復"
tags: [aws, continuum, vulnerability, sandbox, auto-remediation]
topics: [security, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Ships Continuum for Code Vulnerabilities

AWS 的服務會在沙箱真的執行攻擊來證明漏洞可被利用，再自動開修補 PR。

**Why** 傳統掃描誤報多，團隊難分辨哪些漏洞真的有風險。

**How** 在 sandbox 中執行真實 exploit 驗證可利用性，確認後以 pull request 提出修復。

**What** AWS Continuum for code vulnerabilities 於兩個 region 正式 GA；定價依處理的 finding 與程式碼行數計費。實務人員在問，什麼條件下才值得讓它自行合併修復。

### 重點
- 在沙箱以真實 exploit 驗證漏洞可利用性，再開 PR 修復
- GA 於兩個 region；依 finding 數與程式碼行數計費
- 社群關切是否該讓它自動 merge 修復

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-continuum-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has made Continuum for code vulnerabilities generally available in two regions. The service proves exploitability by running real exploits in a sandbox, then opens fixes as pull requests. Published pricing charges per finding processed as well as per line of code, and practitioners are asking what would justify letting it merge fixes on its own. By Steef-Jan Wiggers

</details>