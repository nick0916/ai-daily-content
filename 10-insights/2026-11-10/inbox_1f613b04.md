---
id: inbox_1f613b04
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2322-latent-space-designing-for-agents-zeno-rocha-resend-9a2d]]"
title: "Designing for Agents — Zeno Rocha, Resend"
url: https://latent.space/p/resend/
source: latent-space
published_at: 2026-11-10T20:05:17+00:00
fetched_at: 2026-11-10T23:29:20.367404+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓產品對 AI 代理「看得懂、選得到」，使用者請 agent 寫程式時，它會直接挑你家的 API。 **Why** 開發者通常接受 agent 給的第一個建議，第二選擇很少被試用，所以被 agent 首選就是新的分發管道。 **How** Resend 先用 React Email 讓程式碼已在開發者專案裡；定價頁加上 .md 讓 agent 一次請求讀到表格；MCP server 擴充到 80 多個工具；並用自訂追蹤網域降低共用網域被封鎖的風險。 **What** Latent Space 專訪 Resend 共同創辦人兼 CEO Zeno Rocha。一份 AEO 研究中 Claude Code 在 102 個可擷取的 email 推薦中 64 次首選 Resend，SendGrid 首選 7 次、作為備選出現 55 次。錄製時 Resend 有 430 萬用戶、12 萬付費客戶；另有較新的研究顯示 Postmark 在多數模型中排第一。"
key_points:
  - "AEO 研究：Claude Code 在 102 個 email 推薦中 64 次首選 Resend；SendGrid 首選 7 次、備選 55 次；較新研究則是 Postmark 在多數模型領先"
  - "MCP server 從約 20 個以內的工具成長到 80 多個，對照 Cloudflare Code Mode 只用 search() 與 execute() 兩個工具；建議展開每天呼叫的結果，檢查模型實際需要多少內容"
  - "定價頁加 .md 即得 agent 可一次讀完的表格；React Email 讓 Resend 程式碼在切換服務商前就已在 repo 內"
tags: [aeo, agent-experience, resend, mcp-design, developer-tools]
topics: [agents.mcp, product_and_org.product]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Designing for Agents — Zeno Rocha, Resend

讓產品對 AI 代理「看得懂、選得到」，使用者請 agent 寫程式時，它會直接挑你家的 API。

**Why** 開發者通常接受 agent 給的第一個建議，第二選擇很少被試用，所以被 agent 首選就是新的分發管道。

**How** Resend 先用 React Email 讓程式碼已在開發者專案裡；定價頁加上 .md 讓 agent 一次請求讀到表格；MCP server 擴充到 80 多個工具；並用自訂追蹤網域降低共用網域被封鎖的風險。

**What** Latent Space 專訪 Resend 共同創辦人兼 CEO Zeno Rocha。一份 AEO 研究中 Claude Code 在 102 個可擷取的 email 推薦中 64 次首選 Resend，SendGrid 首選 7 次、作為備選出現 55 次。錄製時 Resend 有 430 萬用戶、12 萬付費客戶；另有較新的研究顯示 Postmark 在多數模型中排第一。

### 重點
- AEO 研究：Claude Code 在 102 個 email 推薦中 64 次首選 Resend；SendGrid 首選 7 次、備選 55 次；較新研究則是 Postmark 在多數模型領先
- MCP server 從約 20 個以內的工具成長到 80 多個，對照 Cloudflare Code Mode 只用 search() 與 execute() 兩個工具；建議展開每天呼叫的結果，檢查模型實際需要多少內容
- 定價頁加 .md 即得 agent 可一次讀完的表格；React Email 讓 Resend 程式碼在切換服務商前就已在 repo 內

**原文：** [latent-space](https://latent.space/p/resend/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Today’s podcast comes from a real life mystery: We are big fans of Cloudflare’s developer platform, and Cloudflare Email is a convenient tool especially when all your domains are already on Cloudflare. So why do agents keep suggesting we use Resend despite having an existing “home bias” and much larger incumbent player? Well, we got the guy who “does AEO for resend” - the CEO of AEO, Zeno Rocha, who has been writing about AEO since 2024 and Agent Experience since Feb 2025 , on the pod today: In a recent AEO study, Claude Code picked Resend first in 64 of the 102 email recommendations the researchers could extract. SendGrid came first seven times, yet showed up 55 times as an alternative. If the developer asks an agent to implement email and accepts the patch, how often does anyone get around to trying the second choice? The study breaks down the results by model and app. Our more recent comprehensive AEO study was a bit more competitive, with Postmark coming up top for most models. Zeno Rocha, Resend’s co-founder and CEO, joined us to walk through what happens on both sides of that pull request. He says Resend had 4.3 million users and 120,000 paying customers when we recorded. He discovered one of them, Warner Bros. Discovery, by sorting through short .com domains in the customer database on a Saturday. The developer gets there before the model Resend’s first useful bit of distribution was an email template. While Zeno and his team were building the sending API, developers kept telling them how painful it was to get the email itself to look right. So they released React Email. You could build a template with it and send it through SendGrid. They even documented how. By the time a developer needed a different provider, some of Resend’s code was already in the repo. React Email Now try the same journey as an agent comparing providers. Resend’s pricing page has a slider. A person can drag it to the right volume and read off the price. Add .md to the URL and the agent gets a table it can read in one request. That’s the kind of change I liked in our Supabase interview too. You can ask whether a model has heard of your product. You can also open your own pricing table and see whether it can answer a customer’s question. 80 tools, or two? When we recorded, Resend’s MCP server had grown from roughly 20 tools or fewer at launch to more than 80. Zeno wants someone working in a chat client to be able to do what they can do in the dashboard. Sending an email gets the demo working. Inviting a teammate, checking usage and managing billing account for some of the long tail. The design looks especially interesting alongside Cloudflare’s Code Mode server , which exposes its API through two tools, search() and execute() . Zeno describes opening the collapsed tool calls in his own sessions to see what the agent actually did. In one, the result was too large to fit in context. Reducing the tool count wouldn’t by itself make that response any smaller. For someone designing an MCP server, that’s a cheap experiment worth borrowing: expand the result of a call you make every day and see how much of it the model actually needs. What happens after “send”? Getting an agent to pick the SDK still leaves the entire business of delivering the mail. Take click tracking. A provider can rewrite links through a shared tracking domain so it can count clicks. If one customer uses that domain for phishing and it gets blocklisted, links in another customer’s perfectly legitimate emails can suffer too. Zeno explains why Resend introduced custom tracking domains and why he wants to keep the free tier even though spammers can sign up for it. Custom tracking domains · Resend’s $3M safety commitment Watch the domain setup and pricing walkthroughs if you build developer tools. Stay for the last stretch if you know Zeno from Dracula. We get into what it’s like to build a company with a family and how much of a founder’s job comes down to finding a name that other people actually use. Show notes Zeno’s original Dracula announcement — the editor theme he launched in 2013. Zeno on what Claude Code chooses — his reading of the recommendation study and the differences between model versions. Resend’s MCP server — the integration behind the tool-count discussion. Anthropic on writing tools for agents — concrete approaches to returning less data when a tool result fills the context window. Resend’s anti-abuse handbook — what happens when a new sender signs up and where the team intervenes. Chapters 0:00 Cold open 0:59 From Dracula to email 5:02 When agents pick the API 6:54 Getting into the inbox 13:28 What tracking measures 17:05 Paying for trust 19:44 The DNS hurdle 23:55 React Email’s wedge 27:01 Measuring adoption 31:58 Owning the mail stack 37:55 Designing the MCP 46:29 CLI, SDKs and craft 52:41 Mail for agents 58:28 Writing for machines 1:06:00 Winning recommendations 1:12:14 Enterprise and pricing 1:16:51 Building with a family 1:23:26 Naming a category Resend - Zeno Rocha - Transcript.txt 94.65 KB • PLAIN File

</details>