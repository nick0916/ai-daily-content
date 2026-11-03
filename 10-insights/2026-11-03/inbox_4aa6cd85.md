---
id: inbox_4aa6cd85
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2347-simon-willison-i-discovered-a-sound-that-leaks-your-exa-7c34]]"
title: "I discovered a sound that leaks your exact location (and it's everywhere) - YouTube"
url: https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/
source: simon-willison
published_at: 2026-11-03T05:32:25+00:00
fetched_at: 2026-11-03T23:53:01.633552+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "從影片背景裡極微弱的飛機聲，就能推算出影片拍攝的確切地點。 **Why** 影片音軌看似無害，卻可能洩漏拍攝位置，是隱私風險。 **How** 擷取背景飛機噪音的 Doppler 曲線，再與 ADS-B 航班資料比對速度、距離與不同航班之間的間隔。 **What** YouTuber Colsto 展示的 OSINT 手法，Simon Willison 稱之為「天才之作」，經 Lobste.rs 分享。"
key_points:
  - "以背景飛機聲的 Doppler 曲線推算飛行狀態"
  - "與 ADS-B 航班資料交叉比對速度、距離與航班間隔"
  - "可定位影片的確切拍攝地點"
tags: [osint, privacy, ads-b, youtube]
topics: [security]
importance: 2
novelty: 4
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I discovered a sound that leaks your exact location (and it's everywhere) - YouTube

從影片背景裡極微弱的飛機聲，就能推算出影片拍攝的確切地點。

**Why** 影片音軌看似無害，卻可能洩漏拍攝位置，是隱私風險。

**How** 擷取背景飛機噪音的 Doppler 曲線，再與 ADS-B 航班資料比對速度、距離與不同航班之間的間隔。

**What** YouTuber Colsto 展示的 OSINT 手法，Simon Willison 稱之為「天才之作」，經 Lobste.rs 分享。

### 重點
- 以背景飛機聲的 Doppler 曲線推算飛行狀態
- 與 ADS-B 航班資料交叉比對速度、距離與航班間隔
- 可定位影片的確切拍攝地點

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I discovered a sound that leaks your exact location (and it's everywhere) - YouTube 
Genius piece of OSINT by Colsto, who demonstrates how you can take almost imperceptible background noise of planes from a video soundtrack, figure out their Doppler curves, then cross reference them against ADS-B data to find the exact location of the video based on their speed, distance, and gaps between different flights. 
 

 Via Lobste.rs 

 Tags: privacy , youtube

</details>