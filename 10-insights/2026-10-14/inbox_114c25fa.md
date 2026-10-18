---
id: inbox_114c25fa
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0258-hackernews-show-hn-petal-open-source-coscreen-scree-4794]]"
title: "Show HN: Petal, open-source CoScreen/ScreenHero finally free"
url: https://petal.live/
source: hackernews
published_at: 2026-10-14T18:23:14+00:00
fetched_at: 2026-10-18T03:24:01.921404+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "CoScreen 創辦團隊成員 Jason Thomas 發表開源、免費的協作螢幕共享工具 Petal，起因是 Datadog 已於 7 月 31 日終止 CoScreen 服務。他列舉同類產品被收購後下架的先例：Screenhero 被 Slack 於 2015 年收購、2017 年 12 月停止獨立 app；Around 被 Miro 收購、2025 年 3 月關閉；Multi（前身 Remotion）2024 年被 OpenAI acqui-hire，約一個月後關閉。Petal 讓共享視窗以真實視窗呈現在桌面上，可移動、縮放，多人可同時共享，每人有標示名稱的游標，並可點入共享視窗打字與捲動；房間為持久化，例如固定加入「eng-sync」。支援 macOS 與 Windows 及 web app，Linux 列為下一步；媒體傳輸使用 LiveKit，可用託管實例或以 docker-compose 自架。作者特別指出：CoScreen 花了近六年打造，Petal 第一版從零開始不到八週，靠 Fable 與 Astra 等前沿模型完成大量工作，即使即時影像與視窗擷取是極難寫的程式碼。團隊承諾之後會發表詳細心得，說明哪些做法有效、哪些無效。"
key_points:
  - "Petal 完全免費開源且不營利，可自架或 fork，以避免被收購後下架的循環"
  - "技術組成：macOS / Windows / web，媒體走 LiveKit，可用 docker-compose 自架 LiveKit"
  - "開發時程對比：CoScreen 近六年 vs Petal 第一版不到八週（原文稱由 Fable、Astra 等前沿模型完成大量工作）"
tags: [petal, coscreen, open-source, pair-programming, livekit]
topics: [product_and_org.product, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Petal, open-source CoScreen/ScreenHero finally free

CoScreen 創辦團隊成員 Jason Thomas 發表開源、免費的協作螢幕共享工具 Petal，起因是 Datadog 已於 7 月 31 日終止 CoScreen 服務。他列舉同類產品被收購後下架的先例：Screenhero 被 Slack 於 2015 年收購、2017 年 12 月停止獨立 app；Around 被 Miro 收購、2025 年 3 月關閉；Multi（前身 Remotion）2024 年被 OpenAI acqui-hire，約一個月後關閉。Petal 讓共享視窗以真實視窗呈現在桌面上，可移動、縮放，多人可同時共享，每人有標示名稱的游標，並可點入共享視窗打字與捲動；房間為持久化，例如固定加入「eng-sync」。支援 macOS 與 Windows 及 web app，Linux 列為下一步；媒體傳輸使用 LiveKit，可用託管實例或以 docker-compose 自架。作者特別指出：CoScreen 花了近六年打造，Petal 第一版從零開始不到八週，靠 Fable 與 Astra 等前沿模型完成大量工作，即使即時影像與視窗擷取是極難寫的程式碼。團隊承諾之後會發表詳細心得，說明哪些做法有效、哪些無效。

### 重點
- Petal 完全免費開源且不營利，可自架或 fork，以避免被收購後下架的循環
- 技術組成：macOS / Windows / web，媒體走 LiveKit，可用 docker-compose 自架 LiveKit
- 開發時程對比：CoScreen 近六年 vs Petal 第一版不到八週（原文稱由 Fable、Astra 等前沿模型完成大量工作）

**原文：** [hackernews](https://petal.live/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi HN! I’m Jason Thomas, one of the founders of CoScreen. As some of you may know, Datadog sunset the CoScreen service on July 31st. Four of us from the original CoScreen team have spent the last couple months building a free and open source pair programming tool inspired by those that came before us: It’s called Petal ( https:&#x2F;&#x2F;github.com&#x2F;kiruna-labs&#x2F;petal ) Some history first, because when we started CoScreen we had hoped to break the sad and established pattern of this industry. Screenhero was an exceptional tool that a lot of us loved for pairing. Multiple cursors, low latency, you could click your partner’s editor, and just start typing. It felt like magic while we had it. Then Slack bought it in 2015, and shut down the standalone app in December 2017. When Till, Max, and I started CoScreen, we were aware of this history, and wanted to build an even more magical collaboration and screen sharing experience: the entire concept was “throw a window from your laptop up on someone else’s screen, and start collaborating with zero friction.” Datadog acquired us in 2022, and thus began the great adventure of adapting our real-time technology into Datadog products, while also continue developing CoScreen as a standalone tool from the Datadog ecosystem. Datadog invested in the product for years and we’re thankful for that. But CoScreen itself proved, like so many other screen sharing tool acquisitions, to be too tangential from the customer base and core mission. We instead built other communication features in Datadog, the integrations with other video platforms, and also its wildly successful MCP server.
We weren&#x27;t the only ones. Around was bought by Miro and shut down in March 2025. Multi (formerly Remotion) was acqui-hired by OpenAI in 2024 and shut down about a month later. It&#x27;s nearly always the same story: a small team builds something hard that people love, a platform buys it for the team or the feature, and the standalone product doesn&#x27;t survive the integration.
So we decided firmly to do things differently this time. Petal is completely free and open source and we aren&#x27;t monetizing it. If we lose interest or get hit by a bus, you can self-host it or fork it, and nobody can sunset it on you. Honestly it&#x27;s a love letter to everyone in this community that supported us, believed in us, and to liberate collaborative screen sharing from this vicious cycle. We hope through this we can help foster a large and vibrant community around innovating in this product sector.
What Petal does: shared windows show up as real windows on your desktop, movable and resizable, not tiles in a grid. Several people can share at once, everyone gets a labeled cursor, and you can click into any shared window to type and scroll. Rooms are persistent, so you click once to join &quot;eng-sync&quot; instead of passing links around.
It runs on macOS and Windows (Linux is next, this time for real and you can help us!), plus a web app. Media goes over LiveKit. You can use our hosted instance with zero config, or point the app at your own LiveKit server with one docker-compose if you want the traffic to stay on your network or even use an entirely different video backend if you want to.
The part that still feels strange to us: CoScreen took almost six years to build. The first version of Petal took under eight weeks, from scratch, with frontier models like Fable and Astra doing a lot of the work. Real-time video and window capture is some of the most unforgiving code we have ever written, so we didn&#x27;t expect that. We will do a proper writeup on what worked and what didn&#x27;t, and are happy to answer questions about it here.
Till, Darren, Max and I will be in the thread.

</details>