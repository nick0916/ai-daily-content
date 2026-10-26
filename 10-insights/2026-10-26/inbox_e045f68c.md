---
id: inbox_e045f68c
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0250-github-trending-agent-tools-agricidaniel-claude-seo-21-023-197-dd4a]]"
title: "AgriciDaniel/claude-seo ⭐ 21,023(今日 +197)"
url: https://github.com/AgriciDaniel/claude-seo
source: github-trending-agent-tools
published_at: 2026-10-26T02:50:38.157251+00:00
fetched_at: 2026-10-26T03:01:01.234076+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在 Claude Code 裡跑一次完整 SEO 稽核，並依影響程度排出行動清單。 **How** 以 26 個子 skill 與 19 個專門 agent 分工，最多 17 個 agent 同時工作，涵蓋技術 SEO、E-E-A-T、結構化資料與 AI 搜尋（GEO）等。 **What** MIT 授權免費開源，GitHub 星數 21,023（今日 +197）；需 Claude Code 1.0.33 以上與 Python 3.11 至 3.14。原文說明，完整稽核中 5 個需要較多判斷的 agent 使用 Opus，其餘使用 Sonnet，所以比單頁檢查更耗用 Claude 方案額度。"
key_points:
  - "指令：`/seo` 列出所有命令，`/seo setup` 安裝專屬 Python 環境與無頭瀏覽器，`/seo doctor` 隨時檢查"
  - "沒有 Google API 金鑰時 Core Web Vitals 為實驗室估算；可用 `/seo google setup` 串接 PageSpeed Insights、Chrome UX Report、Search Console 與 GA4"
  - "頁面內容需要 JavaScript 才會顯示時，會自動以無頭瀏覽器開啟，單頁應用程式也能稽核"
tags: [seo, claude-code-plugin, geo, technical-seo, agents]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## AgriciDaniel/claude-seo ⭐ 21,023(今日 +197)

在 Claude Code 裡跑一次完整 SEO 稽核，並依影響程度排出行動清單。 **How** 以 26 個子 skill 與 19 個專門 agent 分工，最多 17 個 agent 同時工作，涵蓋技術 SEO、E-E-A-T、結構化資料與 AI 搜尋（GEO）等。 **What** MIT 授權免費開源，GitHub 星數 21,023（今日 +197）；需 Claude Code 1.0.33 以上與 Python 3.11 至 3.14。原文說明，完整稽核中 5 個需要較多判斷的 agent 使用 Opus，其餘使用 Sonnet，所以比單頁檢查更耗用 Claude 方案額度。

### 重點
- 指令：`/seo` 列出所有命令，`/seo setup` 安裝專屬 Python 環境與無頭瀏覽器，`/seo doctor` 隨時檢查
- 沒有 Google API 金鑰時 Core Web Vitals 為實驗室估算；可用 `/seo google setup` 串接 PageSpeed Insights、Chrome UX Report、Search Console 與 GA4
- 頁面內容需要 JavaScript 才會顯示時，會自動以無頭瀏覽器開啟，單頁應用程式也能稽核

**原文：** [github-trending-agent-tools](https://github.com/AgriciDaniel/claude-seo)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Universal SEO skill for Claude Code. 26 sub-skills + 19 sub-agents covering technical SEO, E-E-A-T, schema, GEO/AEO, agent readiness (Lighthouse Agentic Browsing, WebMCP, llms.txt), backlinks, local SEO, e-commerce, international SEO, Google APIs, and PDF/Excel reporting. 9 optional extensions for live SEO data.

Claude SEO

See it in action

Real results

Meet the team

Commands

Pricing

How an audit works

Install

FAQ

Extensions

Star history

More from the same family

License and contributing

Author

 Free, open-source SEO audits inside Claude Code . Rank higher in Google and get cited by AI search.

 Install · Demo · Results · Team · Commands · Pricing · FAQ 

 

 

Claude SEO is a free SEO plugin for Claude Code. Give it any website and it runs a full SEO audit in 10 to 15 minutes, then hands you a clear action plan, sorted by what matters most.

It checks everything a good SEO consultant would:

Claude SEO is built from 26 sub-skills and 19 specialist agents, and up to 17 agents work on your site at the same time. Every recommendation explains why it matters and how you will know it worked.

Type /seo in Claude Code to see every command:

Run a full audit and watch the agents fan out across the site:

Watch the full demo on YouTube

The project's own site, claude-seo.md , audited with Claude SEO from day one: 10.8K Search Console clicks in its first 12 weeks and a 99 mobile PageSpeed score.

Built for:

30 core and extension commands in six groups. Open one to see what is inside; a few more extension commands are in the full command reference .

Typical market prices, for illustration. Your numbers may differ.

Reports are saved as Markdown, and /seo google report turns them into a polished PDF.

Want the details? Read the methodology and the architecture .

You need Claude Code 1.0.33 or newer. Run these three commands inside it:

/seo setup prepares everything Claude SEO needs (its own Python environment and a headless browser) without touching the rest of your system. Run /seo doctor any time to check it.

One-liner (curl, review then run):

Why git clone instead of irm | iex ? Claude Code's own security guardrails flag irm ... | iex as a supply chain risk: downloading and executing remote code without verification. The git clone approach lets you inspect claude-seo\install.ps1 before running it.

Two versions. This public version is MIT licensed and free for everyone. AI Marketing Hub Pro members also get a private version with early access to new features. Members install it with:

Your first audit:

A free, open-source SEO audit tool that runs inside Claude Code. It checks technical SEO, Core Web Vitals, content quality, Schema.org structured data, AI search readiness, local SEO, e-commerce and international SEO, then gives you a prioritized action plan. It follows Google's own documentation, including the AI Optimization Guide .

Yes. It is MIT licensed, with no per-site pricing, no usage limits and no tracking. You only need Claude Code. A few optional extensions connect to paid services where you bring your own account, but everything works without them.

No. Claude SEO works out of the box. If you want real field data, you can connect free Google APIs (PageSpeed Insights, Chrome UX Report, Search Console and Google Analytics 4) with /seo google setup . Your keys stay on your machine.

Google says optimizing for AI search is still SEO, so Claude SEO starts with the basics that AI answers rely on: being indexed, fast and clear. Then /seo geo scores how easy your pages are to quote, checks that AI crawlers can reach them and looks at your brand's presence on Wikipedia, Reddit, YouTube and LinkedIn. /seo agentic checks how well AI agents can use your site.

Yes. When a page needs JavaScript to show its content, Claude SEO opens it in a headless browser automatically, so single-page apps are audited as visitors see them.

Crawlers like Screaming Frog crawl faster and deeper, and big SEO suites have their own backlink databases. Claude SEO does something else: it explains what it finds, sorts it by impact, covers AI search in depth and lets you ask follow-up questions in plain English. Many people use both.

Claude SEO runs inside Claude Code, so the pages and data it analyzes are sent to Claude, Anthropic's model, the same as anything else you work on in Claude Code. Reports are saved as files on your machine. No SEO service or other third party sees your data unless you connect an extension or API yourself. Besides the site you audit, some checks read public sources such as Wikipedia, Reddit and Common Crawl. See PRIVACY.md for the full list.

Requirements. Claude Code 1.0.33 or newer and Python 3.11 to 3.14. /seo setup installs the headless browser for you.

Cost of a full audit. Five agents that need more judgment run on Opus and the rest on Sonnet, so a full /seo audit uses more of your Claude plan than a single-page check. You can change any agent's model in its file under agents/ .

Limits. Without Google API keys, Core Web Vitals are lab estimates and indexing is inferred from the page. Pages that load key content only after scrolling or clicking can give noisy results.

Uninstall. Installed as a plugin: /plugin uninstall claude-seo@agricidaniel-claude-seo . Installed manually:

Optional add-ons that bring in more data. Claude SEO works fully without them.

Setup guides live in extensions/ .

Docs: Installation · Commands · Architecture · Troubleshooting · Extensions setup · Security · Privacy · Contributors

MIT License, see LICENSE . Contributions are welcome: read CONTRIBUTING.md first and mention the checks you ran in your pull request.

Built by Agrici Daniel , AI Workflow Architect, with help from the AI Marketing Hub Pro community.

 

Technical SEO. Crawlability, indexing, sitemaps, robots.txt, redirects, page speed and Core Web Vitals.

Content quality. E-E-A-T (experience, expertise, authority and trust), thin pages and topic coverage.

Structured data. Finds, validates and writes Schema.org markup for rich results.

AI search (GEO). How likely Google AI Overviews, AI Mode, ChatGPT, Perplexity and Gemini are to cite your pages.

Local and e-commerce SEO. Google Business Profile, reviews, map pack, product pages and international sites.

SEO agencies that

</details>