---
id: inbox_c0dc40e1
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2252-github-trending-agent-tools-mattpocock-skills-307-425-889-e0c5]]"
title: "mattpocock/skills ⭐ 307,425(今日 +889)"
url: https://github.com/mattpocock/skills
source: github-trending-agent-tools
published_at: 2026-10-30T22:52:43.221412+00:00
fetched_at: 2026-10-30T22:59:48.515926+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "mattpocock/skills 是一組給 Claude Code、Codex 等 coding agent 使用的工程技能，用來解決需求錯位與程式碼失控。 **Why** 原文列出四種常見失敗：agent 不照需求做、回答過於冗長、程式跑不起來、程式碼變成一團爛泥。 **How** 用 /grill-with-docs 先透過追問對齊需求並建立共享術語表 CONTEXT.md，用 /tdd 做紅綠重構，用 /improve-codebase-architecture 審視架構。 **What** GitHub 今日星數 307,425（今日 +889），可透過 plugin 自動更新，或用 npx skills 安裝，每個 repo 執行一次 /setup-matt-pocock-skills。"
key_points:
  - "共享術語表 CONTEXT.md 讓 agent 用一個詞取代冗長描述，原文稱此做法在後續每次 session 都有效"
  - "/tdd 要求 agent 先寫失敗測試再修正，/diagnosing-bugs 將除錯拆成分階段的流程"
  - "/improve-codebase-architecture 建議每幾天執行一次，用來找出可加深的模組，但原文說明它不會替舊專案解開爛泥"
tags: [agent-skills, claude-code, tdd, shared-glossary, feedback-loop]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 2
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## mattpocock/skills ⭐ 307,425(今日 +889)

mattpocock/skills 是一組給 Claude Code、Codex 等 coding agent 使用的工程技能，用來解決需求錯位與程式碼失控。

**Why** 原文列出四種常見失敗：agent 不照需求做、回答過於冗長、程式跑不起來、程式碼變成一團爛泥。

**How** 用 /grill-with-docs 先透過追問對齊需求並建立共享術語表 CONTEXT.md，用 /tdd 做紅綠重構，用 /improve-codebase-architecture 審視架構。

**What** GitHub 今日星數 307,425（今日 +889），可透過 plugin 自動更新，或用 npx skills 安裝，每個 repo 執行一次 /setup-matt-pocock-skills。

### 重點
- 共享術語表 CONTEXT.md 讓 agent 用一個詞取代冗長描述，原文稱此做法在後續每次 session 都有效
- /tdd 要求 agent 先寫失敗測試再修正，/diagnosing-bugs 將除錯拆成分階段的流程
- /improve-codebase-architecture 建議每幾天執行一次，用來找出可加深的模組，但原文說明它不會替舊專案解開爛泥

**原文：** [github-trending-agent-tools](https://github.com/mattpocock/skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Skills for Real Engineers. Straight from my .agents directory.

Skills For Real Engineers

Installation (30-second setup)

Why These Skills Exist

Reference

1. Get the skills

2. Run /setup-matt-pocock-skills

3. Bam - you're ready to go.

#1: The Agent Didn't Do What I Want

#2: The Agent Is Way Too Verbose

#3: The Code Doesn't Work

#4: We Built A Ball Of Mud

Summary

Engineering

Productivity

 

My agent skills that I use every day to do real engineering - not vibe coding.

Developing real applications is hard. Approaches like GSD, BMAD, and Spec-Kit try to help by owning the process. But while doing so, they take away your control and make bugs in the process hard to resolve.

These skills are designed to be small, easy to adapt, and composable. They work with any model. They're based on decades of engineering experience. Hack around with them. Make them your own. Enjoy.

If you want to keep up with changes to these skills, and any new ones I create, you can join ~60,000 other devs on my newsletter:

Sign Up To The Newsletter

A plugin updates itself. skills.sh copies editable files into your project, and you update them by hand. Pick one per agent, because installing both gives you every skill twice.

Updates itself by default.

Updates itself at startup.

Then, once, add to ~/.copilot/settings.json :

In VS Code, run Chat: Install Plugin From Source and enter https://github.com/mattpocock/skills . It updates daily.

Re-run both commands to update.

When the installer asks which skills to take, include setup-matt-pocock-skills . To update, run npx skills@latest update , and re-run add to pick up new skills.

In your agent, run it once per repo. It will:

I built these skills as a way to fix common failure modes I see with Claude Code, Codex, and other coding agents.

"No-one knows exactly what they want"

David Thomas & Andrew Hunt, The Pragmatic Programmer

The Problem . The most common failure mode in software development is misalignment. You think the dev knows what you want. Then you see what they've built - and you realize it didn't understand you at all.

This is just the same in the AI age. There is a communication gap between you and the agent. The fix for this is a grilling session - getting the agent to ask you detailed questions about what you're building.

The Fix is to use:

These are my most popular skills. They help you align with the agent before you get started, and think deeply about the change you're making. Use them every time you want to make a change.

With a ubiquitous language, conversations among developers and expressions of the code are all derived from the same domain model.

Eric Evans, Domain-Driven-Design

The Problem : At the start of a project, devs and the people they're building the software for (the domain experts) are usually speaking different languages.

I felt the same tension with my agents. Agents are usually dropped into a project and asked to figure out the jargon as they go. So they use 20 words where 1 will do.

The Fix for this is a shared language. It's a document that helps agents decode the jargon used in the project.

Here's an example glossary (still named CONTEXT.md at that pinned commit, from before the skills renamed the convention), from my course-video-manager repo. Which one is easier to read?

This concision pays off session after session.

This is built into /grill-with-docs . It's a grilling session, but that helps you build a shared language with the AI, and document hard-to-explain decisions in ADR's.

It's hard to explain how powerful this is. It might be the single coolest technique in this repo. Try it, and see.

Tip

A shared language has many other benefits than reducing verbosity:

"Always take small, deliberate steps. The rate of feedback is your speed limit. Never take on a task that’s too big."

David Thomas & Andrew Hunt, The Pragmatic Programmer

The Problem : Let's say that you and the agent are aligned on what to build. What happens when the agent still produces crap?

It's time to look at your feedback loops. Without feedback on how the code it produces actually runs, the agent will be flying blind.

The Fix : You need the usual tranche of feedback loops: static types, browser access, and automated tests.

For automated tests, a red-green-refactor loop is critical. This is where the agent writes a failing test first, then fixes the test. This helps give the agent a consistent level of feedback that results in far better code.

I've built a /tdd skill you can slot into any project. It encourages red-green-refactor and gives the agent plenty of guidance on what makes good and bad tests.

For debugging, I've also built a /diagnosing-bugs skill that wraps best debugging practices into a disciplined loop, gated phase by phase.

"Invest in the design of the system every day ."

Kent Beck, Extreme Programming Explained

"The best modules are deep. They allow a lot of functionality to be accessed through a simple interface."

John Ousterhout, A Philosophy Of Software Design

The Problem : Most apps built with agents are complex and hard to change. Because agents can radically speed up coding, they also accelerate software entropy. Codebases get more complex at an unprecedented rate.

The Fix for this is a radical new approach to AI-powered development: caring about the design of the code.

This is built in to every layer of these skills:

And crucially, /improve-codebase-architecture surveys a codebase for deepening opportunities and hands you the candidates. I recommend running it on your codebase once every few days. It is a survey, not a rescue: on a genuinely old codebase it will find real candidates, but it won't untangle the mud for you.

Software engineering fundamentals matter more than ever. These skills are my best effort at condensing these fundamentals into repeatable practices, to help you ship the best apps of your career. Enjoy.

These split on one axis: who can invoke them. User-invoked skills are reachable only when you type them (e.g. /grill-me ); th

</details>