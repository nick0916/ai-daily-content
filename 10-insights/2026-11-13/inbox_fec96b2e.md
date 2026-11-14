---
id: inbox_fec96b2e
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-infoq-main-dropbox-shares-how-its-in-house-cookie-a-99ea]]"
title: "Dropbox Shares How Its In-House Cookie Auditor Tests Consent Behaviour Across 200+ Web Surfaces"
url: https://www.infoq.com/news/2026/11/dropbox-cookie-auditor/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-13T06:15:00+00:00
fetched_at: 2026-11-14T01:52:25.627680+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dropbox 用自動化瀏覽器測試，定期檢查 200 多個網頁是否正確遵守 cookie 同意設定。 **How** 以 Playwright 為基礎的 auditor，每頁跑三項測試：美國訪客、歐盟訪客、Global Privacy Control 訊號；cookie 規則放在程式碼之外，另有配套工具找出線上 URL，每週報告區分疑似違規與誤報。 **What** Dropbox 內部自製的 cookie auditor，涵蓋 200 多個網頁介面。"
key_points:
  - "Playwright-based auditor 涵蓋 200+ 網頁介面"
  - "每頁三項測試：US 訪客、EU 訪客、Global Privacy Control 訊號"
  - "規則與程式碼分離，週報區分疑似違規與誤報"
tags: [dropbox, cookie-consent, playwright, privacy-compliance, automated-testing]
topics: [security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Dropbox Shares How Its In-House Cookie Auditor Tests Consent Behaviour Across 200+ Web Surfaces

Dropbox 用自動化瀏覽器測試，定期檢查 200 多個網頁是否正確遵守 cookie 同意設定。

**How** 以 Playwright 為基礎的 auditor，每頁跑三項測試：美國訪客、歐盟訪客、Global Privacy Control 訊號；cookie 規則放在程式碼之外，另有配套工具找出線上 URL，每週報告區分疑似違規與誤報。

**What** Dropbox 內部自製的 cookie auditor，涵蓋 200 多個網頁介面。

### 重點
- Playwright-based auditor 涵蓋 200+ 網頁介面
- 每頁三項測試：US 訪客、EU 訪客、Global Privacy Control 訊號
- 規則與程式碼分離，週報區分疑似違規與誤報

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/dropbox-cookie-auditor/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Dropbox engineers described a Playwright-based auditor that checks cookie consent behavior across more than 200 web surfaces. It runs three tests per page: US visitor, EU visitor, and Global Privacy Control signal. Cookie rules are kept outside the code. A companion tool finds live URLs. Weekly reports separate likely violations from false positives. By Daniel Curtis

</details>