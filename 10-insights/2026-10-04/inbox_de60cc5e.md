---
id: inbox_de60cc5e
date: 2026-10-04
source_ref: "[[00-inbox/2026-10-04/0102-lobsters-ai-kolibri-a-sovereign-open-weight-model-f41f]]"
title: "Kolibri: A Sovereign Open-Weight Model"
url: https://aleph-alpha.com/en/blog/kolibri-has-landed-a-sovereign-open-weight-model/
source: lobsters-ai
published_at: 2026-10-04T02:57:55-05:00
fetched_at: 2026-10-25T01:26:32.361058+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "德國公司 Aleph Alpha 釋出以德文與英文為主、可在地部署的 MoE 開放權重模型 Kolibri。 **Why** 公部門與受監管產業需要可控、可稽核，且不必把資料送往第三方推論服務的模型。 **How** 採 78B 總參數、約 3B 活躍參數的 MoE（384 個小專家），50 層中只有 10 層處理完整上下文，其餘 40 層使用 512-token 視窗，並以自動化訓練 pipeline 每小時評估 checkpoint。 **What** 以 Apache 2.0 授權於 Hugging Face 開放完整權重，支援最長 1M tokens；官方宣稱在數學、程式、grounding 與長上下文任務上可匹敵活躍參數多 4 倍的模型（如 Nemotron 3 Super）。"
key_points:
  - "78B 總參數、約 3B 活躍；50 層中僅 10 層處理完整上下文，其餘 40 層使用 512-token 視窗"
  - "預訓練約 20T tokens（德文佔 21.3%、翻譯約 6%），使用 768 張 B200，三階段合計約 24T tokens"
  - "21 天預訓練中發生 38 次非預期中斷（約每 10,000 GPU 小時一次），pipeline 自動恢復，最多回退 250 steps"
tags: [open-weights, moe, sovereign-ai, german-llm, long-context]
topics: [foundation_models.open_weights, engineering.inference]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Kolibri: A Sovereign Open-Weight Model

德國公司 Aleph Alpha 釋出以德文與英文為主、可在地部署的 MoE 開放權重模型 Kolibri。

**Why** 公部門與受監管產業需要可控、可稽核，且不必把資料送往第三方推論服務的模型。

**How** 採 78B 總參數、約 3B 活躍參數的 MoE（384 個小專家），50 層中只有 10 層處理完整上下文，其餘 40 層使用 512-token 視窗，並以自動化訓練 pipeline 每小時評估 checkpoint。

**What** 以 Apache 2.0 授權於 Hugging Face 開放完整權重，支援最長 1M tokens；官方宣稱在數學、程式、grounding 與長上下文任務上可匹敵活躍參數多 4 倍的模型（如 Nemotron 3 Super）。

### 重點
- 78B 總參數、約 3B 活躍；50 層中僅 10 層處理完整上下文，其餘 40 層使用 512-token 視窗
- 預訓練約 20T tokens（德文佔 21.3%、翻譯約 6%），使用 768 張 B200，三階段合計約 24T tokens
- 21 天預訓練中發生 38 次非預期中斷（約每 10,000 GPU 小時一次），pipeline 自動恢復，最多回退 250 steps

**原文：** [lobsters-ai](https://aleph-alpha.com/en/blog/kolibri-has-landed-a-sovereign-open-weight-model/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Kolibri Has Landed: A Sovereign Open-Weight Model

What Kolibri Delivers

How We Built Kolibri at High Velocity

Benchmarks

Get Started

Contact for Deployment and Specialization

Foundational capabilities for enterprise and government

Contextualized performance for real-world applications

Control and compliance by design: upholding our customers' sovereignty

Our Model Factory: two models, three months apart

Architecture and pre-training

Post-training at scale

German pre-training data

Specialized tokenizers for English-German

Grounding: reducing hallucinations

Contextualized performance

 Aleph Alpha 

On the Day of German Reunification, we are releasing our new model: Kolibri.

Kolibri is an English-German Mixture-of-Experts Transformer with 78B total parameters, 3B
 active. It supports context lengths of up to 1M tokens. The model can be downloaded with the
 full weights on Hugging Face and used under the Apache 2.0 license terms.

Kolibri is the result of continuous iteration of our model training effort. We first built a model training pipeline and validated it by building Kolibri Origin, a 30B total, 3B active model with a much shorter
 65k token context window. Kolibri ran through the same pipeline: from data ingestion and curation,
 through ablations, pre-training, and post-training, to the final evals. It enabled running hundreds
 of ablation experiments and stable pre-training that ran without a person having to step in when
 hardware failed or a data connection dropped. We continuously monitored training metrics and standardized
 monitoring for custom benchmarks. The time we put into building and iterating on this pipeline
 was a valuable investment. We see it in how much better Kolibri is than Kolibri Origin, and in
 how little time separates their releases.

Kolibri is a specialized language model built for sovereign mission-critical work in
 regulated areas including public administration, industrials and aerospace. We specialized
 Kolibri for German, reasoning, math, agentic behavior, and further capabilities our
 customers need in production. The aim of this specialization was to optimize performance in
 our customers' specific use cases. Through specialization, customers achieve contextualized
 performance in their AI operations and they can monitor its economic impact, so that ROI
 stays measurable and grows over time.

Specialization alone is not enough. Sovereignty is just as important. Sovereignty, for us,
 combines two dimensions: how we built the model, and how it transfers to our customers. We
 offer full supply-chain integrity and account for every decision, from data ingestion,
 through pre- and post-training, to the final evaluations. We provide transparency. Customers
 have full freedom of deployment and intellectual-property safety, so compliance comes as an
 inherited property of the model.

Read our tech report for full details.

We optimized Kolibri for performance across a wide range of sectors considering their
 particular domain-specific language, regulatory, and procedural realities. Its small and
 efficient size provides our customers with flexibility to run it efficiently on-premise,
 without sending internal data to third-party inference services. The spotlight in this
 section introduces the model's capabilities, before we describe them in section How we built Kolibri at high velocity .

With Kolibri we optimize the trade-off between model capability and deployment costs, using
 3B active parameters out of 78B total. Kolibri sits on the Pareto frontier for quality
 versus serving cost, for both English and German. The Pareto frontier is a concept from
 economics, marking the best achievable combinations of two objectives, where improving on
 one means giving up some of the other. None of the compared models delivers more quality at
 the same serving cost, or the same quality at lower cost.

English

German

Across math, coding, grounding, and long-context tasks, Kolibri matches models with up to
 four times its active parameter count, such as Nemotron 3 Super.

Public benchmarks fail to capture specialized sector needs, so we developed our own internal
 evaluation suites for the verticals that matter to our customers, such as the German public
 sector, aviation, manufacturing and the automotive industry. Each suite mirrors the skills,
 workflows, and edge cases required in these sectors, and paired synthetic training
 environments let us improve Kolibri against these evaluations without ever training on
 customer data. Read more in section Contextualized performance .

 Answers that are grounded in your documents. We trained Kolibri with abstention
 data and with our Merlin-Arthur protocol. As a result, it is trained to say "I don't know" when
 the answer isn't in the context. Our customers value and request this feature, so we continuously
 track and validate abstention accuracy. We provide more details in the Grounding section.

 Native German and English model. We developed a bilingual German/English tokenizer
 and focused on including organic German data throughout the training process of the model, so that 21.3% of the pre-training tokens are German.
 We used translation sparingly (6% overall), since translated text tends to carry the cultural
 fingerprint of its source language. The result is a model that is bilingual by design, not an
 English model that has read some German. Read more in sections German pre-training data and Specialized tokenizers .

We built Kolibri with the EU AI Act, the General-Purpose AI Code of Practice and the GDPR in mind from the ground up, with copyright law being a focus of our work to trustworthy
 technology.

We are transparent about our model weights and about curation of our training data , so that decisions behind development are visible. Through its reasoning traces, it
 becomes explainable how the model came to a particular answer. With our Merlin-Arthur protocol the model grounds trustworthiness : Kolibri refrains from answering when
 the context doesn't support an answer.

Our teams built the model in Germany, trained it on infrastructure in Germany and Finland,
 under European and German law, with no foreign control . We own the entire
 pipeline, from data curation, through pre- and post-training, to optimization in our Model
 Factory. This control of our end to end pipeline underpins the model's sovereignty. Control
 also passes on to our customers and Kolibri's small size gives them full freedom of
 deployment and supports controllable reasoning effort to trade cost and latency against
 answer quality.

Our Model Factory is our answer to iteration speed, minimizing the time it takes to go from
 knowing what a model gets wrong to training one that does better. We implemented the
 training pipeline as code, so that the learnings of our team landed in one versioned
 training recipe instead of scattered scripts and notes. Here is what that looked like
 between Kolibri Origin and Kolibri.

Work on the pipeline began in January. Five months and hundreds of ablation runs later,
 Kolibri Origin finished pre-training at target scale on 11 June. Kolibri finished on 11
 September. In the three months between those two dates we went from 30B parameters to 78B,
 from a 65k-token context window to up to 1M, and from 7.5T training tokens to 20T. To get
 those 20T, the pipeline processed over 200T tokens of raw data, filtering, deduplicating,
 and curating it down to what we actually trained on. We changed the attention design,
 tripled the number of experts, increased sparsity, replaced the routing algorithm, improved
 our post-training data, more than doubled the number of environment tasks, and taught the
 model to reason at four different effort levels. Both models kept a similar number of
 parameters active per token, yet Kolibri trained faster per token than Kolibri Origin thanks
 to the work of our efficiency team.

What made this possible is our training pipeline, an effort to convert research-grade model
 development into a fully automated production-ready infrastructure to design and train large
 language models. Our pipeline codebase was shared by all . Every proposed code change triggers a small end-to-end model run; training, evaluation,
 to find out if something broke within minutes. Our runs are GitHub Actions workflows, and
 reproducing one means checking out a commit. We used the pipeline for the main training and
 the hundreds of ablations that ran to make our architectures and data-mix decisions.

Training checkpoints land roughly every hour and the pipeline automatically evaluates them
 on English and German knowledge, maths, code, instruction following, tool use, long context,
 safety, abstention to hallucination and grounding. We can watch capabilities appear every
 day rather than finding out how the model turned out at the end. The run itself held up
 better than we expected. Over 21 days of pre-training of Kolibri, we hit 38 unplanned
 interruptions, roughly one per 10,000 GPU-hours, caused by hardware faults or a connection
 timing out. Those were automatically handled by the pipeline without manual intervention.
 The cluster automatically restarted the training job(s) on a different set of nodes, and
 training picked up from a checkpoint at most 250 steps back.

Having access to the whole pipeline, with checkpoints available to everyone, means that any
 team can own a capability end to end rather than a stage of an assembly line. One team
 trained and evaluated the grounding capability of Kolibri as a single piece of work,
 seamlessly integrating into the overall model.

However, getting here was not a linear walk. We stumbled. We stopped the Kolibri Origin
 pre-training after a few trillion tokens and restarted it from scratch, as we identified a
 data-shuffling bug that escaped our tests. We ran ablations, took decisions, only to find a
 bug or an error in the configuration afterwards, forcing us to rerun some experiments.
 Alongside our own experience, we tracked state-of-the-art architectures, best practices, and
 the latest research advances in LLMs. Those accumulated learnings led to improvements in our
 processes and guardrails in our pipeline.

Looking at the delta between Kolibri Origin and Kolibri, the improvement is notable, but
 this is also the easy direction: more parameters, more data, a well-understood architecture
 family, and still at small scale. As we are contemplating scaling up, we are happy to face
 challenges on our foundation. But the most durable thing we built this year is not the
 pipeline, it is a team with the proven capability to build, post-train, and ship LLMs from
 raw data at high velocity.

Kolibri has 78B total parameters, which is 2.5 times more than Kolibri Origin, with ~3B
 active parameters. In our experiments, increasing the size of our model from 32B to 123B led
 to ever-improved performance. Yet the larger size came with larger training and serving
 costs. The latter drove the decision: 123B can handle only 3 long-context 256k-token user
 queries on two H100s, while 78B handles 18 concurrent requests and decodes 28% faster. We
 used 384 smaller experts rather than fewer wide ones, as they performed better in our tests.
 We applied the same efficiency-first reasoning to attention. Out of 50 total layers, only 10
 process full context, while the remaining 40 use a tight 512-token focused window. This
 keeps decode computation and memory bounded in those layers regardless of context length.
 The efficiency gains benefit both serving the trained model and training during
 post-training RL, which relies on huge amounts of inference.

We trained Kolibri on 768 B200 GPUs in three stages: 20T tokens of pre-training at a 16k sequence length over 21 days, 3.44T tokens
 of mid-training at 64k, and 200B tokens of long-context adaptation at 256k. This is nearly 24T
 tokens in total, roughly three times what Kolibri Origin consumed. G

[... truncated for safety ...]

</details>