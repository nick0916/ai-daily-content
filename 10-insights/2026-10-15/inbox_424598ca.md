---
id: inbox_424598ca
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0250-creator-economy-is-software-dead-or-just-not-for-humans-5a6a]]"
title: "Is Software Dead, or Just Not for Humans Anymore?"
url: https://creatoreconomy.so/p/is-software-dead-or-just-not-for-humans-anymore
source: creator-economy
published_at: 2026-10-15T16:55:07+00:00
fetched_at: 2026-10-26T03:00:20.646334+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "傳統軟體的價值正被 AI 侵蝕，金流正轉向為 agent 優先設計的軟體。 **Why** 昂貴軟體被 AI 複製與開源，引發「軟體已死」的爭論。 **How** 原文列出四個理由：AI 可逆向工程應用、個人 app 取代部分 SaaS、企業內部工具取代 SaaS、agent 取代人類成為主要使用者。 **What** Retool 調查指出 35% 企業以內部 app 取代 SaaS；Ramp 的內部 coding agent Inspect 寫了 75% 已合併 PR；Curative 取消了 $600K/年的 Salesforce 合約。"
key_points:
  - "Retool 調查：35% 企業已用內部 app 取代 SaaS 工具"
  - "Ramp 內部 coding agent Inspect 寫了 75% 已合併 PR；Curative 取消 $600K/年 Salesforce 合約改建內部 CRM"
  - "沒有 API 或 MCP 的軟體，作者表示其代理可能就不會使用；團隊用 Opus 重建七款 Adobe 應用"
tags: [software-is-dead, saas, agent-first-software, internal-apps, reverse-engineering]
topics: [agents.mcp, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Is Software Dead, or Just Not for Humans Anymore?

傳統軟體的價值正被 AI 侵蝕，金流正轉向為 agent 優先設計的軟體。

**Why** 昂貴軟體被 AI 複製與開源，引發「軟體已死」的爭論。

**How** 原文列出四個理由：AI 可逆向工程應用、個人 app 取代部分 SaaS、企業內部工具取代 SaaS、agent 取代人類成為主要使用者。

**What** Retool 調查指出 35% 企業以內部 app 取代 SaaS；Ramp 的內部 coding agent Inspect 寫了 75% 已合併 PR；Curative 取消了 $600K/年的 Salesforce 合約。

### 重點
- Retool 調查：35% 企業已用內部 app 取代 SaaS 工具
- Ramp 內部 coding agent Inspect 寫了 75% 已合併 PR；Curative 取消 $600K/年 Salesforce 合約改建內部 CRM
- 沒有 API 或 MCP 的軟體，作者表示其代理可能就不會使用；團隊用 Opus 重建七款 Adobe 應用

**原文：** [creator-economy](https://creatoreconomy.so/p/is-software-dead-or-just-not-for-humans-anymore)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Upgrade to paid to unlock my personal AI course with 25+ lessons, 17 AI skills, $600+ in AI tool credits, my private Slack community, and monthly live workshops. Get instant access Dear subscribers, It&#8217;s easier than ever to build software, but harder than ever to make money from it. When I left my job, I thought I&#8217;d vibe code a SaaS that made money from users while I slept. Instead, I built open source tools like No AI Slop and Human Review for agents. Now, many builders are saying that &#8220;Software is dead.&#8221; ( Pieter Levels ) and &#8220;Pretty soon all software will be de facto open-source.&#8221; ( Amjad , CEO Replit). So what the hell is going on? In this post, I&#8217;ll steelman both sides and give you my take on why I think: It&#8217;s harder to make money from traditional software. Money is shifting to software that&#8217;s built for agents first. I&#8217;m proud to partner with Riverside Riverside&#8217;s new MCP lets me prep episodes, edit recordings, create clips, and schedule posts to multiple video platforms, all from ChatGPT and Claude. You can also use it to host webinars, create brand videos, and much more. Try Riverside for 1 Month Free Why the &#8220;software is dead&#8221; debate is raging again Here&#8217;s what set off the &#8220;software is dead&#8221; debate again: Expensive software is being cloned and open sourced. A small team used Opus to rebuild seven Adobe apps, including PhotoCraft , a Photoshop clone that hit 45K+ GitHub stars. The same team is now cloning Word, Excel, and PowerPoint . Classic games are being decompiled and remixed. Modders are using AI to mash together classic games like Mario in Halo and a free browser version of Super Smash Bros 64 that has 1,000+ characters. These developments have led people like Naval to tweet that &#8220;models are the last moat in software,&#8221; and Chamath to say that software IP has been &#8220;rendered worthless.&#8221; Let&#8217;s explore the argument from both sides: 4 reasons why traditional software is in trouble 1. AI can now reverse engineer many apps and games If you can download it, AI can decompile it. REA , a toolkit built specifically to reverse engineer any software, is currently the #1 trending repo on GitHub, and people are decompiling all kinds of things with it. For example, here are some classic games that you can now play for free on your browser thanks to AI (at least until the lawyers get involved): Unreal Tournament Call of Duty Black Ops Zombies Diablo 2. Builders are replacing SaaS with personal apps Let&#8217;s face it, many traditional SaaS apps have become incredibly bloated. For example, I was paying $200 / year for 1of10 , a YouTube research tool. The product kept adding features I didn&#8217;t need, so I asked Claude to build a replacement. It took just 5 minutes to build the feature that I actually wanted: a Chrome extension that showed me which videos performed well on any YouTube channel. A snapshot of the extension that Claude built You don&#8217;t have to rebuild an entire SaaS with AI, just the 20% that matters. Many SaaS apps have fallen into the trap of catering only to power users and adding features that most people won&#8217;t use. This happened to Adobe and I&#8217;d argue it&#8217;s happening to ChatGPT too. As another example, instead of paying a monthly subscription for a bloated fitness app, I just built my own with AI: I can add or remove features to this app whenever I want. It&#8217;s personalized just for me, so I&#8217;ll probably never pay for another fitness app again. The counter-argument here is that most people won&#8217;t want to build their own software even with AI&#8217;s help. But I believe that building with agents won&#8217;t feel like coding at all. Instead, building will happen naturally in your chats with AI. For example, you might ask Claude what to cook tonight and it&#8217;ll build you a meal planner with recipes for the whole week. 3. Enterprises are replacing SaaS with internal apps The personal app trend isn&#8217;t limited to individuals. Enterprises are also replacing SaaS with their own internal tools and agents. For example: Retool found that 35% of enterprises have replaced SaaS tools with internal apps. Ramp built its own coding agent, Inspect , which now writes 75% of merged PRs . Curative canceled a $600K/year Salesforce contract after building an internal CRM. In enterprise, the biggest competitors to your SaaS might just be internal apps from your customers themselves. 4. Agents are replacing humans as software&#8217;s main users If your product is still charging a subscription for humans to click through screens without proper API or MCP support, you&#8217;re probably in trouble. For example, I&#8217;ve been using Blender to make beautiful 3D assets like this video of Himeji Castle during cherry blossoms. But I have no idea how to use Blender&#8217;s UI: Instead, I rely entirely on Claude to use it through Blender MCP. As I wrote before , if a piece of software doesn&#8217;t have an API or MCP that my agent can use, I probably just won&#8217;t use it period. That&#8217;s why I think a good chunk of traditional SaaS won&#8217;t make it to the agentic era. Ok so to recap, I believe that it&#8217;s harder than ever to make money from traditional software because: AI can now reverse engineer many apps and games Builders are replacing SaaS with personal apps Enterprises are replacing SaaS with internal apps Agents are replacing humans as software&#8217;s main users Thankfully, none of this means that &#8220;software is dead.&#8221; Here&#8217;s where I think the money is moving to in software instead: 
 
 
 Read more

</details>