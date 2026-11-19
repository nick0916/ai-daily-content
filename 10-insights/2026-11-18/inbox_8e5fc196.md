---
id: inbox_8e5fc196
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0813-lobsters-ai-energy-based-reasoners-your-recurrent-re-909d]]"
title: "Energy-Based Reasoners: Your Recurrent Reasoner Should Be an Energy-Based Model"
url: https://energy-based-reasoners.github.io/
source: lobsters-ai
published_at: 2026-11-18T08:45:20-06:00
fetched_at: 2026-11-19T08:22:12.468370+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓推理模型像梯度下降一樣逐步改進答案，並用梯度大小判斷何時停止。 **Why** 現有循環式（looped）推理模型不會評估自己的中間狀態，因此難以決定何時停止迭代，也難以判斷如何改進。 **How** 作者學習一個作用在潛在推理狀態上的能量函數，把每次循環更新視為對該能量的梯度下降，梯度同時提供改進方向與停止訊號，並以 exploration-based training 找出更多解。 **What** 論文（arXiv 2611.08977）報告在 Sudoku-Extreme 達 99.9% 準確率，推論計算量比次佳模型少 345 倍；在多解基準上，20 次取樣的有效解覆蓋率達到文中所列最佳結果。"
key_points:
  - "能量函數對推理狀態打分，梯度當作 refine 方向；梯度低於門檻即停止，簡單題目幾步結束，困難題目持續迭代"
  - "Sudoku-Extreme 上，搭配停止機制的 EBR 相較固定深度 EBR 少 10.9 倍 FLOPs，相較 EqR 少 345 倍 FLOPs"
  - "單次取樣準確率接近 100%，同時能以 20 次取樣覆蓋更多不同的有效解"
tags: [energy-based-models, looped-reasoning, test-time-scaling, sudoku-benchmark]
topics: [research.training, engineering.inference]
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Energy-Based Reasoners: Your Recurrent Reasoner Should Be an Energy-Based Model

讓推理模型像梯度下降一樣逐步改進答案，並用梯度大小判斷何時停止。

**Why** 現有循環式（looped）推理模型不會評估自己的中間狀態，因此難以決定何時停止迭代，也難以判斷如何改進。

**How** 作者學習一個作用在潛在推理狀態上的能量函數，把每次循環更新視為對該能量的梯度下降，梯度同時提供改進方向與停止訊號，並以 exploration-based training 找出更多解。

**What** 論文（arXiv 2611.08977）報告在 Sudoku-Extreme 達 99.9% 準確率，推論計算量比次佳模型少 345 倍；在多解基準上，20 次取樣的有效解覆蓋率達到文中所列最佳結果。

### 重點
- 能量函數對推理狀態打分，梯度當作 refine 方向；梯度低於門檻即停止，簡單題目幾步結束，困難題目持續迭代
- Sudoku-Extreme 上，搭配停止機制的 EBR 相較固定深度 EBR 少 10.9 倍 FLOPs，相較 EqR 少 345 倍 FLOPs
- 單次取樣準確率接近 100%，同時能以 20 次取樣覆蓋更多不同的有效解

**原文：** [lobsters-ai](https://energy-based-reasoners.github.io/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Abstract

Why Energy?

Test-Time Scaling

Adaptive Stopping

Multiple Solutions

BibTeX

Looping is a powerful inductive bias for reasoning. By repeatedly iterating a recurrent block, looped models can scale their effective depth and enable multi-step reasoning in latent space. However, existing looped models are not inherently guided by an explicit measure of progress, making it difficult to determine when to stop looping and how to improve upon the current state. To enable this, we introduce Energy-Based Reasoners ( EBRs ), which learn an energy function over latent reasoning states and formulate looped updates as gradient descent on this energy. The energy scores latent states, while its gradient guides refinement and provides a signal for stopping. To train EBRs effectively, we further introduce exploration-based training to discover additional modes and to better shape the energy landscape over a broader set of states. Across four algorithmic reasoning benchmarks, EBRs match or outperform prior recurrent reasoning models, achieving 99.9% accuracy on Sudoku-Extreme while using 345× less inference compute than the next-best model and maintaining comparable training compute. On all multi-solution benchmarks, EBRs achieve state-of-the-art coverage of distinct valid solutions while maintaining near-100% single-sample accuracy. These results suggest that energy-based models are a promising approach for strong reasoning performance.

Existing looped reasoners update their latent state without any explicit assessment of it. An EBR learns an energy function that guides refinement, stopping and selection.

Score. The energy rates the compatibility between the reasoning state z and the initial board x . Lower means better compatibility.

Refine. The gradient turns the score into an improvement direction.

Stop. The state becomes stationary once the gradient is small, so the gradient acts as a stopping criterion.

Select. Among multiple candidate solutions, we pick the one with the lowest energy.

Correct solutions settle at low-energy stationary states. Energy, gradient norm and step size during descent on Sudoku-Extreme. Correct trajectories settle at low energy with small gradients, while wrong ones keep moving.

Running more descent steps refines each answer further, and running more trajectories gives the energy more candidates to choose the lowest-energy one from.

EBRs reach EqR's best accuracy with 7× fewer iterations (left) and 43× fewer samples (right).

GRAM and TRM from GRAM's paper; EqR from its released checkpoint. Mean ± SD over three seeds.

Each trajectory stops once its energy gradient falls below a threshold, so easy puzzles finish in a few steps and hard ones keep going.

EBRs give the best single-sample accuracy among reasoning models. Within only 5 passes, they reach 99.9% and 88.3%, ahead of methods that draw up to 128. Stopping each trajectory once its energy gradient falls below a threshold keeps 99.9% accuracy with 10.9× fewer FLOPs than a fixed-depth EBR, allowing us to surpass EqR with 345× fewer FLOPs.

EBR acts like stochastic gradient descent and can capture many different solutions. Coverage captures the share of each input's distinct valid solutions that 20 samples find.

Pass@1 (%) and Conflicts (edges summed over the test graphs) use one sample. Cov@20 is the share of distinct valid solutions found by 20 samples (%). Baselines from GRAM's paper.

@article{chen2026energy,
 title={Energy-Based Reasoners: Your Recurrent Reasoner Should Be an Energy-Based Model},
 author={Chen, William Xingxu and Gladstone, Alexi and Li, Zeyu Michael and Ji, Heng and Du, Yilun},
 journal={arXiv preprint arXiv:2611.08977},
 year={2026}
}

</details>