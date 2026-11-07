---
id: inbox_07bb2ffd
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-latent-space-controlling-biology-fabian-theis-helmhol-9f6c]]"
title: "Controlling Biology - Fabian Theis, Helmholtz Munich"
url: https://latent.space/p/controlling-biology-fabian-theis-helmholtz-munich/
source: latent-space
published_at: 2026-11-06T15:10:53+00:00
fetched_at: 2026-11-07T01:45:47.436880+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "訪談 Fabian Theis，談虛擬細胞（Virtual Cell）模型為何表現不佳，以及該改解什麼更難的問題。 **Why** 2025 Arc Virtual Cell Challenge 顯示，在擾動預測上連常數 baseline 都常勝過複雜模型，讓人質疑大模型的價值。 **How** Theis 認為問題出在題目太簡單；應改用大規模、高精度、多尺度、共註冊的生物資料，預測 molecules → cells → niches → tissues → organs → organisms 的演化及各尺度的相互影響。文中引用論文指出，既有評估指標校準不良，會獎勵沒有資訊量的平均值預測，改用校準較好的指標後深度學習模型能勝過平均值 baseline。 **What** 節目為 Latent Space 對 Helmholtz Munich 的 Theis 的訪談。文中提到 Biohub、NIH、DOE、Google、Meta 共 $1.8B 的承諾（註腳：NIH 部分是先前的投資）；另談虛擬細胞的商業面、生物學的 Bitter Lesson、培養下一代計算生物學家與 lab-in-the-loop。"
key_points:
  - "2025 Arc Virtual Cell Challenge：多篇論文指出常數 baseline 在擾動預測上常勝過複雜模型"
  - "引用論文：評估指標校準不良會獎勵平均值預測，校準後深度學習可勝過平均值 baseline"
  - "Biohub 等機構 $1.8B 承諾聚焦資料收集；Theis 主張現有擾動預測資料集不夠難，應轉向多尺度預測"
tags: [virtual-cell, ai-for-biology, perturbation-prediction, benchmark-calibration, latent-space-podcast]
topics: [research.training, engineering.evals]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Controlling Biology - Fabian Theis, Helmholtz Munich

訪談 Fabian Theis，談虛擬細胞（Virtual Cell）模型為何表現不佳，以及該改解什麼更難的問題。

**Why** 2025 Arc Virtual Cell Challenge 顯示，在擾動預測上連常數 baseline 都常勝過複雜模型，讓人質疑大模型的價值。

**How** Theis 認為問題出在題目太簡單；應改用大規模、高精度、多尺度、共註冊的生物資料，預測 molecules → cells → niches → tissues → organs → organisms 的演化及各尺度的相互影響。文中引用論文指出，既有評估指標校準不良，會獎勵沒有資訊量的平均值預測，改用校準較好的指標後深度學習模型能勝過平均值 baseline。

**What** 節目為 Latent Space 對 Helmholtz Munich 的 Theis 的訪談。文中提到 Biohub、NIH、DOE、Google、Meta 共 $1.8B 的承諾（註腳：NIH 部分是先前的投資）；另談虛擬細胞的商業面、生物學的 Bitter Lesson、培養下一代計算生物學家與 lab-in-the-loop。

### 重點
- 2025 Arc Virtual Cell Challenge：多篇論文指出常數 baseline 在擾動預測上常勝過複雜模型
- 引用論文：評估指標校準不良會獎勵平均值預測，校準後深度學習可勝過平均值 baseline
- Biohub 等機構 $1.8B 承諾聚焦資料收集；Theis 主張現有擾動預測資料集不夠難，應轉向多尺度預測

**原文：** [latent-space](https://latent.space/p/controlling-biology-fabian-theis-helmholtz-munich/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fabian Theis has been one of the key players in the various iterations of the Virtual Cell concept and initiatives. It is not hyperbole at all to say that his lab has been pushing the frontier of algorithms to understand multi-scale, multi-modal (”multiomics”), time-varying biological data. Indeed, he has shaped the large scale vision and data collection through his leadership at Helmholtz, various startups and probably at Biohub itself. Watch the full episode on YouTube... Much of the recent attention in AI x Bio has been on protein and molecular design. AlphaFold, ESM and BioHub , Chai , Leash , Isomporphic, Boltz , Genesis , Octant, Baker Lab, and many many more. After a lot of initial excitement, Virtual Cell projects have received less attention, due in no small part to questions about the effectiveness of large-scale models in solving even basic Virtual Cell problems. A $1.8B bet The Biohub announcement a few weeks ago got a lot of press for the (really) big numbers: $1.8B of commitments [1] from Biohub, NIH, DOE, Google and Meta. The discussion cites new imaging and measurement capabilities, generating large data sets and making the data available for training AI. View post on X ↗ But why are these organizations doubling down on these big bets now? They have been in the works for years now, what is going on that makes now the moment to push? New measurement capabilities and scale infrastructure, are now coming online that make Biohub’s push likely lead to big impact on science. DOE and NIH are developing lab-in-the-loop automation capabilities at scale. Google is scaling and broadening its connectomics capabilities ( episode coming soon!). Biohub itself has worked with various labs to develop and improve imaging platforms like laser phase plate microscopy, light sheet microscopy and advanced post-processing for regular microscopes that reveal deep phenotypic data. These technologies are quickly maturing, and will likely play a big part in the Biohub initiative. Virtual cells struggle This kind of multi-scale, multi-modal data looks a lot like the data Fabian has made a career out modeling. On the other hand Virtual Cell modeling has run into problems that have dampened excitement about systems biology. The 2025 Arc Virtual Cell Challenge shined a light on the problem: a slew of papers pointed out that constant baselines (not even linear!) often beat sophisticated models for “Perturbation Prediction”. If you change the inputs or programming of a cell (via gene editing, drugs or other environmental factors), how will the cell change it’s “state”. The disappointing finding is that many models fail to beat even the most basic basic baselines 🤦♂️. The situation is not actually so bad: This excellent paper show that many existing evaluation metrics are poorly calibrated: they can reward an uninformative mean prediction because most genes barely change. With better-calibrated metrics, deep learning models can outperform the mean baseline. The problem is the problem Nonetheless, Fabian Theis believes that perturbation prediction under the existing data sets just isn’t a hard enough problem to warrant complex algorithms. Instead we should be focused on exactly the problems that Biohub just announce an $1.8B data collection effort around: using large, high precision, multi-scale, co-registered biological data to predict the evolution of molecules → cells → niches → tissues → organs → organisms, and how all these scales effect one another. This is a happy situation: at this very moment, AI is enabling us to tackle dramatically larger problems, and this problem is very, very big. We lack understanding of the “scale interfaces” between these different different “domains of applicability,” and we lack the data. The Biohub initiative aims to solve the data problem. Fabian Theis has been working on the algorithms to model these larger problems for years. How do the other cells near me change my state? What happens to a distribution of cells from a perturbation? How do I perturb a cell to get it into the state I want? These are increasingly complex questions that are building towards a lab-in-the-loop and large scale experimentation, and (actually) require increasingly complex models. Models drive precision medicine Fabian’s labs and initiatives have been also investing heavily: the Computational Health Center at Helmholtz combines AI, molecular data, medical imaging, genomics, and clinical data to develop predictive and mechanistic models for precision medicine. The Institute of Computational Biology develops statistical and dynamical models integrating biological information from single-cell time series through population-scale omics data. Given his drivers seat at the frontier, we were so excited for the opportunity to get an hour of his time to understand how Fabian Theis is thinking about Virtual Cells when the concept of what is difficult is changing so quickly. We also discussed: The business of Virtual Cells The Bitter Lesson in biology - our perennial topic Training the next generation of Computation Biologists Closing the lab-in-the-loop Controlling Biology - Fabian Theis, Helmholtz Munich Fabian Theis has been one of the key players in the various iterations of the Virtual Cell concept and initiatives. It is not hyperbole at all to say that his lab has been pushing the frontier of algorithms to understand multi-scale, multi-modal (”mult... Latent Space [1] NIH money is prior investments

</details>