---
id: inbox_77a5eae7
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/2349-hackernews-show-hn-coldframe-a-honeypot-that-poses-b687]]"
title: "Show HN: Coldframe, a honeypot that poses as a supermarket fridge controller"
url: https://github.com/hedgerow-dev/coldframe
source: hackernews
published_at: 2026-11-07T17:27:30+00:00
fetched_at: 2026-11-08T23:53:08.883380+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "做一個假的超市冷凍櫃控制器網站，引誘攻擊者出手並記錄他們的行為。 **Why** 近幾週工業冷凍設備遭到攻擊，作者想知道面對逼真的誘餌時攻擊者會做什麼。 **How** 單一 Python 檔、只用標準函式庫；比對 Shodan 上真實設備的 header 順序、頁面標題、憑證欄位與 TLS 版本，讓 Shodan 把它判為真設備；預設帳密可登入假的店面儀表板，以觀察攻擊者的第二步動作。 **What** 開源 honeypot Coldframe，模擬 Danfoss AK-SM 800A 與 Dixell XWEB，可辨識 CVE-2025-41450（Danfoss「code of the day」登入繞過）並記錄當日代碼是否正確。兩個實例上線一天，目前只看到一般掃描器與 Shodan 爬蟲。"
key_points:
  - "模擬 Danfoss AK-SM 800A 與 Dixell XWEB；Dixell 版本把頁面補到剛好 8,202 bytes、不送 Server header"
  - "辨識 CVE-2025-41450 並標記另外三個 Danfoss CVE 與 XWEB 漏洞的攻擊嘗試"
  - "兩個實例上線一天，只觀察到一般掃描器與 Shodan 爬蟲"
tags: [honeypot, ics-security, cve-2025-41450, danfoss, shodan]
topics: [security]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Coldframe, a honeypot that poses as a supermarket fridge controller

做一個假的超市冷凍櫃控制器網站，引誘攻擊者出手並記錄他們的行為。

**Why** 近幾週工業冷凍設備遭到攻擊，作者想知道面對逼真的誘餌時攻擊者會做什麼。

**How** 單一 Python 檔、只用標準函式庫；比對 Shodan 上真實設備的 header 順序、頁面標題、憑證欄位與 TLS 版本，讓 Shodan 把它判為真設備；預設帳密可登入假的店面儀表板，以觀察攻擊者的第二步動作。

**What** 開源 honeypot Coldframe，模擬 Danfoss AK-SM 800A 與 Dixell XWEB，可辨識 CVE-2025-41450（Danfoss「code of the day」登入繞過）並記錄當日代碼是否正確。兩個實例上線一天，目前只看到一般掃描器與 Shodan 爬蟲。

### 重點
- 模擬 Danfoss AK-SM 800A 與 Dixell XWEB；Dixell 版本把頁面補到剛好 8,202 bytes、不送 Server header
- 辨識 CVE-2025-41450 並標記另外三個 Danfoss CVE 與 XWEB 漏洞的攻擊嘗試
- 兩個實例上線一天，只觀察到一般掃描器與 Shodan 爬蟲

**原文：** [hackernews](https://github.com/hedgerow-dev/coldframe)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I built Coldframe, a honeypot that pretends to be a supermarket refrigeration controller. Inspired by the events on industrial fridge installations in the past weeks, I wanted to see what people would try against a convincing fake. To learn more about this I built a honeypot that resembled perfectly the Danfoss AK-SM 800A and Dixell XWEB interfaces. Both of them are recognized on Shodan as real ones (an not as honeypots). It’s one Python file using only the standard library, and it builds on eppser/danfoss-ak-sm-decoy and public research by Synacktiv, Claroty and Ironhackers. Things that were fun to get right: - Matching real units. I used Shodan records of real devices to match header order, page titles, certificate fields and TLS versions. The Danfoss persona sends nginx headers in the same order as a real AK-SM 800A. The Dixell persona sends no Server header and pads its page to exactly 8,202 bytes. - Recognising exploit attempts. It recognises CVE-2025-41450, the Danfoss “code of the day” login bypass, and records whether the submitted code is correct for today. It also tags attempts targeting three other Danfoss CVEs and the XWEB vulnerabilities. - Letting them in. Default logins open a fake store dashboard with defrost buttons, so you see the second move, not just the first. Nothing behind it is real. Two instances have been live for a day. So far they’ve only seen generic scanners and Shodan’s crawler, which is called refrigerator.census.shodan.io. Feedback welcome, especially from anyone who has seen these devices in the field!

</details>