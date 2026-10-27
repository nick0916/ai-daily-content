---
id: inbox_72993fae
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-substack-dev-leader-mongodb-in-c-claude-code-and-engineering-f17c]]"
title: "MongoDB in C#, Claude Code, and Engineering Leadership"
url: https://devleader.substack.com/p/mongodb-in-c-claude-code-and-engineering
source: substack-dev-leader
published_at: 2026-10-26T04:58:40+00:00
fetched_at: 2026-10-27T01:32:06.467332+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dev Leader 的每週文章與影片彙整，主題是 .NET、Claude Code 與工程管理。 **What** 本週內容包含 MongoClient 在 ASP.NET Core 的生命週期與 singleton 重用、C# 集合的存取／可變性／所有權契約、MongoDB 在 C# 的型別化映射，以及為 .NET repo 提供 Claude Code 脈絡（instruction loading、scoped rules）與 csharp-lsp plugin 的設定與限制。管理類主題有帶初階工程師、處理競爭優先順序、與主管的 one-on-one；影片討論 AI 產生程式碼的品質歸屬與人類退回 AI PR 的流程。內容為連結清單，僅有標題與簡述。"
key_points:
  - "Claude Code 的 .NET 相關文章涵蓋 csharp-lsp plugin、repo 脈絡、scoped rules 與明確的驗證邊界"
  - "MongoDB 文章重點為 MongoClient 在 ASP.NET Core 以 singleton 重用與資源所有權"
  - "影片討論 AI 寫的程式碼仍由人負責品質，以及人類審查退回 AI pull request 的流程"
tags: [dotnet, claude-code, mongodb, csharp, engineering-management]
topics: [agents.coding_agents, product_and_org.leadership]
importance: 1
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## MongoDB in C#, Claude Code, and Engineering Leadership

Dev Leader 的每週文章與影片彙整，主題是 .NET、Claude Code 與工程管理。

**What** 本週內容包含 MongoClient 在 ASP.NET Core 的生命週期與 singleton 重用、C# 集合的存取／可變性／所有權契約、MongoDB 在 C# 的型別化映射，以及為 .NET repo 提供 Claude Code 脈絡（instruction loading、scoped rules）與 csharp-lsp plugin 的設定與限制。管理類主題有帶初階工程師、處理競爭優先順序、與主管的 one-on-one；影片討論 AI 產生程式碼的品質歸屬與人類退回 AI PR 的流程。內容為連結清單，僅有標題與簡述。

### 重點
- Claude Code 的 .NET 相關文章涵蓋 csharp-lsp plugin、repo 脈絡、scoped rules 與明確的驗證邊界
- MongoDB 文章重點為 MongoClient 在 ASP.NET Core 以 singleton 重用與資源所有權
- 影片討論 AI 寫的程式碼仍由人負責品質，以及人類審查退回 AI pull request 的流程

**原文：** [substack-dev-leader](https://devleader.substack.com/p/mongodb-in-c-claude-code-and-engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This week: We’re looking at MongoDB client lifetimes, C# collection contracts, and giving Claude Code useful context for .NET work. There’s practical reading on mentoring junior developers, handling competing priorities, and having clearer conversations with your manager. The videos tackle ownership of AI-generated code, human review of AI pull requests, and retiring products and services. Like what you read or watched from the recap? I’d love if you helped share on Reddit or Daily.dev so others can see! Weekly Recap How Do Developers Deprecate Products and Services? From the ExperiencedDevs subreddit, this developer wanted perspectives on how others deprecate products and services. This Bot Submitted A Question On AI Reviews Rejected By Humans A bot submitted a question to the channel on what processes are followed when humans are rejecting AI pull requests. AI Writes The Code. You Still Own The Quality - Principal Engineering Manager AMA How long do we really think it’s going to last when we can blame the agent for the bug that got into production? Did you sign off on that PR? Or maybe you even had another one of your agents do it... As with all livestreams, I’m looking forward to answering YOUR questions! So join me live and ask in the chat, or you can comment now, and I can try to get it answered while I stream. MongoClient in ASP.NET Core: Lifetime and Resource Ownership Learn MongoClient in ASP.NET Core with explicit configuration, singleton reuse, borrowed collection handles, and version-aware resource ownership at shutdown. Helping a Mentee Choose a Development Focus Help a mentee choose a development focus by exploring interests, everyday friction, and useful opportunities without forcing a goal or a larger career plan. Sharing Information Without Overloading Engineers Share information without overwhelming engineers: make context accessible, explain changes, and distinguish useful transparency from repeated interruption. How to Raise a Difficult Issue in a One-on-One Navigate difficult conversations with your manager: explain the impact, clarify the support you need, and agree on next steps without having every answer. Make a Bounded ASP.NET Core Change with Claude Code Explore a bounded ASP.NET Core change with Claude Code: trace an endpoint, define input rules, preserve existing contracts, and review meaningful evidence. How to Help Junior Developers Without Doing Their Work Help junior developers through the problem in front of them by listening, clarifying expectations, and choosing guidance that keeps them actively involved. Collections in C#: Access, Mutation, and Ownership Explained Understand collections in C# through access, ordering, equality, mutation, and ownership contracts, with practical examples for everyday application code. Handling Competing Priorities as an Engineering Manager Understand competing priorities as an engineering manager: clarify requests, account for capacity, name displaced commitments, and escalate choices clearly. C# Code Intelligence in Claude Code: Setup and Limits Understand C# code intelligence in Claude Code, including the csharp-lsp plugin, server prerequisites, diagnostics, symbol navigation, and verification limits. Career Conversations With Your Manager: Start With Your Own Goals Make career conversations with your manager clearer by exploring your interests, desired responsibilities, role expectations, and opportunities as goals change. Managing Your Time as a New Engineering Manager Learn to manage your time as an engineering manager, balance support and coordination, handle interruptions, and recognize when your workload needs to change. Give Claude Code the Right Context for Your .NET Repository Give Claude Code useful .NET repository context with solution facts, instruction loading, scoped rules, package conventions, and explicit validation boundaries. Test Vercel Eve Integrations in C#: Compatibility and Failure Recovery Vercel Eve testing in C# separates adapter checks from real protocol tests, covering compatible versions, repeated turns, disconnects, and failure recovery. MongoDB in C#: Connecting, Mapping, and Reading Documents Understand MongoDB in C# through client ownership, typed BSON mapping, bounded reads, write boundaries, and index evidence without duplicating CRUD tutorials. Join me and other software engineers in the private Discord community ! Resume reviews and interview guidance ! Software engineering podcast and livestreams ! My Code Commute vlogs are on YouTube ! All of my weekly vlogs are on YouTube ! Remember to check out my courses , including this awesome discounted bundle for C# developers : Get this DISCOUNTED course bundle NOW!

</details>