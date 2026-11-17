---
id: inbox_65bcfefd
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2316-latent-space-cloudflare-joins-the-jevolution-and-labe-9f90]]"
title: "Cloudflare Joins the Jevolution and Labels Itself a Neolab"
url: https://latent.space/p/cloudflare/
source: latent-space
published_at: 2026-11-17T15:00:00+00:00
fetched_at: 2026-11-17T23:22:50.107405+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 自稱「neolab」，開始自己做小而快的模型，用來取代不必要的大型 LLM 呼叫。 **Why** 許多請求用 LLM 是殺雞用牛刀，既慢又容易出錯（如幻覺、輸出格式錯誤的 JSON）；自建模型也能降低對閉源模型授權、監管風險（如中國開源模型）的依賴。 **How** 採用 System One 概念：以小模型在毫秒級完成特定任務；團隊主要做 post-training，而非從零預訓練。Clairic 以單次 forward pass 從非結構化輸入抽取有型別的值。 **What** Cloudflare 的 Michelle Chen 在 AI Engineer Code Summit 發表兩款 System One 模型：Clef（受 TypeSafe AI 的 Jev 啟發，據稱兩週完成，Jev 花了兩年）與 Clairic（新類別的「extract」模型，可從發票等非結構化資料抽取、計算、估計、預測數值）。她也透露未來可能推出推理模型與其他 LLM；Cloudflare 是上市公司，Q3 營收 $782M、年化突破 $30 億，與 neolab 通常的定義（新創、無營收）不盡相符。"
key_points:
  - "Clef 為 Jev 風格的 decision model，據稱兩週完成；Clairic 是新類別「System One extraction model」，單次 forward pass 抽取有型別的值"
  - "Cloudflare 稱不會從零預訓練，團隊以 post-training 為主，並可能推出推理模型與其他 LLM"
  - "Q3 營收 $782M（年增 39%），年化營收超過 $30 億，與 neolab 通常的『新創、營收不多』定義不同"
tags: [cloudflare, neolab, system-one, small-models, post-training]
topics: [foundation_models.open_weights, product_and_org.product, engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Joins the Jevolution and Labels Itself a Neolab

Cloudflare 自稱「neolab」，開始自己做小而快的模型，用來取代不必要的大型 LLM 呼叫。

**Why** 許多請求用 LLM 是殺雞用牛刀，既慢又容易出錯（如幻覺、輸出格式錯誤的 JSON）；自建模型也能降低對閉源模型授權、監管風險（如中國開源模型）的依賴。

**How** 採用 System One 概念：以小模型在毫秒級完成特定任務；團隊主要做 post-training，而非從零預訓練。Clairic 以單次 forward pass 從非結構化輸入抽取有型別的值。

**What** Cloudflare 的 Michelle Chen 在 AI Engineer Code Summit 發表兩款 System One 模型：Clef（受 TypeSafe AI 的 Jev 啟發，據稱兩週完成，Jev 花了兩年）與 Clairic（新類別的「extract」模型，可從發票等非結構化資料抽取、計算、估計、預測數值）。她也透露未來可能推出推理模型與其他 LLM；Cloudflare 是上市公司，Q3 營收 $782M、年化突破 $30 億，與 neolab 通常的定義（新創、無營收）不盡相符。

### 重點
- Clef 為 Jev 風格的 decision model，據稱兩週完成；Clairic 是新類別「System One extraction model」，單次 forward pass 抽取有型別的值
- Cloudflare 稱不會從零預訓練，團隊以 post-training 為主，並可能推出推理模型與其他 LLM
- Q3 營收 $782M（年增 39%），年化營收超過 $30 億，與 neolab 通常的『新創、營收不多』定義不同

**原文：** [latent-space](https://latent.space/p/cloudflare/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare has been one of the essential infrastructure companies of the web for the past decade and a half. But now, it’s turning into a neolab — at least according to a presentation at AI Engineer Code Summit by Michelle Chen , who runs Cloudflare’s AI Platform on the product side. We’ll get into what exactly a neolab is in a minute (the short version: they build models and they’re not called OpenAI or Anthropic). Cloudflare is claiming to be one because it too has begun to launch models. Two System One models , to be precise: Clef and Clairic. As Chen explained in her talk, Clef is a decision model directly inspired by TypeSafe AI’s revolutionary Jev model , while Clairic is a new type of system one model that Cloudflare calls an “extract” model . In an interview with Latent Space after her presentation, Chen hinted that Cloudflare won’t just be producing system one models. There will be large language models, too. “We're not being a neolab [to] only launch system one models, even though it makes sense for our infrastructure. We've kind of entered this Pandora's box now, right? We opened it, now the possibilities are endless.” Chen said it’s “not just system one models, but potentially reasoning models that we've been experimenting with, and other LLMs and whatnot.” However, she added that these probably won’t be pre-trained models built from scratch, like the frontier labs produce. “I don't think that's our focus, but I think we can take existing resources out there and make [them] a lot more efficient and effective.” She noted that “most of our team really just does post-training,” so that will be the focus in model development. What is a neolab and is Cloudflare really one? The term neolab literally means a ‘new lab’ and it was coined last November by Stephanie Palazzolo from The Information, who defined it as “a new generation of research-focused AI startups.” Deedy Das , a partner at Menlo Ventures and an AI influencer, runs a big list of neolabs . It includes companies like Thinking Machines Lab, Poolside, and TypeSafe AI itself. According to Das, neolabs employ elite researchers, spend a lot of compute (“usually to train its own AI model”), don't have significant revenue traction, and they’re typically startups that have raised a lot of money. Deedy Das’ list of neolabs — note that TypeSafe is among the top 20. Cloudflare doesn’t tick at least half of those boxes, since it’s a public company with significant revenue traction . In fact, earlier this month Cloudflare announced record earnings . “The third quarter was Cloudflare's best quarter ever,” said CEO Matthew Prince . “We crossed $3 billion in annualized revenue with revenue of $782 million, up 39% year over year.” So Cloudflare as a “neolab” is pushing the accepted definition. However, as Chen argued in her presentation, building models is part of a natural progression for the company : from infrastructure, to compute (e.g. the Workers platform, including now for agents), to storage, to serving open weight models like Kimi, GLM and DeepSeek (on Workers AI), to now building its own models. Jev as the “east wind” Chen readily admits that Jev inspired Cloudflare’s pivot to building models. Referencing a Chinese proverb, she framed Jev’s arrival in September as “the east wind” that unexpectedly changed how Cloudflare viewed AI models. “And so when the system one and Jev paradigm started coming on board,” Chen said in her presentation, “we were like, this makes so much sense for us to adopt, right? We don't have to send every request to an LLM. We can send some of it to a System One model.” In our conversation, Chen commented on how it took only two weeks for them to build Clef — which is a copy of Jev — whereas it took TypeSafe AI two years to build Jev. She meant that as a compliment for how hard TypeSafe AI worked to create this new type of model. “All credit to TypeSafe, really, for actually attacking this space and inventing something new here , that people could relate to so strongly and be able to use it. And, yeah, we came up with a model super quickly, but they put in a lot of legwork and we knew exactly what the API schema should look like and whatnot.” Cloudflare is, at its core, still an infrastructure company — speed and low latency is its meat and potatoes. The main benefit of System One models, Chen remarked, is that they allow more work to be done by smaller, faster models , where output is measured in milliseconds rather than seconds. Clairic and what extraction models do While Clef was a clone of Jev, Cloudflare soon came up with an original twist on System One with Clairic , launched last month as “the first model in a new class: System One extraction models.” “What Clairic does is it can take unstructured input, and it can extract, compute, estimate and forecast values from those inputs,” Chen explained in her presentation. In our interview, Chen said that her team wanted to use System One principles to find other areas where LLMs were “overkill” and didn’t always return the right answer. One of the problems they settled on was that LLMs don’t always deal well with unstructured input. Because LLMs are autoregressive, Chen explained, they are prone to hallucinate and they sometimes return malformed JSON. “So we used the same System One principles [as Jev/Clef] there, and decided on extraction.” Some examples of system one use cases at Cloudflare. She used the example of an invoice, where an LLM will sometimes get an important detail wrong — like the order number. “When you send it [the order] to an LLM, they're like, wait, I think the order number's three, maybe it's four, maybe it's five. But it's like, the number's right there, you just have to read it! ” So the idea with Clairic is that it will extract a typed value — like a number — from unstructured data, in one forward pass. Why Cloudflare is in the lab now Using the label “neolab” sounds a bit like a marketing gimmick, but it also makes a ton of sense for Cloudflare to produce system one models — and even, in future, reasoning models. “Being a neolab means that we can create what we are missing,” Chen said in her presentation. In our interview, she also mentioned that creating their own models allows Cloudflare to derisk its AI operations. “I think there's a lot of risk in the AI space , because just like Jev was closed source and we couldn't run it, there [are] a lot of models out there [with] maybe regulatory risks coming up, like the Chinese open source models. I think lots of model labs want to actually make money, as well — so enforcing quite expensive licenses.” If you look at Cloudflare’s product page now, it resembles what Amazon’s cloud computing product page looked like at the height of Web 2.0 — i.e. there’s a lot there! But there’s still room for several more models.

</details>