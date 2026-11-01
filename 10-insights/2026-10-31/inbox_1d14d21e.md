---
id: inbox_1d14d21e
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-simon-willison-how-we-took-over-chatgpt-accounts-06b3]]"
title: "How We Took Over ChatGPT Accounts"
url: https://simonwillison.net/2026/Oct/31/how-we-took-over-chatgpt-accounts/
source: simon-willison
published_at: 2026-10-31T23:15:22+00:00
fetched_at: 2026-11-01T00:24:08.900600+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把幾個各自無害的小漏洞串起來，就能突破 ChatGPT 的 HTML 預覽沙盒並偷走使用者資料。 **Why** artifacts 類功能要在 sandbox iframe 裡執行不受信任的 HTML，沙盒一旦被突破，就能碰到使用者的私人資料與 OpenAI API。 **How** MathLive 虛擬鍵盤透過 postMessage() 讓父頁面用 innerHTML 插入 HTML，且沒有機制擋住沙盒 iframe 呼叫，因此可注入一個沒有沙盒限制的新 iframe；CSP 雖擋 inline script，但白名單包含 YouTube，YouTube oEmbed endpoint 能反射 JavaScript 使其執行，取得執行權後再以圖片請求外洩資料。 **What** Parameter Labs 揭露此攻擊鏈：攻擊者可做出 ChatGPT 分享連結，已登入的使用者一開就會被外洩私人資料或被代為操作。OpenAI 已修補並付出 $5,000 bug bounty，Simon Willison 認為對這種嚴重度偏低。"
key_points:
  - "攻擊鏈：沙盒 iframe → postMessage 觸發 MathLive 虛擬鍵盤 → 父頁面 innerHTML 注入無沙盒 iframe → 利用 CSP 白名單中的 YouTube oEmbed 反射 JS → 以圖片請求外洩資料"
  - "CSP 擋掉 inline script 並限制腳本來源，仍被白名單網域（YouTube）上的反射端點繞過"
  - "OpenAI 已修補，bug bounty $5,000；影響範圍為造訪惡意 ChatGPT 分享連結的已登入使用者"
tags: [chatgpt, xss, iframe-sandbox, csp-bypass, postmessage]
topics: [security]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How We Took Over ChatGPT Accounts

把幾個各自無害的小漏洞串起來，就能突破 ChatGPT 的 HTML 預覽沙盒並偷走使用者資料。

**Why** artifacts 類功能要在 sandbox iframe 裡執行不受信任的 HTML，沙盒一旦被突破，就能碰到使用者的私人資料與 OpenAI API。

**How** MathLive 虛擬鍵盤透過 postMessage() 讓父頁面用 innerHTML 插入 HTML，且沒有機制擋住沙盒 iframe 呼叫，因此可注入一個沒有沙盒限制的新 iframe；CSP 雖擋 inline script，但白名單包含 YouTube，YouTube oEmbed endpoint 能反射 JavaScript 使其執行，取得執行權後再以圖片請求外洩資料。

**What** Parameter Labs 揭露此攻擊鏈：攻擊者可做出 ChatGPT 分享連結，已登入的使用者一開就會被外洩私人資料或被代為操作。OpenAI 已修補並付出 $5,000 bug bounty，Simon Willison 認為對這種嚴重度偏低。

### 重點
- 攻擊鏈：沙盒 iframe → postMessage 觸發 MathLive 虛擬鍵盤 → 父頁面 innerHTML 注入無沙盒 iframe → 利用 CSP 白名單中的 YouTube oEmbed 反射 JS → 以圖片請求外洩資料
- CSP 擋掉 inline script 並限制腳本來源，仍被白名單網域（YouTube）上的反射端點繞過
- OpenAI 已修補，bug bounty $5,000；影響範圍為造訪惡意 ChatGPT 分享連結的已登入使用者

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/31/how-we-took-over-chatgpt-accounts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How We Took Over ChatGPT Accounts 
Parameter Labs describe an exploit they found against ChatGPT's implementation of the artifacts pattern (OpenAI used to call this "Canvas" but it looks like the latest revision is called HTML previews ), where interactive custom HTML apps are displayed in a sandboxed iframe. 
 It's important that HTML in these stays tightly sandboxed to avoid untrusted code interacting with OpenAI APIs and accessing private data. 
 Parameter found quite a complex attack chain. OpenAI use the MathLive JavaScript library as part of their graph support, and that library includes its own virtual keyboard , which can be triggered in the parent page via postMessage() from the sandboxed iframe. 
 That message receiving code uses innerHTML , so anything that sends a message can add custom HTML to the parent - and there was no mechanism to prevent other sandboxed frames, including HTML preview frames, from calling that method. 
 This meant untrusted code in an iframe could insert HTML, and while innerHTML doesn't directly execute script elements it could be used to inject a new iframe without sandbox restrictions. 
 OpenAI’s CSP rules blocked inline scripts entirely, and only allowed script loading from a handful of domains, but one of those was YouTube - and the YouTube oEmbed endpoint could be used to reflect JavaScript back in a way that executed it. 
 Once the attack had JavaScript execution on ChatGPT, it was trivial to fetch private user data from APIs and exfiltrate it via an image reference. 
 The end result: you could create a ChatGPT share URL which, when visited by another signed-in user, could exfiltrate their private data or take actions on their behalf. 
 OpenAI closed the hole and paid out a $5,000 bug bounty, which I think was a bit cheap for a vulnerability this serious.

 Via Hacker News 

 Tags: iframes , javascript , sandboxing , security , xss , openai , chatgpt , content-security-policy

</details>