---
id: inbox_5d21e2fd
date: 2026-11-27
source_ref: "[[00-inbox/2026-11-27/0053-github-trending-agent-tools-zhouxiaoka-autoclip-16-934-774-95c2]]"
title: "zhouxiaoka/autoclip ⭐ 16,934(今日 +774)"
url: https://github.com/zhouxiaoka/autoclip
source: github-trending-agent-tools
published_at: 2026-11-27T00:53:19.226928+00:00
fetched_at: 2026-11-27T01:04:26.218950+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個開源、本地運行的 AI 工具，把長影片自動剪成短影音。 **Why** 原文定位為 OpusClip 的開源替代方案，主打零訂閱、免付費牆。 **How** 剪輯與渲染都在本機執行，語音辨識可用本地 Whisper / SenseVoice 或雲端 ASR，分析可接 Ollama / LM Studio 離線運行。 **What** 支援 TikTok、Shorts、Reels、抖音、小紅書、Bilibili 等平台，內建 MCP（`uvx autoclip-mcp`）供 Claude Code、Cursor 等代理呼叫，目前 v1.6、MIT 授權，GitHub 顯示 16,934 星（今日 +774）。"
key_points:
  - "本地優先架構：剪輯與渲染在本機完成，可搭配 Ollama 與 Whisper 完全離線運行"
  - "內建 MCP server，安裝指令為 `claude mcp add autoclip -- uvx autoclip-mcp`，可讓編程代理直接剪片"
  - "支援 TikTok、YouTube Shorts、Reels、抖音、小紅書、Bilibili 等多平台輸出，並可自動產生字幕與封面"
tags: [video-clipping, open-source, mcp, local-first, whisper]
topics: [agents.mcp, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## zhouxiaoka/autoclip ⭐ 16,934(今日 +774)

一個開源、本地運行的 AI 工具，把長影片自動剪成短影音。

**Why** 原文定位為 OpusClip 的開源替代方案，主打零訂閱、免付費牆。

**How** 剪輯與渲染都在本機執行，語音辨識可用本地 Whisper / SenseVoice 或雲端 ASR，分析可接 Ollama / LM Studio 離線運行。

**What** 支援 TikTok、Shorts、Reels、抖音、小紅書、Bilibili 等平台，內建 MCP（`uvx autoclip-mcp`）供 Claude Code、Cursor 等代理呼叫，目前 v1.6、MIT 授權，GitHub 顯示 16,934 星（今日 +774）。

### 重點
- 本地優先架構：剪輯與渲染在本機完成，可搭配 Ollama 與 Whisper 完全離線運行
- 內建 MCP server，安裝指令為 `claude mcp add autoclip -- uvx autoclip-mcp`，可讓編程代理直接剪片
- 支援 TikTok、YouTube Shorts、Reels、抖音、小紅書、Bilibili 等多平台輸出，並可自動產生字幕與封面

**原文：** [github-trending-agent-tools](https://github.com/zhouxiaoka/autoclip)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AutoClip|The open-source OpusClip alternative — local-first AI clipping & MCP server, zero subscriptions. 一个链接,一键出片。开源 AI 视频剪辑桌面工具,将播客、访谈、课程等长视频自动剪成短视频,生成字幕、封面和发布文案,适配抖音、小红书、TikTok、Reels 与 YouTube Shorts。

AutoClip

Overview

What's New in v1.6

Examples

Quick Start

Benchmarks

Sponsor ❤️

Cloud Transcription (Alibaba Cloud)

FAQ

Documentation

Contribute

Turn any video, link, or live stream into ready-to-post clips.

Vertical · Interview & Podcast

Landscape · Original Aspect Ratio

1. Desktop App

2. CLI & MCP (Claude Code, Cursor, Codex, OpenCode & scripts)

3. Docker / Web

The open-source OpusClip alternative — local-first AI clipping for podcasts, interviews, and gaming streams with smart reframing, captions, covers, titles, and built-in MCP for AI agents . Zero subscriptions, no paywall.

 

 

 Website · Download · Live Replays (v1.6) · Showcase · Quick Start · Docs · Issues 

 English · 简体中文 · 繁體中文 · 日本語 · 한국어 · Español · Português · Русский · Français · Bahasa Indonesia · Türkçe · Tiếng Việt · Deutsch 

⭐ Free, MIT-licensed, zero subscriptions — everything cuts and renders on your machine. Star the repo if you find it useful! 

Drop in a link, local video, or live stream replay — AutoClip finds the best moments, tracks the speaker, burns in captions, generates covers, and exports ready-to-post clips for TikTok, Shorts, Reels, YouTube, Douyin, Xiaohongshu, and Bilibili.

Local-first by design: cutting and rendering run directly on your computer with no upload queues and no monthly fee. Bring your own API key or run 100% offline with Ollama / LM Studio + Whisper / SenseVoice .

Home → 6 Live Replay sources → OBS WebSocket setup → Twitch import → Finished clip with captions & one-click publish.

Click any thumbnail or ▶ Play to watch full clips rendered by AutoClip. Language labels indicate burned-in subtitle language.

Browse 16+ clips, covers, and post copy in the Showcase → , or share your own clips . Source copyrights remain with their original creators.

Installers are built publicly on GitHub Actions ( Desktop Build ) with build-provenance.json SHA-256 verification. First launch on an unsigned build: on macOS run xattr -dr com.apple.quarantine "/Applications/AutoClip Desktop.app" (or System Settings → Privacy & Security → Open Anyway ); on Windows click More info → Run anyway on SmartScreen. See Code Signing & Verification Policy (notarization tracked in #119 ).

Let AI coding agents clip videos directly from your terminal ( claude mcp add autoclip -- uvx autoclip-mcp ). Full MCP setup guides: English · 简体中文 · 日本語 · 한국어 · Español · Deutsch .

To build a local MCPB bundle without publishing, run python scripts/pack_mcpb.py (never run smithery mcp publish automatically).

Open the web UI at http://localhost:3000 (API docs at http://localhost:8000/docs ). See Docker Guide for bind-mount permissions and custom origins.

Measured on an Apple Silicon Mac (LLM cost estimated with qwen-plus ; excludes cloud ASR and AI image generation; check your provider bill for exact usage):

Affiliate link (separate from the sponsor above): sign up on Alibaba Cloud, create an API key in the Bailian console, and enable Bailian cloud ASR under Settings → Default models → Speech to subtitles .

Yes — AutoClip is free and MIT-licensed. Cloud analysis, transcription, and AI covers use your own API keys at provider rates (local cover layout is free by default). Ollama and LM Studio require no cloud key. Direct publishing uses your own Bilibili or Upload-Post account.

Cutting and rendering run locally. Cloud analysis only sends transcript text; vision models only receive sampled frames; cloud ASR uploads audio. Running local LLMs + Whisper / SenseVoice keeps everything offline. Analytics and crash reports can be turned off in Settings. See Privacy .

Podcasts, interviews, talks, courses, and gaming live stream replays (OBS / Twitch / YouTube / Kick / Discord). Sources with existing subtitles are fastest; otherwise use local Whisper / SenseVoice or cloud ASR. For gameplay or low-dialogue streams, enable a vision-capable model.

Check the failed stage: subtitles/transcription, model connection, FFmpeg, disk space, or platform length limits (YouTube long-form requires ≥180s; use Shorts, TikTok, or Bilibili for shorter clips). If it still fails, open an issue with autoclip --version , OS, model, and redacted logs, or check Known Issues (#96) .

Troubleshooting · Known Issues

PRs, bug reports, sample clips, and translations are welcome. If AutoClip saves you time, a ⭐ star helps!

AutoClip is maintained solo — please expect async replies (no live or 1-on-1 setup support).

Built with FastAPI, React, Tauri, FFmpeg, yt-dlp, Whisper, and FunASR. MIT License .

Download the latest installer from GitHub Releases ( aarch64.dmg for Apple Silicon macOS, x64-setup.exe for Windows). Portable Python and FFmpeg are bundled.

Open Settings , pick a cloud provider (or start Ollama / LM Studio), test the connection, and save — or click Try the built-in example with no API key.

Paste a video link, drop a file, or switch to Live Replay to connect OBS or import a stream recording. Pick your platforms and click Generate .

Alibaba Cloud signup (affiliate link)

Bailian console — create your API key

Community: GitHub Discussions · First-Clip Q&A · Feature Ideas

Bug reports: use the issue template with OS, version, model, repro steps, and redacted logs

Partnerships: christine_zhouye@163.com

uvx autoclip-mcp
npx skills add zhouxiaoka/autoclip

autoclip --version
autoclip produce talk.mp4 --srt talk.srt --platform tiktok --portrait-style podcast --json
autoclip outputs PROJECT_ID --export-kits

# Install from a downloaded CLI/MCP release ZIP wheel python3 -m venv .venv && source .venv/bin/activate
python -m pip install -r requirements.txt
python -m pip install --force-reinstall --no-deps autoclip_mcp- * -py3-none-any.whl # Or install from source python -m pip install --no-deps .

git clone https://github.com/zhouxiaoka/autoclip.git cd autoclip
cp env.example .env
mkdir -p data logs uploads
docker compose up -d --build

</details>