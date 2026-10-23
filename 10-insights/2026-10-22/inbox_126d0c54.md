---
id: inbox_126d0c54
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-hackernews-tell-hn-i-unknowingly-broke-the-php-rce-c661]]"
title: "Tell HN: I unknowingly broke the PHP RCE embargo. I am sorry."
url: https://news.ycombinator.com/item?id=50193416
source: hackernews
published_at: 2026-10-22T10:11:44+00:00
fetched_at: 2026-10-23T00:55:43.010028+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "有人在 Hacker News 提前公開了 PHP 遠端程式碼執行漏洞的消息，事後道歉說自己不知道有禁令。 **Why** 協調式漏洞揭露需要維持 embargo，提前洩露會打亂修補與公告時程。 **How** 作者表示當時聯絡人告知沒有 embargo，他的本意是提醒自行從原始碼編譯 PHP（跟隨 4 週發布週期）的人注意更新的急迫性。 **What** 貼文者針對 CVE-2026-109618 與 CVE-2026-109619 相關的 PHP RCE 道歉，承認造成協調揭露時程與額外工作量的連帶影響，並表示已吸取教訓。"
key_points:
  - "涉及 CVE-2026-109618 與 CVE-2026-109619 的 PHP RCE"
  - "作者稱聯絡人告知無 embargo，因此不知情地提前公開"
  - "造成協調式揭露（coordinated disclosure）時程受影響與額外工作量"
tags: [php, rce, cve, embargo, coordinated-disclosure]
topics: [security]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Tell HN: I unknowingly broke the PHP RCE embargo. I am sorry.

有人在 Hacker News 提前公開了 PHP 遠端程式碼執行漏洞的消息，事後道歉說自己不知道有禁令。 **Why** 協調式漏洞揭露需要維持 embargo，提前洩露會打亂修補與公告時程。 **How** 作者表示當時聯絡人告知沒有 embargo，他的本意是提醒自行從原始碼編譯 PHP（跟隨 4 週發布週期）的人注意更新的急迫性。 **What** 貼文者針對 CVE-2026-109618 與 CVE-2026-109619 相關的 PHP RCE 道歉，承認造成協調揭露時程與額外工作量的連帶影響，並表示已吸取教訓。

### 重點
- 涉及 CVE-2026-109618 與 CVE-2026-109619 的 PHP RCE
- 作者稱聯絡人告知無 embargo，因此不知情地提前公開
- 造成協調式揭露（coordinated disclosure）時程受影響與額外工作量

**原文：** [hackernews](https://news.ycombinator.com/item?id=50193416)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I posted here about the then-upcoming PHP RCEs related to CVE-2026-109618 &amp; CVE-2026-109619. I appreciate this has had considerable knock-on effects with the schedule for co-ordinated disclosure, and created additional workload. I am truly sorry. I take full responsibility for my actions. It was not remotely my intention to cause any of the subsequent side effects. At the time of posting, I didn&#x27;t know about any embargo. My contact had told me there was no embargo, and her contact had told her the same thing. As someone who follows the 4-weekly PHP release cycle and compiles it from source, my intention was to alert others in a similar position to be aware of the importance&#x2F;urgency of the updates. That clearly backfired in a pretty wild fashion. I have learned my lesson.

</details>