---
id: inbox_a80b4b43
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-substack-product-growth-how-to-build-an-ai-customer-research-age-301b]]"
title: "How to Build an AI Customer Research Agent in Claude Code"
url: https://www.news.aakashg.com/p/ai-customer-research
source: substack-product-growth
published_at: 2026-11-13T23:56:59+00:00
fetched_at: 2026-11-14T01:52:08.203649+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 AI 主動寫信給每一位流失的客戶並問一個問題，把客戶訪談規模從每月個位數放大到全部。 **Why** 流失客戶早已離開 app，應用內問卷抓不到他們；Greg Greiner 在 Bolt 擔任 CPO 時每月只能訪談 7～8 位客戶。 **How** 在 Claude Code 提供四樣東西：流失用戶 email 的 CSV、規範對話與信件格式的 CLAUDE.md、agent 可做與不可做的政策、寄信 skill（用 Gmail MCP）；信件用純文字、一次只問一個問題；另加 eval 步驟，檢查回覆是否有文件依據，失敗就重跑整個生成並存成草稿待審。 **What** Woven CEO Greg Greiner 約 30–40 分鐘就在 Claude Code 做出可運作版本，專案已放 GitHub。Ancestry.com 案例中 3,470 人回信：42.1% 提到隱私與意外 DNA 發現、38.6% 提到送禮與自用時機、31.2% 提到訂閱與隱藏費用；提出運送時效的人 41% 最終購買，等促銷者 28%，被訂閱搞混者 20%。email 回覆率約 20–40%，量大時建議從 Gmail 換成 Postmark 這類寄送服務。"
key_points:
  - "6 個接觸時機：註冊未完成、試用期間、試用結束未購買、新增購功能未轉換、近幾週使用量下降、已取消；信件用純文字、只問一件事"
  - "Eval 技巧：不要把 eval 的評語當精確指令交給 agent（會過擬合），而是把失敗結果當成一個額外輸入重跑完整生成；email 非即時，使 eval 失敗重跑不會被客戶察覺"
  - "Ancestry 案例：3,470 人回覆，運送時效問題的客戶 41% 購買，對比等促銷 28%、訂閱困惑 20%"
tags: [customer-research, claude-code, gmail-mcp, llm-judge, churn]
topics: [agents.coding_agents, engineering.evals, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Build an AI Customer Research Agent in Claude Code

用 AI 主動寫信給每一位流失的客戶並問一個問題，把客戶訪談規模從每月個位數放大到全部。

**Why** 流失客戶早已離開 app，應用內問卷抓不到他們；Greg Greiner 在 Bolt 擔任 CPO 時每月只能訪談 7～8 位客戶。

**How** 在 Claude Code 提供四樣東西：流失用戶 email 的 CSV、規範對話與信件格式的 CLAUDE.md、agent 可做與不可做的政策、寄信 skill（用 Gmail MCP）；信件用純文字、一次只問一個問題；另加 eval 步驟，檢查回覆是否有文件依據，失敗就重跑整個生成並存成草稿待審。

**What** Woven CEO Greg Greiner 約 30–40 分鐘就在 Claude Code 做出可運作版本，專案已放 GitHub。Ancestry.com 案例中 3,470 人回信：42.1% 提到隱私與意外 DNA 發現、38.6% 提到送禮與自用時機、31.2% 提到訂閱與隱藏費用；提出運送時效的人 41% 最終購買，等促銷者 28%，被訂閱搞混者 20%。email 回覆率約 20–40%，量大時建議從 Gmail 換成 Postmark 這類寄送服務。

### 重點
- 6 個接觸時機：註冊未完成、試用期間、試用結束未購買、新增購功能未轉換、近幾週使用量下降、已取消；信件用純文字、只問一件事
- Eval 技巧：不要把 eval 的評語當精確指令交給 agent（會過擬合），而是把失敗結果當成一個額外輸入重跑完整生成；email 非即時，使 eval 失敗重跑不會被客戶察覺
- Ancestry 案例：3,470 人回覆，運送時效問題的客戶 41% 購買，對比等促銷 28%、訂閱困惑 20%

**原文：** [substack-product-growth](https://www.news.aakashg.com/p/ai-customer-research)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Check out the conversation on Apple , Spotify , and YouTube . Brought to you by Jira Product Discovery Today's episode is about getting you insights from hundreds of customers. But where do you put that information? How do you turn it into decisions? That's where Jira Product Discovery enters the picture. It's a great place to put your feedback, requests, and ideas. Its AI helps connect each piece of feedback to the idea it supports. If you're in the Atlassian ecosystem, it's a no-brainer. Try Jira Product Discovery free Today's Episode Engineering is getting faster with AI. Is product management? I'd argue one way it can is by helping you talk to far more of your customers. You've probably used Claude to synthesize interview transcripts. But have you used it to run research with every customer who drops out of your funnel? Greg Greiner has. He was chief product officer at Bolt and head of product at Uber for Business. Now he's CEO of Woven . When he was CPO of Bolt, he was happy if he talked to 7 or 8 customers in a month. Today, he talks to every single one. With his AI. And customers convert more as a result: In today's episode, he breaks down how the entire system works, then gives you an entirely free system so you can build one in Claude Code. Learn the whole system ↓ Apple | Spotify | YouTube A Quick Plug I'm starting the next cohort of my Land a PM Job program on November 23rd. We have a jam packed schedule to help you with your search through March: Apply for Cohort 5 Newsletter Deep Dive Today's newsletter deep dive goes beyond the podcast and gives you a full kit to build customer agents and increase your conversion rates with this practical growth hack: Why have AI talk to your customers? The 6 moments to reach out to your customers Step-by-step: building the research agent in Claude Code How to add evals to keep these safe in production Subscribe now 1. Why have AI talk to your customers? One of the things you might be asking yourself is, why have AI talk to your customers? And that's a good question. AI research finds things that a typical in-app survey can't: Greg gave the anecdotal example of his work with Ancestry.com. Their customers started buying a DNA kit, but then would drop off. So they worked with Woven to have AI reach out to the email address or phone number people had left, and many wrote back. In fact, 3,470 replied. Here's what they said: 42.1% mentioned privacy and unexpected DNA discoveries 38.6% mentioned gifting versus personal-use timing 31.2% had subscription and hidden-fee concerns It essentially divided the issues into the right buckets and correlated those to what customers did after the conversation. So Ancestry could see how often each group went on to buy, against the baseline of everyone who talked. That helped them see the real lever was shipping and delivery timing. 41% of the people who raised it went on to buy, against 28% of those waiting for a promotion and 20% of those confused by the subscription. And the craziest thing: people who asked about shipping and delivery time got an answer from the AI and converted. So they were basically able to solve that problem. The subscription problem they were less able to solve. Why choose email when in-app chat seems smoother? The people you most want to hear from have already left your app. So an email is a great way to get to them. Greg mentioned only 20 to 40% of people respond, but this is still better than people talking to a website chat bubble. If you want to increase your response rate, speed matters. Do it right after the churn versus many days later. 2. The 6 moments to reach out to your customers It's not just churned customers. There are many different types of customers you might want to reach out to with AI for this type of email research. Here are the 6 most important moments: Started sign-up but didn't finish During their trial Trial ended without a purchase Tried a new upsell feature and didn't convert Usage dropped over the last few weeks They canceled Each one should get a plain-text email with a simple question. That's right, a plain-text email. And it should look something like this: As Greg said, most people try to ask too many questions at once, and that's recreating the survey in the email. Just ask one thing and let the customer lead. That's it. 3. Step-by-step: building the research agent in Claude Code For a lot of people it's not going to make sense to buy a dedicated product like Woven to accomplish this outreach. Greg built this whole loop in Claude Code and it took him about 30 minutes: You give Claude Code four things: The emails of people who dropped off. You can do this as a CSV from a CDP or your warehouse. The CLAUDE.md on how to approach the conversation and format the email. Your policies on what the agent can and can't do. A skill to send the emails. Greg told Claude he wanted an outreach program from his inbox, sent with the Gmail MCP. Then he pointed it at the customer data and said he wants to be reaching out to people who are 10 days into their trial. After some fixes, he had a working version in 30-40 minutes. You can use Gmail at small volume but will want to move to a proper sender like Postmark at volume. Greg shared the exact project he built for the episode. Get it on GitHub here: Get Greg's Claude Code project on GitHub New to Claude Code? Start with Andre Albuquerque's guide for non-technical PMs . And to see how far one folder can go, James McAulay runs his company's growth from a single Claude Code folder . 4. How to add evals to keep these safe in production Obviously you're going to want to build evals to make sure that the claims in your replies are backed by your documentation, and that they match your style, via an LLM judge . So this is what you type into Claude Code: We now want to add an eval step after classification for responses that are queued to be auto-sent. Focus that eval step on groundedness in the documentation. If the eval fails, rerun the generation process and save the new generation as a draft for review.
 Don't hand the agent the eval's note as exact instructions though. You end up overfitting where it's just taking this exact eval and it's like following it to a T. Pass the failure in as one more input to a full run. For the vast majority of cases where these evals are failing, you can pretty quickly get to a positive response. This is something I haven't seen somebody build before. If you launched this loop, I'd bet you'd see a bump in your groundedness metric, because the agent gets the feedback live. Nobody expects an email back in seconds: It's actually a little bit weird if you're responding like within seconds. In a chat, the same loop means someone sitting there waiting for minutes. Over email, the eval can fail and rerun without the customer ever noticing. Email buys your evals time. Go deeper on evals with Aparna Dhinakaran's episode and why most LLM judges fail . Final words Greg used to feel that Uber often had too many PMs. He was the only PM to about 25 engineers during his biggest scope over there. And he still calls it one of his most productive times. Because there was no room for anything but building a good product. AI brings that ratio back. 3-4 engineers can now produce what 20-25 used to. So go out there and have fun. Get Transcript To get my AI tool stack ($2,371 in tools, including Linear, Magic Patterns and Descript), become an annual subscriber ($150) and grab Aakash's bundle . To get my AI PM products ( PM OS , Job Search OS , Prompt Library and quarterly product drops), become a founding member ($250). Where to find Greg Greiner online LinkedIn Woven Share If this was useful, take a moment to follow us on Apple , Spotify and YouTube ! Your support helps me and the team keep bringing you high-quality resources for free.*

</details>