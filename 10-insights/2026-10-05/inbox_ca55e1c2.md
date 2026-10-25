---
id: inbox_ca55e1c2
date: 2026-10-05
source_ref: "[[00-inbox/2026-10-05/0101-substack-dev-leader-ai-agents-c-pipelines-and-ef-core-perfor-3673]]"
title: "AI Agents, C# Pipelines, and EF Core Performance"
url: https://devleader.substack.com/p/ai-agents-c-pipelines-and-ef-core
source: substack-dev-leader
published_at: 2026-10-05T04:28:11+00:00
fetched_at: 2026-10-25T01:08:31.870802+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dev Leader 週報，涵蓋 Vercel Eve durable agent、C# pipeline 並行、EF Core 效能與 RAG 授權。 **What** 本期文章包括 Vercel Eve 的 durable agent runtime（filesystem-first 設計、replay 邊界、版本固定的 HTTP client）、C# pipeline 各並行模型的吞吐與排序、用 .NET 10 建立有界 TPL Dataflow pipeline、Specification Pattern 在 EF Core 的轉譯陷阱，以及 RAG 的租戶過濾、provenance 與刪除生命週期。影片提到作者改用免費 LLM 供應商寫程式後「全部垮掉」，以及 AI agent 放任後會產生過多 CI/CD bloat。"
key_points:
  - "RAG 授權與資料生命週期：server 端衍生 scope、租戶過濾、provenance、revision、刪除、cache 與稽核紀錄"
  - "EF Core Specification Pattern 效能：檢查轉譯邊界、SQL、query 形狀、命令數量與執行計畫，以實測為依據"
  - "作者經驗：改用免費 LLM 供應商取代 frontier 模型寫程式效果不佳；agent 放任會產生過多 CI/CD bloat"
tags: [vercel-eve, dotnet, rag, ef-core, weekly-recap]
topics: [agents.frameworks, engineering.rag, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## AI Agents, C# Pipelines, and EF Core Performance

Dev Leader 週報，涵蓋 Vercel Eve durable agent、C# pipeline 並行、EF Core 效能與 RAG 授權。 **What** 本期文章包括 Vercel Eve 的 durable agent runtime（filesystem-first 設計、replay 邊界、版本固定的 HTTP client）、C# pipeline 各並行模型的吞吐與排序、用 .NET 10 建立有界 TPL Dataflow pipeline、Specification Pattern 在 EF Core 的轉譯陷阱，以及 RAG 的租戶過濾、provenance 與刪除生命週期。影片提到作者改用免費 LLM 供應商寫程式後「全部垮掉」，以及 AI agent 放任後會產生過多 CI/CD bloat。

### 重點
- RAG 授權與資料生命週期：server 端衍生 scope、租戶過濾、provenance、revision、刪除、cache 與稽核紀錄
- EF Core Specification Pattern 效能：檢查轉譯邊界、SQL、query 形狀、命令數量與執行計畫，以實測為依據
- 作者經驗：改用免費 LLM 供應商取代 frontier 模型寫程式效果不佳；agent 放任會產生過多 CI/CD bloat

**原文：** [substack-dev-leader](https://devleader.substack.com/p/ai-agents-c-pipelines-and-ef-core)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This week: Explore durable AI agents with Vercel Eve, practical AI development workflows, and the risks of relying on free LLM providers. Dig into C# pipeline parallelism, TPL Dataflow, EF Core specification performance, and secure RAG retrieval. The videos also cover startup tradeoffs, junior developer soft skills, engineering leadership, and code review pressure. Like what you read or watched from the recap? I&#8217;d love if you helped share on Reddit or Daily.dev so others can see! Weekly Recap Should You Leave A Stable Job For An AI Startup? - Principal Engineering Manager AMA Startups can be an exciting opportunity, but what does that look like compared to something more stable? And does stable REALLY exist anymore? Did it ever? As with all livestreams, I&#8217;m looking forward to answering YOUR questions! So join me live and ask in the chat, or you can comment now, and I can try to get it answered while I stream. I Used Free LLM Providers To Code And It All Fell Apart In this video, I talk about how I tried using some free LLM providers instead of frontier models. Buckle up. I&#8217;m A Junior Developer - How Do I Improve My Soft Skills? From the ExperiencedDevs subreddit, this developer wanted perspectives on improving soft skills as a junior software engineer. Some Of The Stuff I&#8217;m Building With AI In this video, I catch up on some of the side projects I am building with support from AI. My Agents Are Their Own Worst Enemies. In this video, I talk about how my AI agents, if left to their own, continue to build too much CI/CD bloat. I&#8217;m Building An AI-Powered SQL Workbench With Copilot In this video, I talk about a product I am building with AI for working with SQL databases. The Engineers Are TOO Productive! What Do We Do?! From the ExperiencedDevs subreddit, this engineering manager wanted perspectives on what to do when the developers are... TOO productive. Side Projects And Building Games With AI Development Flows In this video, I talk more about building side projects and diving into a bit of game development using AI. We&#8217;re Pushing Code To Production Without Reviewing It From the ExperiencedDevs subreddit, this developer wanted perspectives on dealing with pressure to deliver software and the side effects of rushing that code. Vercel Eve Explained: Durable AI Agents and C# Integration Understand Vercel Eve&#8217;s durable agent runtime, filesystem-first design, replay boundaries, and how C# applications connect through a version-pinned HTTP client. Are C# Pipeline Stages Parallel? Throughput, Ordering, and Benchmarks Measure C# pipeline parallelism and throughput across sequential, async, item, stage, and data-parallel models without inventing performance claims or results. Specification Pattern Performance and EF Core Translation Traps Diagnose Specification Pattern performance in EF Core through translation boundaries, SQL inspection, query shape, command counts, plans, and measured evidence. RAG Retrieval Authorization and Data Lifecycle: Tenant Filters, Provenance, and Deletion Learn RAG access control and data lifecycle patterns for .NET: server-derived scopes, tenant filters, provenance, revisions, deletion, caches, and audit trails. Build a TPL Dataflow Pipeline in Modern .NET Build a bounded TPL Dataflow pipeline in .NET 10 with explicit capacity, concurrency, ordering, cancellation, coordinated faults, and terminal completion. Join me and other software engineers in the private Discord community ! Resume reviews and interview guidance ! Software engineering podcast and livestreams ! My Code Commute vlogs are on YouTube ! All of my weekly vlogs are on YouTube ! Remember to check out my courses , including this awesome discounted bundle for C# developers : Get this DISCOUNTED course bundle NOW!

</details>