---
id: inbox_c6bdbbca
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0106-lobsters-ai-the-sleep-framework-a-new-way-for-llms-t-337e]]"
title: "The sleep framework: A new way for LLMs to retain knowledge in continual learning"
url: https://research.google/blog/the-sleep-framework-a-new-way-for-llms-to-retain-knowledge-in-continual-learning/
source: lobsters-ai
published_at: 2026-11-18T15:53:43-06:00
fetched_at: 2026-11-20T01:15:02.250681+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 LLM 在清醒互動與離線「睡眠」鞏固之間交替，減少災難性遺忘並寫入新知識。 **Why** 持續更新參數容易造成災難性遺忘，只靠 in-context learning 則短期資訊在 session 結束後即消失。 **How** 睡眠階段包含記憶鞏固（以低秩 MoE 專家承接短期記憶，並用 on-policy 蒸餾與語意獎勵對齊）與夢境（隨機啟用專家產生合成資料，以梯度篩選樣本後做 RL 精修）。 **What** 作者報告：BABILong 可擴展至 10M tokens；SQuAD 單任務 48.9%、CPT 46.2%；AIME 24、AIME 25、HMMT 25 分別為 79.2%、69.0%、46.1%。"
key_points:
  - "循環分為 Active（清醒）與 Sleep 兩相：清醒時存入短期記憶，睡眠時進行 Consolidation（記憶鞏固）與 Dreaming（夢境自我改進）"
  - "Consolidation 以 GKD 與 RL 模仿（LTI，以 Levenshtein 距離給獎勵）把短期 token 蒸餾進新展開的 MoE 專家，完成後重設高頻暫存參數"
  - "Dreaming 讓 MoE 路由隨機啟用非標準專家產生合成資料，以梯度資料選擇篩選，再做 SFT 與 RL 精修；原文稱仍在固定模型架構內運作，只是解鎖預先配置的 MoE 記憶區塊"
tags: [continual-learning, catastrophic-forgetting, mixture-of-experts, memory-consolidation, google-research]
topics: [research.training, engineering.architecture]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The sleep framework: A new way for LLMs to retain knowledge in continual learning

讓 LLM 在清醒互動與離線「睡眠」鞏固之間交替，減少災難性遺忘並寫入新知識。

**Why** 持續更新參數容易造成災難性遺忘，只靠 in-context learning 則短期資訊在 session 結束後即消失。

**How** 睡眠階段包含記憶鞏固（以低秩 MoE 專家承接短期記憶，並用 on-policy 蒸餾與語意獎勵對齊）與夢境（隨機啟用專家產生合成資料，以梯度篩選樣本後做 RL 精修）。

**What** 作者報告：BABILong 可擴展至 10M tokens；SQuAD 單任務 48.9%、CPT 46.2%；AIME 24、AIME 25、HMMT 25 分別為 79.2%、69.0%、46.1%。

### 重點
- 循環分為 Active（清醒）與 Sleep 兩相：清醒時存入短期記憶，睡眠時進行 Consolidation（記憶鞏固）與 Dreaming（夢境自我改進）
- Consolidation 以 GKD 與 RL 模仿（LTI，以 Levenshtein 距離給獎勵）把短期 token 蒸餾進新展開的 MoE 專家，完成後重設高頻暫存參數
- Dreaming 讓 MoE 路由隨機啟用非標準專家產生合成資料，以梯度資料選擇篩選，再做 SFT 與 RL 精修；原文稱仍在固定模型架構內運作，只是解鎖預先配置的 MoE 記憶區塊

**原文：** [lobsters-ai](https://research.google/blog/the-sleep-framework-a-new-way-for-llms-to-retain-knowledge-in-continual-learning/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The sleep framework: A new way for LLMs to retain knowledge in continual learning

Rethinking machine learning: Active (wake) vs. sleep phases

Key components of the sleep process

Theoretical foundations

Conclusion

Acknowledgements

Other posts of interest

1. Memory consolidation

2. Dreaming for self-improvement

October 27, 2026

Ali Behrouz and Vahab Mirrokni, Google Research

We introduce a sleep phase in continual learning, enabling large language models to continuously integrate new facts and enhance reasoning while mitigating catastrophic forgetting or static knowledge cutoffs.

Modern LLMs achieve impressive performance via pre-training and in-context learning (ICL). However, once deployed, they remain largely static, operating with a fixed knowledge cutoff date that leaves them unable to acquire long-term capabilities or adapt to new information.

While updating models with new data seems like the obvious solution, continual parameter updates often trigger catastrophic forgetting , a fundamental issue where learning new tasks severely degrades performance on previously learned ones. Alternatively, relying strictly on ICL limits knowledge retention to the immediate context window: once the context session ends, the acquired short-term information is forgotten.

Inspired by how the human brain processes and stabilizes memory during rest, we introduce a sleep framework in continual learning: a learning paradigm that equips large language models (LLMs) with a continuous periodic lifecycle, enabling them to continually learn, consolidate fragile short-term context into stable long-term parameters. With this framework, we demonstrate that alternating between active interaction and offline memory consolidation allows LLMs to continuously acquire new facts, retain long-context knowledge up to 10M tokens, and improve complex reasoning.

Traditional machine learning relies on a strict separation between training and inference. In a continual learning framework, this distinction becomes artificial; an intelligent agent must constantly learn, adapt, and process information.

Under the sleep paradigm, an LLM operates across two primary states:

While terms like "sleep," "dreaming," and "self-improvement" borrow from neuroscience, our framework operates entirely within a fixed model architecture and human-defined training rules. During the offline sleep phase, the model unlocks pre-allocated Mixture-of-Experts (MoE) memory blocks and updates its numerical weights using self-generated practice examples. This automated post-training cycle helps a deployed model absorb new facts and sharpen its reasoning accuracy while keeping its core codebase and design unchanged.

The sleep paradigm addresses catastrophic forgetting and continuous adaptation through two stages: memory consolidation and dreaming.

In the human brain, non-rapid eye movement (NREM) slow-wave sleep consolidates fragile memories into long-term structures via abstraction and distillation. Our proposed sleep framework mirrors this natural phenomenon through two key technical mechanisms:

Overview of our sleep framework: Input streams from the active phase are stored in short-term memory before entering the sleep cycle, which bifurcates into Consolidation (transferring fragile short-term tokens into expanded long-term parametric memory using low-rank structures and MoE) and Dreaming (autonomous self-improvement via synthetic routing with random experts and RL refinement).

During REM sleep , the human brain actively simulates scenarios, consolidates emotional/semantic connections, and explores novel neural pathways. Mirroring this, during the “dreaming stage”, the sleep framework implements an autonomous self-improvement loop:

Beyond the empirical results, our sleep paradigm is grounded in a theory that clarifies why its two stages (memory consolidation and dreaming) can support continual learning without simply trading new knowledge for old capabilities.

For memory consolidation, the analysis shows that knowledge seeding can be understood as a structured, low-rank compression problem. The model is not asked to copy every detail of its short-term traces into its parameters. Instead, it identifies a compact set of directions that best preserve both the model’s own on-policy behavior and the semantic qualities rewarded by the learning objective.

This perspective explains the complementary roles of the two signals: on-policy distillation aligns consolidation with the trajectories the model will actually produce at inference time, reducing the mismatch that can arise when training only on teacher-generated distributions; meanwhile, the semantic reward changes what is worth retaining, prioritizing directions that preserve meaning and task-relevant behavior rather than merely matching token probabilities. Parameter expansion then provides the capacity needed to write these selected memories without overwriting previously consolidated knowledge.

For dreaming, the theory characterizes random expert activation and reward-based sample selection as mechanisms for improving the geometry of learning. Injecting different MoEs broadens the set of gradient directions explored during synthetic generation, exposing the model to a richer collection of updates than those induced by its ordinary wake-time data alone. Gradient-based filtering then emphasizes the synthetic experiences that carry the most useful learning signal, strengthening informative directions while preserving the structure of the underlying gradient space.

Together, these steps yield a more balanced optimization landscape: learning is less dominated by a small number of directions, gradients are better conditioned, and the model can make more stable progress when refining its capabilities. In this view, dreaming is not simply self-generated data augmentation; it is a deliberate process for diversifying, selecting, and consolidating the updates through which the model improves itself.

Comparative performance of our sleep framework against baseline approaches (such as in-context learning and supervised fine-tuning) across major evaluation axes, including Class-Incremental Learning, continual translation, long-context scaling up to 10M tokens, factual knowledge incorporation, and mathematical reasoning.

For continual translation , in unseen languages, such as Manchu and Kalamang, the sleep framework maintained a near-zero performance drop in multi-stage evaluations, whereas standard baselines like ICL, Cartridges , and supervised fine-tuning (SFT) suffered severe catastrophic forgetting during sequential learning.

In long-context understanding on the BABILong benchmark, our sleep method demonstrated near-perfect scaling up to 10M tokens, outperforming strong baselines like GPT-4 , and Titans by using sleep-time consolidation to compress long-context information directly into parametric memory.

For factual knowledge incorporation evaluated on SQuAD and continued pre-training (CPT), our sleep method achieved 48.9% on single-task and 46.2% on CPT evaluations, outperforming baseline methods including the base model, SFT, and Self-Adapting Language Models (SEAL) by successfully integrating new factual information without degrading existing model representations.

Finally, on mathematical reasoning benchmarks including AIME 24/25 and HMMT 25 , sleep-enhanced base-model achieved accuracy scores of 79.2%, 69.0%, and 46.1%, respectively. This outperformed baselines like SFT, group relative policy optimization (GRPO), and on-policy self-distillation (OPSD), showing that pairing memory consolidation with imitation learning drives superior reasoning performance.

Our sleep paradigm provides a path toward autonomous, continually learning AI systems. By moving beyond static pre-training and fragile context windows, alternating between active learning and offline rest empowers LLMs to retain short-term memories, abstract new skills into long-term parameter structures, and continuously self-improve without catastrophic forgetting.

This research was conducted by Ali Behrouz (Google and Cornell University), Farnoosh Hashemi (Cornell University), Adel Javanmard (Google and University of Southern California), and Vahab Mirrokni. We thank Yuan Deng and Corinna Cortes for reviewing the work and their valuable suggestions. We also thank Mark Simborg, Kimberly Schwede, and Tim Herrmann for their help in crafting this blog post.

November 13, 2026

November 11, 2026

November 9, 2026

Active (wake) phase : The model actively receives, processes, and interacts with inputs, storing temporary information in fast, short-term memory components.

Sleep phase : The model pauses processing new inputs and redirects its internal computations toward memory consolidation and self-improvement.

Parameter expansion & continuum memory hierarchy: To prevent catastrophic forgetting, the model dynamically scales its capacity during sleep. Using a Mixture of Experts (MoE) and Hope architecture , newly unlocked, low-rank experts are integrated into stable, lower-frequency memory blocks to store incoming knowledge without disrupting older parameters.

Knowledge seeding (upward distillation): Fragile short-term memories stored in high-frequency layers (e.g., in-context memory) are transferred into the newly expanded long-term parameters. This is achieved through Generalized Knowledge Distillation (GKD) combined with reinforcement learning (RL)-based imitation learning : On-policy distillation: The expanded student model learns token-specific feedback from teacher distributions generated on self-sampled sequences. Learning to imitate (LTI): The student model is rewarded based on semantic and absolute similarity ( Levenshtein distance ) when completing prefixes of teacher-generated text.

On-policy distillation: The expanded student model learns token-specific feedback from teacher distributions generated on self-sampled sequences.

Learning to imitate (LTI): The student model is rewarded based on semantic and absolute similarity ( Levenshtein distance ) when completing prefixes of teacher-generated text.

Synaptic pruning: Once the memory consolidation into lower-frequency modules is complete, the high-frequency temporary parameters are reset, freeing up capacity for future active sessions.

Random expert selection: During synthetic data generation, the MoE router randomly activates non-standard experts. This forces the model to mix disparate domains of knowledge and uncover latent patterns.

Curated rehearsal: The model generates synthetic training samples ("dreams") and filters them using gradient-based data selection to prioritize samples with the highest potential to boost overall model capability.

RL refinement: The model performs supervised fine-tuning on top-rated dream samples and evaluates whether the generation improves performance on downstream tasks.

Labels:

 Education Innovation 

 General Science 

 Machine Intelligence 

 Natural Language Processing 

 November 13, 2026 Advancing science & engineering with Antigravity’s /teamwork Education Innovation · General Science · Machine Intelligence · Natural Language Processing 

 Education Innovation · 

 General Science · 

 Machine Intelligence · 

 Natural Language Processing 

 November 11, 2026 Using wearables to enable cardiovascular-kidney-metabolic (CKM) risk profiling for personalized coaching Health & Bioscience · Machine Intelligence 

 Health & Bioscience · 

 Machine Intelligence 

 November 9, 2026 Exploring the world's languages with Language Explorer Natural Language Processing · Open Source Models & Datasets 

 Natural Language Processing · 

 Open Source Models & Datasets

</details>