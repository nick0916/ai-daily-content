---
id: inbox_22d5cf03
date: 2026-10-19
source_ref: "[[00-inbox/2026-10-19/0101-substack-dev-leader-claude-code-ai-agents-and-engineering-le-715a]]"
title: "Claude Code, AI Agents, and Engineering Leadership"
url: https://devleader.substack.com/p/claude-code-ai-agents-and-engineering
source: substack-dev-leader
published_at: 2026-10-19T01:44:31+00:00
fetched_at: 2026-10-25T01:08:31.869276+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dev Leader 週報，彙整 Claude Code 在 .NET 的工作流程、Vercel Eve 的 C# 整合，以及工程管理與職涯文章與影片。 **What** 本期涵蓋 Windows 上為 .NET solution 設定 Claude Code、提供 repository 正確 context（solution 資訊、scoped rules、套件慣例、明確的驗證邊界）、可供審查的 repository 工作流程；Vercel Eve 的 ASP.NET Core 驗證、human-in-the-loop 核准與恢復、C# 整合測試；另有轉任工程經理、一對一會議、mentoring 等文章，以及 AI 程式碼品質、程式語言是否仍重要、晉升 senior/staff 的影片。"
key_points:
  - "Claude Code 與 .NET：Windows 設定（native 與 WSL）、提供 repo context（solution 資訊、scoped rules、套件慣例、明確驗證邊界）、搭配權限與人工審查"
  - "Vercel Eve C# 系列：ASP.NET Core 驗證（服務憑證與使用者授權分離）、human-in-the-loop 核准與恢復、相容性與失敗恢復測試"
  - "管理主題：轉任工程經理、一對一會議、mentoring、加入新團隊先學再改"
tags: [claude-code, dotnet, vercel-eve, engineering-management, weekly-recap]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code, AI Agents, and Engineering Leadership

Dev Leader 週報，彙整 Claude Code 在 .NET 的工作流程、Vercel Eve 的 C# 整合，以及工程管理與職涯文章與影片。 **What** 本期涵蓋 Windows 上為 .NET solution 設定 Claude Code、提供 repository 正確 context（solution 資訊、scoped rules、套件慣例、明確的驗證邊界）、可供審查的 repository 工作流程；Vercel Eve 的 ASP.NET Core 驗證、human-in-the-loop 核准與恢復、C# 整合測試；另有轉任工程經理、一對一會議、mentoring 等文章，以及 AI 程式碼品質、程式語言是否仍重要、晉升 senior/staff 的影片。

### 重點
- Claude Code 與 .NET：Windows 設定（native 與 WSL）、提供 repo context（solution 資訊、scoped rules、套件慣例、明確驗證邊界）、搭配權限與人工審查
- Vercel Eve C# 系列：ASP.NET Core 驗證（服務憑證與使用者授權分離）、human-in-the-loop 核准與恢復、相容性與失敗恢復測試
- 管理主題：轉任工程經理、一對一會議、mentoring、加入新團隊先學再改

**原文：** [substack-dev-leader](https://devleader.substack.com/p/claude-code-ai-agents-and-engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This week: We&#8217;re covering Claude Code workflows for .NET, from Windows setup to giving your repository the right context, plus Vercel Eve authentication, human approval, and integration testing in C#. There&#8217;s practical reading on becoming an engineering manager, mentoring engineers, and making one-on-ones useful. The videos tackle AI code quality, whether programming languages still matter, growing toward senior and staff roles, and getting support from other teams. Like what you read or watched from the recap? I&#8217;d love if you helped share on Reddit or Daily.dev so others can see! Weekly Recap Raising Visibility To Other Teams And Getting Their Support In this video, I talk about an approach to getting support from another team by raising visibility. This Is The Project In My Career That I Am MOST Proud Of From the ExperiencedDevs subreddit, this developer wanted to hear about the projects that people are most proud of in their careers. Do Programming Languages Still Matter After AI? - Principal Engineering Manager AMA Now that AI writes all the code and we&#8217;ve all been replaced, does the programming language that gets used even matter? I mean, who&#8217;s even reviewing these PRs, anyway?! As with all livestreams, I&#8217;m looking forward to answering YOUR questions! So join me live and ask in the chat, or you can comment now, and I can try to get it answered while I stream. What Is The Most Effective Way To Get To Senior, Staff, and Beyond? From the ExperiencedDevs subreddit, this developer wanted perspectives on the best ways to get to senior, staff, and levels beyond. How Do We Maintain A High Quality Bar With AI Development? From the ExperiencedDevs subreddit, this developer wanted to understand how to maintain a high bar for quality when building with AI. Give Claude Code the Right Context for Your .NET Repository Give Claude Code useful .NET repository context with solution facts, instruction loading, scoped rules, package conventions, and explicit validation boundaries. Test Vercel Eve Integrations in C#: Compatibility and Failure Recovery Vercel Eve testing in C# separates adapter checks from real protocol tests, covering compatible versions, repeated turns, disconnects, and failure recovery. Feeling Unproductive as an Engineering Manager: Understanding Your Impact Feeling unproductive as an engineering manager? Understand your impact when you code less, support others, and help the team work without depending on you. How to Get Useful Feedback in a One-on-One Get useful feedback in a one-on-one by examining specific work, understanding your manager&#8217;s observations, and agreeing on next steps without guesswork. Set Up Claude Code for a .NET Solution on Windows Set up Claude Code for a .NET solution on Windows, understand native and WSL environments, check SDK visibility, and separate terminal use from IDE support. Mentoring and Coaching Software Engineers: Building Capability Mentoring helps software engineers reason, learn, and become more capable. Explore useful support without taking over their work or imposing your ambitions. Starting With a New Engineering Team: Learn Before You Change Things Joining a new engineering team? Learn its responsibilities, priorities, and working practices before choosing bounded changes with the people doing the work. Human-in-the-Loop AI Agents in C#: Approval and Resume with Vercel Eve Learn human-in-the-loop AI agents in C#: authenticate human decisions, select the correct pending input, and resume Vercel Eve with authoritative resolutions. One-on-Ones With Quiet Employees: Make Space Without Forcing Conversation Support quiet employees in one-on-ones with thoughtful preparation, room to respond, useful feedback, and respect for individual goals and personal boundaries. Claude Code for .NET Developers: A Reviewable Repository Workflow Learn how Claude Code fits a .NET repository workflow, from solution context and bounded changes to permissions, meaningful verification, and human review. From Software Engineer to Engineering Manager: Starting Well Starting as an engineering manager means changing how you contribute. Understand expectations, support your team, and avoid becoming its permanent bottleneck. Authenticate Vercel Eve Calls from ASP.NET Core: Service Access and User Authorization Understand Vercel Eve authentication from ASP.NET Core: separate user authorization, service credentials, route access, reconnects, and safe redirect policies. When One-on-Ones Become Nothing but Status Updates When one-on-one status updates take over every meeting, restore room for support, feedback, and goals without banning useful conversations about the work. Join me and other software engineers in the private Discord community ! Resume reviews and interview guidance ! Software engineering podcast and livestreams ! My Code Commute vlogs are on YouTube ! All of my weekly vlogs are on YouTube ! Remember to check out my courses , including this awesome discounted bundle for C# developers : Get this DISCOUNTED course bundle NOW!

</details>