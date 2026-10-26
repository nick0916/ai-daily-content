---
id: inbox_e092d317
date: 2026-10-05
source_ref: "[[00-inbox/2026-10-05/0101-substack-product-growth-n8n-ceo-why-we-arent-dead-how-to-build-g-949c]]"
title: "n8n CEO: Why we aren’t dead, how to build great AI products, and what I look for in an AI PM"
url: https://www.news.aakashg.com/p/n8n-vs-claude-code
source: substack-product-growth
published_at: 2026-10-05T22:35:16+00:00
fetched_at: 2026-10-25T01:09:02.667212+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 Claude Code 快速做原型，要讓全隊共用、可審核的流程再搬到 n8n。 **Why** 每次有新 AI 工具出現就有人宣告 n8n 已死；n8n CEO 認為當流程不能只靠 95% 的成功率、必須 100% 可靠時，仍需要編排層。 **How** Claude Code 只負責「描述並生成」，n8n 補上後三步：在風險工具前加人工核准、每次執行逐節點記錄輸入輸出並可從任一點重跑、邀請同事協作並有版本歷史。文中給出問卷，2 題以上答「是」就遷移到 n8n，並提供透過 n8n MCP server 自動重建 workflow 的 prompt。 **What** Aakash Gupta 專訪 n8n 創辦人兼 CEO Jan Oberhauser。n8n 數據：200K+ GitHub stars、150 萬活躍用戶、1,200 家企業版客戶；5 月 SAP 以 52 億美元估值投資，並將 n8n 嵌入其 agent builder Joule Studio。n8n 產品團隊以 3–5 名工程師、1–2 名 PM、1 名設計師組成 squad，招募看重技術深度、builder 特質與超越 demo 的可靠性與評估能力。"
key_points:
  - "Claude Code 負責第 1 步（描述生成）；n8n 提供第 2–4 步：高風險工具人工核准、逐節點執行稽核與重跑、協作與版本管理"
  - "n8n 內部也大量使用 Claude Code：先用它做原型，再用 n8n MCP server 遷移；遷移 prompt 要求用原生節點、每個 AI Agent 節點加 fallback model、寫入類工具需人工核准、加 Slack 錯誤告警、保持未發布供審閱"
  - "n8n 數據：200K+ GitHub stars、1.5M 活躍用戶、1,200 家企業客戶；SAP 於 5 月以 $5.2B 估值投資"
tags: [n8n, claude-code, workflow-orchestration, ai-pm, human-in-the-loop]
topics: [agents.frameworks, agents.mcp, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## n8n CEO: Why we aren’t dead, how to build great AI products, and what I look for in an AI PM

用 Claude Code 快速做原型，要讓全隊共用、可審核的流程再搬到 n8n。

**Why** 每次有新 AI 工具出現就有人宣告 n8n 已死；n8n CEO 認為當流程不能只靠 95% 的成功率、必須 100% 可靠時，仍需要編排層。

**How** Claude Code 只負責「描述並生成」，n8n 補上後三步：在風險工具前加人工核准、每次執行逐節點記錄輸入輸出並可從任一點重跑、邀請同事協作並有版本歷史。文中給出問卷，2 題以上答「是」就遷移到 n8n，並提供透過 n8n MCP server 自動重建 workflow 的 prompt。

**What** Aakash Gupta 專訪 n8n 創辦人兼 CEO Jan Oberhauser。n8n 數據：200K+ GitHub stars、150 萬活躍用戶、1,200 家企業版客戶；5 月 SAP 以 52 億美元估值投資，並將 n8n 嵌入其 agent builder Joule Studio。n8n 產品團隊以 3–5 名工程師、1–2 名 PM、1 名設計師組成 squad，招募看重技術深度、builder 特質與超越 demo 的可靠性與評估能力。

### 重點
- Claude Code 負責第 1 步（描述生成）；n8n 提供第 2–4 步：高風險工具人工核准、逐節點執行稽核與重跑、協作與版本管理
- n8n 內部也大量使用 Claude Code：先用它做原型，再用 n8n MCP server 遷移；遷移 prompt 要求用原生節點、每個 AI Agent 節點加 fallback model、寫入類工具需人工核准、加 Slack 錯誤告警、保持未發布供審閱
- n8n 數據：200K+ GitHub stars、1.5M 活躍用戶、1,200 家企業客戶；SAP 於 5 月以 $5.2B 估值投資

**原文：** [substack-product-growth](https://www.news.aakashg.com/p/n8n-vs-claude-code)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Check out the conversation on Apple , Spotify , and YouTube . Brought to you by: Customer.io - Send smarter messages using your product data Kameleoon - Leading AI experimentation platform Bolt - Ship AI-powered products 10x faster Jira Product Discovery - Plan with purpose, ship with confidence Product Faculty - Get $150 off their #1 AI PM Certification via code AAKASH150 Today&#8217;s Episode On October 6, 2025, OpenAI launched its Agent Builder. By the next day, the posts were out: ChatGPT had killed n8n and Zapier. It turned out to be one of n8n&#8217;s best weeks ever. Now it&#8217;s Claude Code&#8217;s turn. Last month, this went viral: So do you still need n8n? That&#8217;s today&#8217;s episode with Jan Oberhauser , the founder and CEO of n8n. We talked about where n8n makes sense, where his own team uses Claude Code, and how to become an AI PM at n8n: Apple | Spotify | YouTube I&#8217;m giving a free webinar on the fundamentals of AI that anyone getting into PM must know. Tokenization, how LLM models work, all of it. Join me . Newsletter Version Here&#8217;s the newsletter version of our conversation: What n8n does that Claude Code can&#8217;t How to use n8n and Claude Code in tandem Roadmap to becoming the AI PM n8n would hire Subscribe now 1. What n8n does that Claude Code can&#8217;t We have been called dead probably a thousand times. I don&#8217;t remember half of the things that killed us over the years. We&#8217;re still here. &#8212;Jan Over the course of 2025, Claude Code exploded. By the holidays, it surpassed n8n in search interest and never looked back: This April, Anthropic also shipped Routines, which run Claude Code on a schedule in the cloud. Is there really any space left for n8n? I posed this question to Jan. From his point of view, things have never better . In May, SAP invested at a $5.2B valuation , more than double the valuation n8n held the prior October. It also embedded n8n into Joule Studio, its agent builder. So every SAP customer (it has millions) gets n8n in the product with no setup required. And today n8n has: 200K+ GitHub stars 1.5M active users 1,200 customers on the enterprise product So how is n8n succeeding despite Claude Code? n8n evolved its use cases. A year ago, people came to n8n for personal stuff, like an email summary. Now the growth is in business-critical workflows. So, what does n8n do for business-critical work that Claude Code can&#8217;t? Claude Code is an agentic tool that runs Anthropic&#8217;s models in your terminal. n8n is an orchestration layer that connects your tools, models, and data on a visual canvas . Jan&#8217;s AI assistant workflow generated by n8n&#8217;s AI Assistant If it&#8217;s for when you cannot rely on something working 95% of the time. You want to be 100% sure that it really works. So, you choose n8n. Jan gave us a course on how to build in it: Step 1 - Describe it Back in 2025, the viral n8n posts were all workflows. You don&#8217;t start on the canvas anymore. Jan prompted his n8n AI Assistant to create an agent for a personal project. Like a typical Claude Code experience, it asked clarifying questions and came back with the full workflow. Step 2 - Gate the risky tools Your editing really starts on the canvas now. The main thing you want to do is figure out your where to do approval. For instance, Jan asked the agent to book a meeting with his VP of Sales for 3pm the next day. He&#8217;s added human approval for meetings. So instead of book on its own, it showed him the event it was about to create and asked if it was allowed to. He clicked Add event. Then it booked. Step 3 - Audit the run Then it&#8217;s time to run and audit. The delightful thing about n8n is every execution is logged node by node, with the exact input and output at each step. So let&#8217;s say you add a deterministic node between the agent and the final output, the log will show which path it took. And you can rerun the rest of the workflow from that exact point with the same data. Step 4 - Hand-off Then this is the special part of n8n: hand-offs. How do you give something in Claude Code to someone on your team? You have to use Github, and it&#8217;s messy. In n8n, you just invite them. They see version history and who changed what. Then they can publish versions with notes. You can also export a workflow and just email it. So now you should understand the difference between Claude Code and n8n. Claude Code stops at step 1. n8n is the infrastructure to do steps 2-4. 2. How to Use Claude Code and n8n in tandem One of the. most fascinating insights from Jan was that n8n are heavy users of Claude Code themselves! So it&#8217;s worth figuring out where they use Claude Code and where they use n8n. The rule of thumb is: They very often prototype with Claude Code, because you can get something started very fast, but then they migrate it afterwards to n8n. So, to know which workflows to move, I put together this questionnaire. If you get 2 or more yeses, move it to n8n. n8n and Claude Code are very different products, and in the end you need both. Claude Routines are built for one person running tasks against their own repos. Meanwhile, n8n is built for processes a whole team shares and signs off on. You also don&#8217;t have to rebuild anything by hand when you move a workflow over! Use this prompt: Using the n8n MCP server, rebuild the workflow in this folder as an n8n workflow. - Use native n8n nodes wherever one exists. Only use a Code node when no native node fits. - Add a fallback model to every AI Agent node. - Require human approval on any tool that sends, creates, updates, or deletes. - Add an error workflow that alerts me in Slack. - Leave it unpublished so I can review the canvas before it goes live. 3. Roadmap to becoming the AI PM n8n would hire Having Jan on the podcast, I had to ask him about the AI PM job search . Here&#8217;s what I learned about how they run product and what they hire for. n8n&#8217;s product team runs in squads consisting of 3-5 engineers, 1-2 PMs, and a designer. They hire people for: Technical depth The more technical, the better, for every role. Even n8n&#8217;s designers are expected to use Claude Code. Builders Tinkerers who run home automation for fun, because they&#8217;re close to the users. Depth past the demo How an agent scales, how you evaluate it, and how you keep it reliable. This gives you a really good path. Study technical interviews , build synthetic experience , and learn AI tools . Here&#8217;s how I&#8217;d build a portfolio that passes that test: Build your first n8n workflow with Pawel Huryn&#8217;s guide . Then follow Mahesh Yadav&#8217;s learning path in How to Become a Builder PM . Prototype your next agent there, and promote it into n8n through the MCP server. Write 20 test cases and run them as an eval. As for the interview, n8n runs live sessions where you work through a problem together. Here&#8217;s my guide . And that&#8217;s it for today! Get Transcript Where to find Jan Oberhauser LinkedIn X n8n PS. Please subscribe on YouTube and follow on Apple and Spotify . It helps!

</details>