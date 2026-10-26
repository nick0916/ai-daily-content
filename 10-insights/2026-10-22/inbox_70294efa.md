---
id: inbox_70294efa
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0348-hackernews-show-hn-onkey-i-m-a-bad-singer-so-i-buil-15da]]"
title: "Show HN: OnKey – I&#39;m a bad singer, so I built an app to show where I&#39;m off-key"
url: https://github.com/dsmurrell/onkey
source: hackernews
published_at: 2026-10-22T14:04:44+00:00
fetched_at: 2026-10-24T03:52:30.157203+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個 Mac 小工具，先聽一次原曲學會音高軌跡，再讓你跟著唱並對照自己跑調的地方。 **Why** 作者練唱的 app 歌單塞滿非原唱版本，他想跟著原曲練習。 **How** 讓 App 先聽一次歌曲（不存檔，約需數分鐘）學出音高軌跡，再比對使用者歌聲；歌曲辨識用短版 Shazam 指紋，歌詞來自 LRCLIB。作者起初請 Claude Code 寫 Python 原型，能偵測音高但無法即時偵測原唱音高。 **What** OnKey 是 MIT 授權的開源免費 Mac App，可搭配 Spotify、Apple Music 與瀏覽器 YouTube，限 Apple Silicon（M1 以上）與 macOS 14.2 以上。已知限制：伴奏嘈雜時難抓音高、偶爾差一個八度、評分對初學者偏寬鬆。"
key_points:
  - "需先聽歌一次學習音高軌跡，不儲存音樂；僅外送 Shazam 指紋、歌曲資訊、LRCLIB 歌詞查詢與更新檢查"
  - "限制：Apple Silicon M1+、macOS 14.2+；伴奏吵雜時音高難辨、偶有八度誤判"
  - "起點是請 Claude Code 寫 Python 原型，作者提到類似專案 Nightingale 需要本機歌曲庫"
tags: [show-hn, open-source, macos, audio-pitch-detection, claude-code]
topics: [agents.coding_agents, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: OnKey – I'm a bad singer, so I built an app to show where I'm off-key

一個 Mac 小工具，先聽一次原曲學會音高軌跡，再讓你跟著唱並對照自己跑調的地方。

**Why** 作者練唱的 app 歌單塞滿非原唱版本，他想跟著原曲練習。

**How** 讓 App 先聽一次歌曲（不存檔，約需數分鐘）學出音高軌跡，再比對使用者歌聲；歌曲辨識用短版 Shazam 指紋，歌詞來自 LRCLIB。作者起初請 Claude Code 寫 Python 原型，能偵測音高但無法即時偵測原唱音高。

**What** OnKey 是 MIT 授權的開源免費 Mac App，可搭配 Spotify、Apple Music 與瀏覽器 YouTube，限 Apple Silicon（M1 以上）與 macOS 14.2 以上。已知限制：伴奏嘈雜時難抓音高、偶爾差一個八度、評分對初學者偏寬鬆。

### 重點
- 需先聽歌一次學習音高軌跡，不儲存音樂；僅外送 Shazam 指紋、歌曲資訊、LRCLIB 歌詞查詢與更新檢查
- 限制：Apple Silicon M1+、macOS 14.2+；伴奏吵雜時音高難辨、偶有八度誤判
- 起點是請 Claude Code 寫 Python 原型，作者提到類似專案 Nightingale 需要本機歌曲庫

**原文：** [hackernews](https://github.com/dsmurrell/onkey)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi all I was pretty terrible at singing, now I’d say I’m bad but not terrible. This is because I’ve been using a singing app (won’t name it here) that scores me on my pitch and timing throughout the song so that I can improve. Lately however, the app I’ve been using has flooded their song list with songs that aren’t originals. I didn’t like this at all as for me, it’s easier to try to improve when you’re singing along to the original. So, I asked an agent (Claude Code) if it could write some code to listen to Spotify and also listen to me and see if it could detect both pitches and score me. It impressed me by writing some Python and showing me my pitch in the terminal! It couldn’t go all the way though and detect the singer’s pitch in real time. So I found the next best setup and built OnKey, a Mac app that needs to listen to the song once (it doesn’t save it) and then when it’s learnt the song (takes a couple of minutes), you can sing along to the pitch track that it’s learnt. OnKey is free to use and open source under the MIT license. It can listen to Spotify, Apple Music, and YouTube playing in your browser with the right permissions. During the build I found that someone had done something similar in Nightingale, but this requires a library of songs exported to disk and who has this in 2026 (maybe some of you ;) - but we need to help the normies too). You can check out a demo video on the site of me singing (warning given) here: https:&#x2F;&#x2F;singonkey.app The app sends out to find the song info (short Shazam fingerprint, and looks up song details), lyrics (from LRCLIB), and checks for updates. The app never sends the music (it doesn’t save this to disk) and your voice. Everything you’d expect to stay private does. It’s still weak in a few places: - when the song’s backing is noisy it’s hard to pick the pitch track out - sometimes it gets a note an octave off - it’s limited to Apple Silicon Macs, M1 or later, and only macOS 14.2 up because extra drivers aren’t required past this point - the scoring is built for beginners like me so it’s fairly easy on you Would love for people to try it out and let me know what works and what doesn’t for them!

</details>