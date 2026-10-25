---
id: inbox_e6c68792
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0102-lobsters-vibecoding-orib-bringing-back-the-old-reddit-interf-b5eb]]"
title: "orib: Bringing back the old Reddit interface, with a few new enhancements"
url: https://github.com/rajtilakjee/orib
source: lobsters-vibecoding
published_at: 2026-10-16T23:22:50-05:00
fetched_at: 2026-10-25T01:28:03.599693+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Reddit 換回經典舊版介面的瀏覽器擴充功能。 **How** ORIB 是 Manifest V3 擴充功能，在 reddit.com 注入 document_start 腳本，讀取 Reddit 公開 JSON 列表後重繪頁面，並透過既有登入 session 執行投票、儲存、隱藏與留言。 **What** 版面包含子版塊列、藍色標頭、側欄與巢狀留言，支援 RES 風格鍵盤導覽；目前上架版本為 0.2.0，上架 zip 只含 manifest.json、renderer.js、classic.css 與 icons/。"
key_points:
  - "Manifest V3 擴充功能，於 www.reddit.com 以 document_start 注入，替換成經典版版面"
  - "讀取 Reddit 公開 JSON 列表，投票、儲存、隱藏、留言經由既有登入 session 送出"
  - "v0.2.0 上架包為 dist/orib-0.2.0.zip；Shift+? 可在頁面內顯示快捷鍵清單"
tags: [browser-extension, reddit, manifest-v3, web-ui]
topics: [product_and_org.product]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## orib: Bringing back the old Reddit interface, with a few new enhancements

把 Reddit 換回經典舊版介面的瀏覽器擴充功能。 **How** ORIB 是 Manifest V3 擴充功能，在 reddit.com 注入 document_start 腳本，讀取 Reddit 公開 JSON 列表後重繪頁面，並透過既有登入 session 執行投票、儲存、隱藏與留言。 **What** 版面包含子版塊列、藍色標頭、側欄與巢狀留言，支援 RES 風格鍵盤導覽；目前上架版本為 0.2.0，上架 zip 只含 manifest.json、renderer.js、classic.css 與 icons/。

### 重點
- Manifest V3 擴充功能，於 www.reddit.com 以 document_start 注入，替換成經典版版面
- 讀取 Reddit 公開 JSON 列表，投票、儲存、隱藏、留言經由既有登入 session 送出
- v0.2.0 上架包為 dist/orib-0.2.0.zip；Shift+? 可在頁面內顯示快捷鍵清單

**原文：** [lobsters-vibecoding](https://github.com/rajtilakjee/orib)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ORIB

Install

What it covers

Keyboard shortcuts

Store package

Project layout

Docs

Bringing back the old Reddit interface, with a few new enhancements.

ORIB is a Manifest V3 browser extension. On www.reddit.com it replaces the current page with a classic layout: subreddit bar, blue header, ranked posts, sidebar, and threaded comments. It reads Reddit's public JSON listings and posts votes, saves, hides, comments, and submissions through Reddit's existing session.

The extension itself lives in extension/ . Docs and the store listing stay outside that folder so they are not part of the upload.

The content script matches *://www.reddit.com/* and runs at document_start .

These paths stay on Reddit's own UI: /chat , /settings , /poll , /mod , and /message .

Shortcuts are ignored while focus is in an input, textarea, or content-editable element. Press Shift+? on a classic page for the in-page list.

Version 0.2.0 is what gets submitted. From the repository root:

That writes dist/orib-0.2.0.zip . The zip contains only manifest.json , renderer.js , classic.css , and icons/ , with the manifest at the root of the archive. Upload that zip. Do not upload the git repository.

The Chrome Web Store and Firefox Add-ons copy, plus the privacy policy, are in store/LISTING.md and store/PRIVACY.md .

Open chrome://extensions (or the equivalent page in another Chromium browser).

Turn on Developer mode.

Choose Load unpacked and select the extension directory.

Visit reddit.com . The page should show the classic layout after a short "loading classic reddit" state.

Frontpage and subreddit listings, including hot, best, new, rising, controversial, and top

Comment threads, with collapse and inline reply

User profiles and /saved

A classic submit form at /submit

Subreddit sidebar (subscriber count, users online, public description, and the subreddit's own stylesheet)

Expando previews for self text, images, galleries, and Reddit-hosted video

Upvote, downvote, save, and hide while you are logged in

Keyboard navigation in the style of Reddit Enhancement Suite

Architecture — how a page is replaced and which endpoints are called

Design — colors, type, and layout that keep the UI looking like old Reddit

Contributing — development setup, coding guidelines, and commit standards

powershell - File scripts / pack.ps1

</details>