---
id: inbox_7f6dd48c
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/0250-creator-economy-use-my-video-short-skill-to-turn-any-raw-91d9]]"
title: "Use My /Video-Short Skill to Turn Any Raw Recording Into a Compelling Short"
url: https://creatoreconomy.so/p/use-my-video-short-skill-to-create-compelling-shorts
source: creator-economy
published_at: 2026-10-21T14:01:34+00:00
fetched_at: 2026-10-26T03:00:20.643834+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 代理把原始錄影剪成含字幕與 B-roll 的短影片。 **How** 代理先轉錄錄影並剪掉重拍、停頓與空白，研究主題、找網路 B-roll，列出逐場景計畫後再依回饋修改。 **What** 免費開源的 /video-short skill（GitHub: petergyang/video-short）提供四種版面（A-roll、Punch、Split、B-roll）與逐幀審閱頁面；AI 影片與音樂為選用，需啟用計費的 Gemini API。"
key_points:
  - "/video-short 可自動加入 B-roll、動態圖形（HTML 撰寫）、逐字字幕與音樂"
  - "提供審閱頁面，可暫停在任一幀留下回饋，代理套用後以新版本重新載入"
  - "需安裝 ffmpeg、yt-dlp、Parakeet、HyperFrames、Python、Node.js，約需 1 GB 磁碟空間"
tags: [video-short, claude-code-skill, short-video, parakeet, hyperframes]
topics: [agents.coding_agents, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Use My /Video-Short Skill to Turn Any Raw Recording Into a Compelling Short

讓 AI 代理把原始錄影剪成含字幕與 B-roll 的短影片。 **How** 代理先轉錄錄影並剪掉重拍、停頓與空白，研究主題、找網路 B-roll，列出逐場景計畫後再依回饋修改。 **What** 免費開源的 /video-short skill（GitHub: petergyang/video-short）提供四種版面（A-roll、Punch、Split、B-roll）與逐幀審閱頁面；AI 影片與音樂為選用，需啟用計費的 Gemini API。

### 重點
- /video-short 可自動加入 B-roll、動態圖形（HTML 撰寫）、逐字字幕與音樂
- 提供審閱頁面，可暫停在任一幀留下回饋，代理套用後以新版本重新載入
- 需安裝 ffmpeg、yt-dlp、Parakeet、HyperFrames、Python、Node.js，約需 1 GB 磁碟空間

**原文：** [creator-economy](https://creatoreconomy.so/p/use-my-video-short-skill-to-create-compelling-shorts)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Dear subscribers, Today, I&#8217;m excited to launch /video-short , my new AI skill that lets anyone turn a raw recording into a compelling short video. Best of all, it&#8217;s 100% free. /video-short can add B-roll, motion graphics, captions, music, and more using your favorite AI agents. It even comes with a review page to let you give feedback to AI on any frame until the short feels just right. Watch my tutorial now to see exactly how the skill works and get the skill on GitHub. Get /video-short for free on GitHub If you find the skill useful, please star the GitHub repo so more people can find it. You can also upgrade to paid to get 16+ other quality AI skills, $600+ in Grok Bot and other discounts, my personal AI course, and an invite to my private Slack community. Below&#8217;s an explainer on what the skill can do and how you can install it for free. I&#8217;m proud to partner with Google Gemini I use Gemini 4 Argon in my video short tutorial because I think it&#8217;s the best multimodal model with great APIs for image, video, and music generation. Get a Gemini API key in AI Studio and try it with my skill to create your next short. Try Gemini 4 Argon in AI Studio What /video-short can do /video-short makes it easy for you to iterate with AI to create compelling shorts. The best part of the skill is it gives you a review page to give feedback to your AI agent on any frame until the short feels right: The skill supports making shorts with 4 different layouts: A-roll: You, full screen. Punch: A tighter shot of you for emphasis. Split: A visual on top, you below. B-roll: A visual full screen while you keep talking. It can also add the following automatically: Captions that match what you say, word for word. Motion graphics written in HTML to bring the short to life. B-roll footage found online that&#8217;s relevant to what you&#8217;re saying. AI video and music (optional) generated with Gemini Omni Flash and Lyria. This step needs a Gemini API key with billing enabled. How to install /video-short To install the skill, just paste this into Claude Code, ChatGPT Desktop, Antigravity, or your favorite AI agent: Install the /video-short skill from https://github.com/petergyang/video-short The first time you run the skill by typing &#8220;/video-short&#8221;, it&#8217;ll check if you have ffmpeg (to cut and encode video), yt-dlp (to pull B-roll), Parakeet (to transcribe the video), HyperFrames (to render the video), plus Python and Node.js. If you don&#8217;t have the above, it&#8217;ll offer to install what&#8217;s missing. Plan for around 1 GB of disk space, mostly for the Parakeet speech model (smaller models aren&#8217;t as accurate). How to use /video-short I&#8217;ve made this skill as simple as possible to use, just follow these 4 steps: Install. Paste the install prompt above into your AI agent. You only do this once. Upload. Record yourself talking, then run the skill and point it at your raw video: /video-short edit my video at [path/to/video.mp4] . It&#8217;ll transcribe the recording and cut retakes, false starts, and dead air. Plan. It researches the topic, finds B-roll from the web, and shows you a scene-by-scene plan in chat: what&#8217;s on screen, the words spoken, and anything it wants to generate. Reply &#8220;go&#8221; or ask for changes. Iterate. Once your agent is done with a draft edit, it&#8217;ll open the review page for you to play the short, pause on any frame, and leave feedback. The agent will then apply your feedback before reloading the review page with a new version. Here&#8217;s an example short that I created using the skill: Get /video-short for free on GitHub and star the repo if you find it useful!

</details>