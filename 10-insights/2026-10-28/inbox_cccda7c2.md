---
id: inbox_cccda7c2
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0017-infoq-main-chrome-opens-trial-for-the-email-verific-6081]]"
title: "Chrome Opens Trial for the Email Verification API: Letting Sites Verify Without Sending Emails"
url: https://www.infoq.com/news/2026/10/chrome-email-verification/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-28T09:32:00+00:00
fetched_at: 2026-10-29T00:22:35.503964+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓網站不用寄驗證信，就能由瀏覽器確認使用者擁有某個 email。 **Why** 傳統驗證要寄信、等使用者點連結，流程繁瑣。 **How** 瀏覽器向 email 提供者確認所有權並產生簽章 token，開發者在表單加提示，並在伺服器端驗證該 token。 **What** Google 開啟 Chrome 的 Email Verification API origin trial（WICG 提案），Gmail 是第一個支援的提供者。留言者質疑其隱私效益，建議作為漸進式增強使用。"
key_points:
  - "Chrome 開放 Email Verification API origin trial，源自 WICG 提案"
  - "Gmail 為首個提供者；開發者加表單提示並在伺服器端驗證簽章 token"
  - "建議作為 progressive enhancement，社群對隱私效益有疑慮"
tags: [chrome, email-verification, web-api, origin-trial, wicg]
topics: [product_and_org.product]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Chrome Opens Trial for the Email Verification API: Letting Sites Verify Without Sending Emails

讓網站不用寄驗證信，就能由瀏覽器確認使用者擁有某個 email。

**Why** 傳統驗證要寄信、等使用者點連結，流程繁瑣。

**How** 瀏覽器向 email 提供者確認所有權並產生簽章 token，開發者在表單加提示，並在伺服器端驗證該 token。

**What** Google 開啟 Chrome 的 Email Verification API origin trial（WICG 提案），Gmail 是第一個支援的提供者。留言者質疑其隱私效益，建議作為漸進式增強使用。

### 重點
- Chrome 開放 Email Verification API origin trial，源自 WICG 提案
- Gmail 為首個提供者；開發者加表單提示並在伺服器端驗證簽章 token
- 建議作為 progressive enhancement，社群對隱私效益有疑慮

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/chrome-email-verification/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google has opened a Chrome origin trial for the Email Verification API, a WICG proposal that lets the browser confirm email ownership without sending a message. Gmail is the first provider. Developers add form hints and validate a signed token server-side. Commenters question the privacy benefit, and the API is best used as a progressive enhancement. By Daniel Curtis

</details>