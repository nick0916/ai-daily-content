---
id: inbox_d06a9f9e
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-substack-product-growth-i-made-my-entire-podcast-available-to-yo-b128]]"
title: "I made my entire podcast available to your AI"
url: https://www.news.aakashg.com/p/pod-transcripts-github
source: substack-product-growth
published_at: 2026-11-26T00:11:53+00:00
fetched_at: 2026-11-27T00:59:03.029731+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把整個 Growth Podcast 的逐字稿公開，並做成可讓 AI 直接查詢的 MCP server。 **Why** 作者想讓使用者的 AI 能取得 166 集訪談累積的產品、AI、成長知識，而且比一般 Claude 更有針對性。 **How** 同一個問題用三種方式測試（一般 Claude、GitHub repo、MCP），發現 repo 較慢且成本較高、只能在複製的資料夾內使用，所以他加入彙整重點的 context 檔與框架搜尋，做成 MCP。 **What** 作者 Aakash 將 2024 年 8 月以來 166 集逐字稿放上 GitHub（含 46 位 CPO 與產品領導者、35 位創辦人、85 位 AI PM），並舉辦至 12 月 8 日、總值 1,200 美元的作品競賽。MCP 僅限年訂閱者；作者稱測試中 repo 方式比 MCP 慢 15%、貴 23%，MCP 在盲測品質評比得分最高。"
key_points:
  - "166 集逐字稿免費放上 GitHub；MCP server 僅限年訂閱者，在 Claude Code 以一行 prompt 即可加入"
  - "作者自測：GitHub repo 方式比 MCP 慢 15%、貴 23%，且缺少 context 檔與框架搜尋；MCP 在盲測品質評比最高"
  - "示範用途：PRD 引用具名實務者與時間戳、模擬 AI PM 面試官、查詢同類產品的技術選型"
tags: [mcp-server, podcast-transcripts, growth-podcast, claude-code, pm-tools]
topics: [agents.mcp, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## I made my entire podcast available to your AI

把整個 Growth Podcast 的逐字稿公開，並做成可讓 AI 直接查詢的 MCP server。

**Why** 作者想讓使用者的 AI 能取得 166 集訪談累積的產品、AI、成長知識，而且比一般 Claude 更有針對性。

**How** 同一個問題用三種方式測試（一般 Claude、GitHub repo、MCP），發現 repo 較慢且成本較高、只能在複製的資料夾內使用，所以他加入彙整重點的 context 檔與框架搜尋，做成 MCP。

**What** 作者 Aakash 將 2024 年 8 月以來 166 集逐字稿放上 GitHub（含 46 位 CPO 與產品領導者、35 位創辦人、85 位 AI PM），並舉辦至 12 月 8 日、總值 1,200 美元的作品競賽。MCP 僅限年訂閱者；作者稱測試中 repo 方式比 MCP 慢 15%、貴 23%，MCP 在盲測品質評比得分最高。

### 重點
- 166 集逐字稿免費放上 GitHub；MCP server 僅限年訂閱者，在 Claude Code 以一行 prompt 即可加入
- 作者自測：GitHub repo 方式比 MCP 慢 15%、貴 23%，且缺少 context 檔與框架搜尋；MCP 在盲測品質評比最高
- 示範用途：PRD 引用具名實務者與時間戳、模擬 AI PM 面試官、查詢同類產品的技術選型

**原文：** [substack-product-growth](https://www.news.aakashg.com/p/pod-transcripts-github)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

👋 Hey there, I'm Aakash. Each week, I share hands-on AI, product and career advice. For more: The Growth Podcast | AI by Aakash | Land a PM Job | Advertise . Subscribe now P.S. Get a free year of Bolt.new, Airtable, Speechify, Magic Patterns, Linear, Arize and more, plus your Growth Podcast MCP key, by becoming an annual subscriber. Learn more . I've just put every transcript of every episode of my podcast onto GitHub , for free: Check out the repo Since August 2024, I've sat down with 46 CPOs and product leaders, 35 founders and 85 AI PMs and operators. That's 166 episodes . You now have access to all of that knowledge. 🎊 Introducing my $1,200 contest From now through December 8 , if you create a product with this, post it under Discussions, in Show and tell on GitHub. I will assess every single one . The best products, I'll even write about in a future newsletter. For the top 3, I'll also be giving you: A year of paid Product Growth ($150 value) A 15-minute call with me ($250 value on Intro ) It comes to $1,200, and it's free. All you have to do is post it. Here's a few ideas to get you started: A tool workflow agent that lives on your desktop, guiding you to get more out of AI An expert database that helps brands connect with PM influencers A PM coach database that helps people find PM coaches for their situation I can't wait to see what you build! The knowledge you're getting I've been covering everything important in product management, AI and growth over the last 2 years: Here are 3 of my biggest episodes: Turning Claude into an OS with Carl Vellotti: 1.42M views ( X · YouTube ) Building a company OS with Jiaona Zhang: 537K views ( X · YouTube ) Becoming an AI PM with Jyothi Nookula: 475K views ( X · YouTube ) Today's Deep Dive So that's the free stuff. For paid subscribers, I built you even more: An optimized MCP server How to use this to get ahead 9 lessons from the podcast Get the annual plan 1. An optimized MCP server So those are all the transcripts, for free on GitHub. Then I wanted to get to the question of how do I give you the best information and resources? So I asked the same question three ways: As you can see, regular Claude never mentions that PMs now get asked to build something live in the round, which guests who hire AI PMs say decides it. It doesn't have the right context. The GitHub repo is good, but it took 15% longer, cost 23% more, and is missing the context files and the framework search. It also only works inside the folder you cloned. I realized that the best way to do this would be to build you an MCP server. Then I started testing my MCP server, and I realized the best thing to do would be to add a bunch of context files that synthesize the learnings. That way agents: Use fewer tokens Are faster Give you better quality responses The testing agreed with me. The MCP response is the fast one, the cheaper of the two, the most accurate with quotes, and the top score in a blind quality review. That's why I built it for you. Adding the MCP in Claude Code To add the MCP to your Claude Code, simply prompt like this: How to grab your key This MCP is only available for annual subscribers, because it costs me money to maintain it. If you're an annual or founding member, sign in at bundle.aakashg.com with the email on your paid subscription, claim the Growth Podcast MCP card, and copy your key. You can come back any time to see it again. Then open Claude Code and just tell it: add this MCP for all my projects: https://growth-podcast-mcp.aakashg.workers.dev/mcp key: YOUR_KEY Stuck? Here’s every step with screenshots . I'm looking forward to what you build . 2. How to use this to get ahead If you already run my PM OS , Job Search OS or Content OS , add the podcast to it. Open Claude Code in your OS folder and tell it: add the Growth Podcast MCP to this project: https://growth-podcast-mcp.aakashg.workers.dev/mcp key: YOUR_KEY. keep the key out of git, and add a line to my CLAUDE.md to search the podcast whenever a task touches a company, person or topic a guest covered Here’s a few great use cases for it in your pm job, when job searching, and on side projects. In your PM job It’s great for writing better docs like a PRD. For instance, I tried regular Claude with the prompt, "Write a PRD for [your feature] using the best practices from AI and PM practitioners" inside a PM OS: It generated a solid PRD. It reads the roadmap and plans evals up front. But it has several misses: No held-out set. Every prompt change and the launch bar run on the same 250 rows. Shreya Shankar's "number one strategy" is a test set you "never, never look at" while you build ( 00:35:15 ). No evals that fail. It rules "why did signups drop?" out of v1 and only tests that it declines. Ankur Goyal (Braintrust) keeps failing evals for "what is impossible today" and reruns them "when a new model comes out" ( 00:39:12 ). A golden set that never grows. It builds 250 rows by January, and nothing from the beta gets added. Ankur says "the best teams don't think of evals as a gate" and pull new patterns from production logs into the data set ( 00:47:48 ). No names. You asked for practitioners' best practices, and its closing list of five has no one's name on it. And here's the same ask with the podcast plugged in: So much better. It searched the podcast on its own and fixed all four. Other use cases for PMs might include: Pressure-test your doc. "Pick 5 personas from the guest transcripts and have them review my product doc as a simulated audience." Settle a team debate. "Find where guests gave opposite advice on prototyping before the spec, with one exact quote and timestamp from each." In your job search This can also be super helpful in the job search. For instance, ask it to play interviewer: Act as an AI PM interviewer at Google. Use what Satyajeet Salgar, Jaclyn Konzelmann, Diego Granados and Marily Nika said on the podcast about how Google builds and hires, then ask me your first question and tell me what a strong answer would cover. Here it is inside my Job Search OS: It asks a real product question, then tells you what a strong answer covers, with a link to the moment each guest said it. On your side project Let’s say you want to build a new side project. Now you can ask my guests about the tech stack: What's the best architecture to build an AI customer research agent? Pull what guests who built something similar chose, with timestamps. It pulled what Greg Greiner and two other guests actually built, with a timestamp on every claim. The MCP is rich context for whatever you're working on. Get your MCP key 3. 9 lessons from the podcast I've been using the MCP myself. One of the things I used it for is putting together my 9 most important lessons across the podcast. So here they are: You can read the full write-ups in the graphic. I also grabbed the juiciest clips for you to go deeper on each: When building gets cheap, choosing gets expensive Start from proven, earn the new Speed multiplies your defects The bottleneck moves to the slowest human Price on value, not tokens Don't build what the next model gives you free Context beats cleverness Fix the factory, not the widget Great evals leave room to grow I thought this was a fun way to explore the podcast, and I hope you do too. Final Words I hope this helps you upgrade your AI setup with the latest AI PM insights. Who should I have next on the podcast? Where should I take it? Let me know. Share PS. Last call for late registrations to my Land a PM Job cohort that just started. This is the last one ever. PPS. Want to advertise with The Growth Podcast? Email me at productgrowthppp@gmail.com or book through my Passionfroot page .

</details>