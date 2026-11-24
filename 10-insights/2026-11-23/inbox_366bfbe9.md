---
id: inbox_366bfbe9
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-substack-lennys-newsletter-openclaw-for-executives-automate-every-1-d279]]"
title: "OpenClaw for executives: Automate every 1% annoyance | Ankit Maheshwari (Innovaccer)"
url: https://www.lennysnewsletter.com/p/openclaw-for-executives-automate
source: substack-lennys-newsletter
published_at: 2026-11-23T13:04:43+00:00
fetched_at: 2026-11-24T02:15:34.428002+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "同一集 Lenny 訪談的節目頁：CTO 如何用 OpenClaw 打造個人 AI 幕僚長。 **Why** Ankit Maheshwari 想擺脫自己因核准流程而成為瓶頸的狀況，並降低每月 $500–600 的 Anthropic 帳單。 **How** 先從核准流程自動化起步，再擴及其他事務；以 soul file 與護欄建立信任，並把語音通話拆成獨立子代理人；同時測試本地模型能否取代昂貴的雲端模型。 **What** 節目由 Claire Vo 主持，內容涵蓋 OpenClaw 在 Mac Mini 上的使用、Navan 機票核准、訂餐、智慧家居與 GLM Flash 本地模型測試，並列出 OpenClaw、Bland AI、Navan、ElevenLabs、Twilio、Claude Code、Codex 等引用工具。本文為節目大綱與章節時間軸，內容與同集的另一篇重點整理重疊。"
key_points:
  - "章節涵蓋：為何選 OpenClaw、Navan 機票核准的通知問題、soul file 與子代理人結構（健康教練、email 分流、master soul）"
  - "單一全域代理人在人設上出現幻覺，改用範圍明確的子代理人；語音通話獨立為專責子代理人"
  - "引用工具包含 Bland AI、Twilio、ElevenLabs、Claude Code、Codex、DoorDash Meal Manager，並測試 GLM Flash 本地模型"
tags: [openclaw, subagents, local-models, voice-agent, lennys-podcast]
topics: [agents.frameworks, product_and_org.adoption]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenClaw for executives: Automate every 1% annoyance | Ankit Maheshwari (Innovaccer)

同一集 Lenny 訪談的節目頁：CTO 如何用 OpenClaw 打造個人 AI 幕僚長。

**Why** Ankit Maheshwari 想擺脫自己因核准流程而成為瓶頸的狀況，並降低每月 $500–600 的 Anthropic 帳單。

**How** 先從核准流程自動化起步，再擴及其他事務；以 soul file 與護欄建立信任，並把語音通話拆成獨立子代理人；同時測試本地模型能否取代昂貴的雲端模型。

**What** 節目由 Claire Vo 主持，內容涵蓋 OpenClaw 在 Mac Mini 上的使用、Navan 機票核准、訂餐、智慧家居與 GLM Flash 本地模型測試，並列出 OpenClaw、Bland AI、Navan、ElevenLabs、Twilio、Claude Code、Codex 等引用工具。本文為節目大綱與章節時間軸，內容與同集的另一篇重點整理重疊。

### 重點
- 章節涵蓋：為何選 OpenClaw、Navan 機票核准的通知問題、soul file 與子代理人結構（健康教練、email 分流、master soul）
- 單一全域代理人在人設上出現幻覺，改用範圍明確的子代理人；語音通話獨立為專責子代理人
- 引用工具包含 Bland AI、Twilio、ElevenLabs、Claude Code、Codex、DoorDash Meal Manager，並測試 GLM Flash 本地模型

**原文：** [substack-lennys-newsletter](https://www.lennysnewsletter.com/p/openclaw-for-executives-automate)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ankit Maheshwari , the CTO of Innovaccer, walks me through the OpenClaw Jarvis he still runs on a Mac Mini. He started with the approvals that were making him the bottleneck at work, then kept going until the same system was ordering his lunch, calling coworkers who haven’t responded on Slack, negotiating restaurant reservations, and turning on the AC before he gets home. We get into the soul files and guardrails that make it trustworthy, why he split voice calling into its own subagent, and why he’s pressure-testing GLM 5.3 Flash against a $500-to-$600-a-month Anthropic bill. Listen or watch on YouTube , Spotify , or Apple Podcasts What you’ll learn: Why he’s still on OpenClaw The automation that started it all How soul files and subagents actually work The mid-flight moment that tested his guardrails How Jarvis calls people who don’t reply on Slack Whether a local model can cut a $500-to-$600 bill How Jarvis took over his smart home Why he just talks to OpenClaw like a new hire Brought to you by: Parallel —Web search built for AI scale GiveDirectly —Send cash to the world’s poorest In this episode, we cover: ( 00:00 ) Teaser ( 02:26 ) Why OpenClaw ( 03:57 ) Approvals ( 05:01 ) Flight approvals in Navan, the notification problem, and the domino effect ( 06:38 ) Soul files and subagents ( 07:28 ) Subagent structure: health coach, email triage, and the master soul ( 08:45 ) Why one global agent hallucinated on personas, and the fix ( 10:53 ) Why well-scoped subagents beat one agent for everything ( 11:42 ) How he builds ( 15:52 ) Food ordering ( 17:36 ) Travel and restaurants ( 19:45 ) Smart home ( 21:07 ) The 1% annoyance rule ( 24:12 ) Guardrails ( 25:49 ) Local models and cost ( 27:37 ) What GLM 5.2 Flash can and can’t do Tools referenced: OpenClaw: https://openclaw.ai/ Bland AI: https://www.bland.ai Navan: https://navan.com Coupa: https://www.coupa.com DoorDash Meal Manager: https://www.doordash.com/business/meal-plans/ GLM 5.3 Flash: https://docs.z.ai/guides/vlm/glm-5.3-flash WhatsApp: https://www.whatsapp.com Android Auto: https://www.android.com/auto/ Claude Code: https://claude.ai/code Codex: https://chatgpt.com/codex Slack: https://slack.com ElevenLabs: https://elevenlabs.io Twilio: https://www.twilio.com Other reference: REA (Reverse Engineer Anything): https://github.com/morluto/rea Where to find Ankit Maheshwari: LinkedIn: https://www.linkedin.com/in/ankit-mah X: https://x.com/ankitTwiits Innovaccer: https://innovaccer.com Where to find Claire Vo: ChatPRD: https://www.chatprd.ai/ Website: https://clairevo.com/ LinkedIn: https://www.linkedin.com/in/clairevo/ X: https://x.com/clairevo Production and marketing by https://penname.co/ . For inquiries about sponsoring the podcast, email jordan@penname.co.

</details>