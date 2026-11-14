---
id: inbox_ababe34b
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0148-hackernews-show-hn-yogurt-free-private-open-source-b216]]"
title: "Show HN: Yogurt – Free, private, open-source alternative to Granola"
url: https://github.com/FrigadeHQ/yogurt
source: hackernews
published_at: 2026-11-11T15:33:06+00:00
fetched_at: 2026-11-14T01:53:42.939857+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一款完全在本機跑 AI 的開源會議筆記工具，錄音和逐字稿都不離開你的電腦。 **Why** 作者認為摘要會議筆記不需要頂級模型，而現有開源筆記工具缺日曆整合、MCP server，或要求註冊帳號，也不夠好用。 **How** 用 whisper.cpp 做轉錄（系統支援時用 Apple 的 SpeechAnalyzer），摘要與問答用 llama.cpp 跑本機開源權重 LLM，依硬體能力自動下載合適的模型；以 Electron 支援 Windows/Mac/Linux。 **What** Yogurt（FrigadeHQ/yogurt），MIT 授權、免費的桌面 app，定位為 Granola 的開源替代品，背景運行、不加入通話。內建本機 MCP server，可把筆記分享給 Anthropic、OpenAI 等前沿模型；另有回音偵測/降低、全域/資料夾/單筆層級搜尋與自動結束錄音。"
key_points:
  - "技術棧：Electron + whisper.cpp（轉錄）+ Apple SpeechAnalyzer（支援時）+ llama.cpp（本機 LLM 摘要/問答）"
  - "本機 MCP server 讓使用者自行決定是否把筆記交給 Anthropic、OpenAI 等雲端模型，不需付費中介服務"
  - "MIT 授權，筆記、錄音、摘要不離開電腦；含日曆整合、回音處理、三層級搜尋、自動結束錄音"
tags: [open-source, meeting-notes, on-device-ai, local-llm, mcp]
topics: [product_and_org.product, agents.mcp, foundation_models.open_weights]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Yogurt – Free, private, open-source alternative to Granola

一款完全在本機跑 AI 的開源會議筆記工具，錄音和逐字稿都不離開你的電腦。

**Why** 作者認為摘要會議筆記不需要頂級模型，而現有開源筆記工具缺日曆整合、MCP server，或要求註冊帳號，也不夠好用。

**How** 用 whisper.cpp 做轉錄（系統支援時用 Apple 的 SpeechAnalyzer），摘要與問答用 llama.cpp 跑本機開源權重 LLM，依硬體能力自動下載合適的模型；以 Electron 支援 Windows/Mac/Linux。

**What** Yogurt（FrigadeHQ/yogurt），MIT 授權、免費的桌面 app，定位為 Granola 的開源替代品，背景運行、不加入通話。內建本機 MCP server，可把筆記分享給 Anthropic、OpenAI 等前沿模型；另有回音偵測/降低、全域/資料夾/單筆層級搜尋與自動結束錄音。

### 重點
- 技術棧：Electron + whisper.cpp（轉錄）+ Apple SpeechAnalyzer（支援時）+ llama.cpp（本機 LLM 摘要/問答）
- 本機 MCP server 讓使用者自行決定是否把筆記交給 Anthropic、OpenAI 等雲端模型，不需付費中介服務
- MIT 授權，筆記、錄音、摘要不離開電腦；含日曆整合、回音處理、三層級搜尋、自動結束錄音

**原文：** [hackernews](https://github.com/FrigadeHQ/yogurt)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hey HN, I’m Eric and I want to share an OSS project that I’ve been building in my free time. Yogurt is a free, MIT licensed desktop app that uses on-device AI models to transcribe, summarize, and chat with your meetings. Here's a quick demo video: https://www.youtube.com/watch?v=BFfbXAwRq98 Similar to Granola, Yogurt runs in the background and does not join your calls. But unlike Granola, Yogurt is open-source, free to use, and private. Your meeting transcripts, call recordings, and summaries never leave your computer. As small OSS models have gotten faster and more powerful, Yogurt seemed like a pretty obvious win for privacy and cost conscious folks. You do not need a frontier model to summarize meeting notes or answer questions about them. And if you want to make your notes available to a frontier model, you can just share it with Anthropic, OpenAI, etc. directly via Yogurt’s local MCP server. There’s no need to use a paid cloud service as a middleman. I tried some of the most popular OSS note taking tools, and most were missing features like calendar integration, MCP server, etc. or required you to connect or create an account. And more than that, they didn’t feel polished enough for it to be something I actually wanted to use daily, and so I built Yogurt to scratch that itch. I spent a lot of time fine-tuning every UI interaction/animation and optimizing the model calls to get the most out of your hardware + make it snappy. To support Windows/Mac/Linux, I decided to go with Electron. I use whisper.cpp for transcription and Apple’s on-device SpeechAnalyzer if your system supports it. For call summaries and questions, I use a local open weight LLM that automatically gets downloaded and set up based on what your hardware can handle without your cooling fans firing off like crazy (this part uses llama.cpp). I’ve spent a lot of time working on details like echo detection/reduction, global/folder/local level search respectively, and auto-end recordings. Hope this is useful for any of you who have held out on using AI note tools for privacy or cost reasons, or for folks using cloud tools who want to switch to something free and open source that still feels great to use. Would love to hear what you think about the onboarding and note taking experience :)

</details>