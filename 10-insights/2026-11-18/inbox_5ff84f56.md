---
id: inbox_5ff84f56
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-tomsguide-chatgpt-i-tested-chatgpts-new-gpt-6-2-astra-with-2b1d]]"
title: "I tested ChatGPT’s new GPT-6.2 Astra with one prompt — and built a website I’d actually use"
url: https://www.tomsguide.com/ai/chatgpt/i-tested-chatgpts-new-gpt-6-2-astra-with-one-prompt-and-built-a-website-id-actually-use
source: tomsguide-chatgpt
published_at: 2026-11-18T06:45:00+00:00
fetched_at: 2026-11-19T08:22:12.466961+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用一段完整需求描述，讓 AI 直接生成可互動的家庭管理網站。 **Why** 作者想要一個能把行事曆、餐點與家務集中管理的工具，並想測試 GPT-6.2 Astra 能否從文字描述直接做出可用成品。 **How** 作者在 ChatGPT Work 中送出一則長 prompt，要求功能彼此連動、不追問、自行決定設計，並在完成前自行測試、說明無法驗證的部分。 **What** 文章稱 OpenAI 同週推出 Astra 與較快的 Sol；作者在第 11 分鐘追問進度，最後得到含行事曆、餐點規劃、自動產生購物清單、家務追蹤與儲存功能的網站；Astra 目前透過 ChatGPT Work 開放給符合條件的 Plus、Pro、Enterprise 與 Edu 用戶。"
key_points:
  - "prompt 要求行事曆增刪移動事件、餐點自動產生購物清單並可勾選、家務指派與進度追蹤，且資料刷新後保留"
  - "作者回報 Astra 在過程中會說明進度，並列出仍待測試的互動項目；文章未提供基準測試數據"
  - "文章指出 Astra 未加入一般 Chat 模型選單，需在 ChatGPT Work 中依權限選用"
tags: [gpt-6-2-astra, website-generation, chatgpt-work, model-launch]
topics: [foundation_models.gpt, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I tested ChatGPT’s new GPT-6.2 Astra with one prompt — and built a website I’d actually use

用一段完整需求描述，讓 AI 直接生成可互動的家庭管理網站。

**Why** 作者想要一個能把行事曆、餐點與家務集中管理的工具，並想測試 GPT-6.2 Astra 能否從文字描述直接做出可用成品。

**How** 作者在 ChatGPT Work 中送出一則長 prompt，要求功能彼此連動、不追問、自行決定設計，並在完成前自行測試、說明無法驗證的部分。

**What** 文章稱 OpenAI 同週推出 Astra 與較快的 Sol；作者在第 11 分鐘追問進度，最後得到含行事曆、餐點規劃、自動產生購物清單、家務追蹤與儲存功能的網站；Astra 目前透過 ChatGPT Work 開放給符合條件的 Plus、Pro、Enterprise 與 Edu 用戶。

### 重點
- prompt 要求行事曆增刪移動事件、餐點自動產生購物清單並可勾選、家務指派與進度追蹤，且資料刷新後保留
- 作者回報 Astra 在過程中會說明進度，並列出仍待測試的互動項目；文章未提供基準測試數據
- 文章指出 Astra 未加入一般 Chat 模型選單，需在 ChatGPT Work 中依權限選用

**原文：** [tomsguide-chatgpt](https://www.tomsguide.com/ai/chatgpt/i-tested-chatgpts-new-gpt-6-2-astra-with-one-prompt-and-built-a-website-id-actually-use)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I’ve tested plenty of AI tools that promise to make life easier, but I usually end up spending more time figuring out how to use them than I save. That’s why one particular feature of OpenAI’s new GPT-6.2 Astra caught my attention. According to OpenAI’s announcement , the company’s newest frontier model can build more attractive, functional websites from a written description. You don’t need to know how to code, design a website, or understand what happens behind the scenes. As a working mom of three, I immediately thought of something I could actually use. Between school schedules, activities, dinner plans and the endless list of things everyone needs to remember, keeping a family organized can feel like a full-time job. So I decided to give GPT-6.2 Astra a single prompt and see whether it could build a family command center to keep everything in one place. My goal wasn’t to create another pretty dashboard. I wanted a website where I could move things around on a calendar, plan dinners, automatically generate grocery lists, and track chores without jumping between apps. And I wanted ChatGPT to build the entire thing without asking me a dozen follow-up questions. Why GPT-6.2 Astra is worth testing (Image credit: Shutterstock) OpenAI introduced GPT-6.2 Astra on Tuesday, alongside GPT-6.2 Sol, a faster, more efficient model designed for everyday tasks. Astra is the more powerful of the two, with improvements in coding, visual design and complex projects that require multiple steps. One of the more interesting claims is that the model can create websites that not only look better but actually work better. OpenAI says Astra has improved visual reasoning, helping it choose layouts, images and interactive elements that fit the purpose of a website. This matters because building something useful takes more than generating a page with a few buttons. Those buttons need to work, information needs to update correctly, and the experience should make sense to someone who isn’t a developer. For this test, I wanted to see how close Astra could get to a finished website using nothing more than one detailed prompt. The one prompt I used (Image credit: Olena Malik / Getty Images) I opened ChatGPT Work, selected GPT-6.2 Astra and entered the following prompt: Build me a fully functional, interactive family command center website that helps a busy household with three children stay organized. I want a weekly calendar where I can add, edit and move events, including school activities, appointments and family plans. Include a meal planner for breakfast, lunch and dinner that automatically generates a grocery list based on the meals I select. Let me check off grocery items as I shop. Add a chore tracker where I can assign tasks to different family members, mark them complete and see everyone's progress throughout the week. Create a homepage dashboard showing today's events, upcoming activities, tonight's dinner and anything that still needs to get done. Make the website beautiful, modern, mobile-friendly and simple enough for children and adults to use. Use realistic sample data so I can test everything immediately. Every button, calendar interaction, checkbox and calculation must function. I don't want a static mockup. Store changes so my information doesn't disappear when I refresh the page, if the available environment supports persistent storage. Do not ask follow-up questions. Make reasonable design decisions yourself and build the complete experience. Before finishing, check the functionality, test the interactions and fix any problems you find. Tell me what you were unable to verify. I deliberately included several features that depend on one another. A meal planner is useful on its own, but it becomes much more interesting when the meals automatically populate a grocery list. I also wanted to see whether Astra could handle the less glamorous parts of building a website, such as saving changes and making sure everything still worked when I returned. What GPT-6.2 Astra built (Image credit: Future) As Astra worked, it kept me updated on its progress with responses like, "I’ll build a complete family organizer with a shared calendar, meal planning and grocery lists, chore tracking, and a dashboard, then test the main interactions and saved data." And then it went on to say, "The design is taking shape as 'Hearth,' with a calm dashboard and a color for each family member. I’m connecting the calendar, meal planner, grocery quantities, and weekly chore progress so changes carry through the whole app. At any time I could have interrupted the model and suggested it go a different way. For instance, if instead of a calm theme, I could have had it use bold or even neon colors to reflect the chaos of a home with three young children. Of course, I stayed with calm. Every little bit helps. It's important to note, if you're going to ask GPT-6.2 to create a website, it isn't as fast as Gemini Hydrogen. That's not because it's not as good or not working correctly, each model just works differently, and that includes latency. After 11 minutes, I asked, "Are you almost done?" It then responded with, "The visual layout is ready, and I’m finishing the interactive features. I still need to test adding and moving events, generating groceries, checking off chores, and saving through a refresh before it’s ready to use." When it finally completed the task, a beautiful, fully functional website in the browser appeared. I was truly surprised by how nice the website turned out. Astra built a site that handles multiple connected tasks, remembers my changes and works without constant troubleshooting, that's a much more compelling demonstration of what AI can do than another chatbot answering questions. Bottom line GPT-6.2 Astra is available through ChatGPT Work for eligible Plus, Pro, Enterprise and Edu users, with access depending on the rollout and workspace permissions. The model is not being added to the regular Chat model selector as part of this launch. To try it, open ChatGPT Work, select GPT-6.2 Astra if it's available and paste in the prompt above. You can customize it for your own household, changing the number of family members or adding features you'd find more useful. You can also adapt the same approach to build a vacation planner, homework tracker, personal budget dashboard or other simple web app. The best way to judge the result is to try using it. Give it a try and let me know in the comments what you think. More from Tom's Guide Google's Gemini 4 Hydrogen is free — here are 5 impressive things you can do with it I found a free AI trick that could make your old smart TV feel new again Claude just got 3 powerful new tools — and they could replace some of your favorite apps

</details>