---
id: inbox_72b4b08b
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0145-latent-space-the-jev-revolution-what-engineers-are-al-45fd]]"
title: "The Jev Revolution: What Engineers Are Already Building with System One Models"
url: https://latent.space/p/jev-revolution/
source: latent-space
published_at: 2026-11-12T05:08:20+00:00
fetched_at: 2026-11-14T01:51:35.026999+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把快速、可靠的「System One」小模型像邏輯閘一樣嵌進程式碼，取代到處用大型 LLM 硬湊。 **Why** LLM 型軟體不可靠，「95% 的時間是愛因斯坦，5% 是豆豆先生」，無法分辨時就難以自動化。 **How** 系統一模型不生成文字，而是回傳結構化選擇、分數或機率，比推理 LLM 快且便宜；Almeida 主張「程式碼是自動化的語言」，所以要整合進程式碼中。 **What** AI Engineer Code Summit 上，TypeSafe AI 的 Diogo Almeida 提倡以 Jev 做「可靠智慧」。Glean 以其零樣本彈性處理分類，免去重複微調；UiPath 用 Jev 以「錦標賽」方式為文件 chunk 排名，數千次呼叫不到 1 秒；Workday 原型在使用者輸入時就預先填好請假表單。"
key_points:
  - "Almeida 的核心論點：LLM 讓你「95% 得到愛因斯坦、5% 得到豆豆先生」，分不清就難以自動化，所以要用 Jev 這類可靠的系統一模型"
  - "UiPath 用「錦標賽」排名 chunk：小組內選出最相關者、勝者晉級下一輪，數千次 Jev 呼叫不到 1 秒完成"
  - "Glean 的使用原則：決策空間分類變動時不必反覆微調（zero-shot 彈性），且對使用者隱藏背後用的是 Jev 還是 LLM"
tags: [system-one-models, jev, typesafe-ai, aie-code, smart-software]
topics: [engineering.architecture, product_and_org.adoption]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Jev Revolution: What Engineers Are Already Building with System One Models

把快速、可靠的「System One」小模型像邏輯閘一樣嵌進程式碼，取代到處用大型 LLM 硬湊。

**Why** LLM 型軟體不可靠，「95% 的時間是愛因斯坦，5% 是豆豆先生」，無法分辨時就難以自動化。

**How** 系統一模型不生成文字，而是回傳結構化選擇、分數或機率，比推理 LLM 快且便宜；Almeida 主張「程式碼是自動化的語言」，所以要整合進程式碼中。

**What** AI Engineer Code Summit 上，TypeSafe AI 的 Diogo Almeida 提倡以 Jev 做「可靠智慧」。Glean 以其零樣本彈性處理分類，免去重複微調；UiPath 用 Jev 以「錦標賽」方式為文件 chunk 排名，數千次呼叫不到 1 秒；Workday 原型在使用者輸入時就預先填好請假表單。

### 重點
- Almeida 的核心論點：LLM 讓你「95% 得到愛因斯坦、5% 得到豆豆先生」，分不清就難以自動化，所以要用 Jev 這類可靠的系統一模型
- UiPath 用「錦標賽」排名 chunk：小組內選出最相關者、勝者晉級下一輪，數千次 Jev 呼叫不到 1 秒完成
- Glean 的使用原則：決策空間分類變動時不必反覆微調（zero-shot 彈性），且對使用者隱藏背後用的是 Jev 還是 LLM

**原文：** [latent-space](https://latent.space/p/jev-revolution/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Today at the AI Engineer Code Summit , the main theme was system one models — non-generative models that return structured choices, scores, or probabilities. They’re also typically much faster and cheaper than reasoning LLMs (a.k.a. system two models). And who better to give an inspirational rallying cry for system one models than Diogo Almeida , co-founder and CEO of TypeSafe AI . Almeida was lead creator of Jev , the product that kicked off this trend less than two months ago. Jev was an instant revelation for AI engineers when it was released in September. In a podcast with Latent Space on launch (which quickly became our most popular episode of the year), Almeida explained the core problem with making LLMs the heart of software: reliability . In his keynote at AIE Code today, he took it a step further by claiming that Jev is “reliable intelligence” that should be used for “just automating everything.” Integrating system one models into code Of particular interest to AI engineers is Almeida’s point that system one models should become integrated with code. As he put it in his keynote, “code is the language of automation , therefore you need to integrate with code.” Latent Space founder swyx interprets this as a call to “liberally sprinkle ‘System One’ model calls everywhere INSIDE application code to make smarter software instead of increasingly convoluted forms of ‘concat strings together and hope for the best" AI engineering.’” The term “smart software” was used throughout Almeida’s presentation. It sounds like the kind of term used by companies like Microsoft or IBM during Web 2.0, but in the AI era it does actually signify a harsh reality about LLM-driven software: sometimes it’s just not very smart. As Almeida quipped during his presentation, “you get Einstein 95% of the time, but Mr. Bean 5% of the time.” “And if you can't tell which is which, how the fuck are you going to automate anything,” he added. Almeida ended with an impassioned plea to “automate everything.” Like an AI-pilled, pink-haired Steve Jobs, he called out to “the dreamers and the people who don't want to be limited by everything that has happened so far,” promising that TypeSafe AI wants to “really fight for you, and we want this to be as reliable as a fourth logic gate. ” How Glean uses Jev With the unenviable task of immediately following Almeida on stage, Chinmay Goyal from Glean presented a more prosaic version of Jev usage. He explained that system one models are used at Glean alongside LLMs and other types of classifiers, and that Jev is especially suited for “zero-shot flexibility.” “As the taxonomy of the decision space changes, we don't have to fine-tune these models again and again,” he said. In a short interview after his presentation, Goyal told Latent Space that their customers don’t actually need to know which type of model they’re using. “Jev powers a significant number of flows [but] the user just needs to have a product that works; that is always our aim with building anything. So we want to hide away all the complexity of whether we are using Jev or we are using a full-blown LLM.” In the conclusion of his presentation, Goyal offered some rules on when to use Jev: Jev patterns and prototypes Next up at AIE Code were Chibi Vikram and Kevin Bernstein from UiPath , a business orchestration and automation platform. One of their examples showed a test of Jev ranking document chunks . They held a “tournament” where Jev picked the most relevant chunks from small groups, then the winners advanced to another round, and so on. This whole process took under a second , even with thousands of Jev calls. “We realized that Jev is a building block that we can adjust ,” said Vikram about this and other experiments, “and we have to find these new strategies where we will be able to apply this building block. It might look less intelligent on its own, but with these strategies and patterns, we can get more intelligent — with even the current Jev model that we have.” Scott Roberts , a Principal Engineer at Workday , finished the ‘system one’ session at AIE Code with some prototypes his team has run with Jev. In one, an interface starts to fill in a time-off card while the user is still typing. It was an interesting showcase of Almeida’s idea that a fast model call can change what the software itself does. Roberts described it as going “from predicting what you want to say to predicting what you want to do.” Like the early internet The biggest learning I took from the System One presentations today is that a model like Jev can open up surprising new ways to build software . I was sitting next to a conference attendee who heads up AI at his company. He told me that in his spare time, he used Jev to create a website that sorts and ranks news about fantasy football. But the final word has to go to Almeida, who likened the new opportunities opened up by system one models to the experimentation of the early internet. “I think that there's going to be an explosion of what software can do, and we will want people to be exploring those boundaries of software. Not necessarily because it's valuable, but because they can, because we have new frontiers to explore , and this is what the early internet was like.”

</details>