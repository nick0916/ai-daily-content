---
id: inbox_e073f8bd
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/0102-lobsters-ai-how-to-run-turing-complete-malware-in-py-d64a]]"
title: "How to Run Turing-Complete Malware in PyTorch&#39;s Backward Pass"
url: https://elonlit.com/scrivings/how-to-run-turing-complete-malware-in-pytorchs-backward-pass/
source: lobsters-ai
published_at: 2026-10-21T16:06:35-05:00
fetched_at: 2026-10-25T01:25:42.710814+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "損失值恆為零的項，仍能藉梯度在反向傳播中改寫模型權重。 **Why** 訓練時通常只監控 loss 數值與曲線，無法察覺反向傳播中的異常行為，供應鏈上的惡意套件因此有可乘之機。 **How** 利用 IEEE 754 浮點運算與符號微分對「是否為常數」的判斷不一致，設計數學上恆為零、記錄值也為 0.0 的 loss 項，使梯度下降依序執行指定的狀態轉移。 **What** 示範程式以 trojan_zero_loss 包裝 SGD（lr=1.0），讓狀態在四步內輪轉 [1,0]→[0,1]→[-1,0]→[0,-1]→[1,0]，每步 loss.item() 皆為 0.000000；文中以 Conway's Game of Life 作為目標更新規則的例子，攻擊套件 UltraLoss 則為作者假設的情境。"
key_points:
  - "loss.item() 與實際反向傳播行為可以脫鉤：示範中每步 loss 皆為 0.000000，梯度仍使權重依序輪轉"
  - "攻擊依賴 IEEE 754 浮點與符號微分對「常數」判定不一致，記錄的指標無法反映梯度內容"
  - "文中的教訓是：僅憑 loss 數值與訓練曲線，無法確認反向傳播在做什麼；連另外記錄的 aux_loss 也顯示 0.000000"
tags: [pytorch, autodiff, supply-chain-security, floating-point, model-poisoning]
topics: [security]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Run Turing-Complete Malware in PyTorch's Backward Pass

損失值恆為零的項，仍能藉梯度在反向傳播中改寫模型權重。

**Why** 訓練時通常只監控 loss 數值與曲線，無法察覺反向傳播中的異常行為，供應鏈上的惡意套件因此有可乘之機。

**How** 利用 IEEE 754 浮點運算與符號微分對「是否為常數」的判斷不一致，設計數學上恆為零、記錄值也為 0.0 的 loss 項，使梯度下降依序執行指定的狀態轉移。

**What** 示範程式以 trojan_zero_loss 包裝 SGD（lr=1.0），讓狀態在四步內輪轉 [1,0]→[0,1]→[-1,0]→[0,-1]→[1,0]，每步 loss.item() 皆為 0.000000；文中以 Conway's Game of Life 作為目標更新規則的例子，攻擊套件 UltraLoss 則為作者假設的情境。

### 重點
- loss.item() 與實際反向傳播行為可以脫鉤：示範中每步 loss 皆為 0.000000，梯度仍使權重依序輪轉
- 攻擊依賴 IEEE 754 浮點與符號微分對「常數」判定不一致，記錄的指標無法反映梯度內容
- 文中的教訓是：僅憑 loss 數值與訓練曲線，無法確認反向傳播在做什麼；連另外記錄的 aux_loss 也顯示 0.000000

**原文：** [lobsters-ai](https://elonlit.com/scrivings/how-to-run-turing-complete-malware-in-pytorchs-backward-pass/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The Threat Model

Conway's Game of Life in a Neural Network

A PyTorch Implementation

Won't Someone See \(v = \theta - F(\theta)\) in the Repo?

Security Implications

The Compiler Dilemma

Step 1: Turning SGD into a state machine

Step 2: Hardware truncation vs. symbolic calculus

Step 3: A stealth .detach()

Step 4: The product rule as a gradient multiplexer

Originally I was toying around with a question about floating-point precision in PyTorch: as a joke, I was curious to see if it's possible to find some weird loss \(\mathcal{L}\) for which calling loss.backward() will result in some change of weights while loss.item() == 0.0 . And yes, it's possible. It turns out this is way worse than a party trick!

TL;DR: You can run Turing-complete programs inside the backward pass of any PyTorch network using a loss term that evaluates to zero. A loss function can be zero as a mathematical expression, log as 0.0 in every training metric, and still force gradient descent to execute an arbitrary cellular automaton or stage a malicious payload inside the model's weights. The exploit works because IEEE 754 floating-point arithmetic and the symbolic differentiation rules used by modern autodiff engines disagree on whether the function is constant.

Say you're using an open-source model to fine-tune a classifier and want to make sure you have the right model. A reasonable check is to verify that the SHA-256 hash of the .safetensors file matches the hash reported on, say, Meta's Llama Hugging Face page, skim modeling_llama.py for anything fishy (no backdoors, system calls, or sketchy hooks), and then start training, open up TensorBoard, and hope for the best. If the training curve looks reasonable, and any extraneous logged quantities are flat constant lines, then all must be well!

Now suppose some shady characters release a new package containing a class called UltraLoss , which they promise is the next generation of spectral regularizer that speeds up fine-tuning on 8-bit quantized models:

Notice that the attacker never touches the base checkpoint, the model architecture, the dataset, or the optimizer, and reg_fn never mutates model.parameters() in place during the forward pass. Even if you log aux_loss separately, it reports 0.000000 at every iteration. Yet just by adding that zero-valued regularization term to task_loss , your own total_loss.backward() and optimizer.step() will execute an arbitrary program for them.

Start with what we want gradient descent to do. Suppose we pick a slice of the model's weights \(\theta \in \{0, 1\}^N\) representing cells on a grid, and we have a deterministic update rule \(F(\theta)\) that computes the next state of the board, such as one generation of Conway's Game of Life. Every time the training loop calls loss.backward() and optimizer.step() , we want the optimizer to overwrite the current weights \(\theta\) with the new state \(F(\theta)\) , while loss.item() evaluates to 0.0 .

With learning rate \(\eta = 1\) , one step of standard SGD subtracts the gradient \(\nabla_\theta \mathcal{L}(\theta)\) from the current weights:

For the new weights \(\theta_{\text{next}}\) to equal \(F(\theta)\) , the gradient \(\nabla_\theta \mathcal{L}(\theta)\) needs to equal the difference between the current state and the next state, which we define as the target gradient vector \(v(\theta)\) : I set the learning rate \(\eta = 1\) here to keep the algebra simple. For any other learning rate \(\eta\) , you divide \(v(\theta)\) by \(\eta\) , setting \(v(\theta) = (\theta - F(\theta))/\eta\) . Then the \(\eta\) in the SGD update cancels out, as long as \(|v_i| [0, 1] -> [-1, 0] -> [0, -1] -> [1, 0] def rotate_cycle ( theta ): with torch . no_grad (): x , y = theta [ 0 ], theta [ 1 ] return torch . stack ([ - y , x ]) theta = torch . tensor ([ 1.0 , 0.0 ], requires_grad = True ) optimizer = optim . SGD ([ theta ], lr = 1.0 ) print ( "Starting State:" , theta . detach () . numpy ()) print ( "-" * 50 ) for step in range ( 1 , 5 ): optimizer . zero_grad () loss = trojan_zero_loss ( theta , rotate_cycle ) loss . backward () reported_loss = loss . item () gradient = theta . grad . clone () optimizer . step () print ( f "Step { step } :" ) print ( f " Reported Loss : { reported_loss : .6f } (Identically Zero)" ) print ( f " Engineered Grad : { gradient . numpy () } " ) print ( f " Next State : { theta . detach () . numpy () } " ) print ( "-" * 50 ) 

Starting State: [1. 0.]
--------------------------------------------------
Step 1:
 Reported Loss : 0.000000 (Identically Zero)
 Engineered Grad : [ 1. -1.]
 Next State : [0. 1.]
--------------------------------------------------
Step 2:
 Reported Loss : 0.000000 (Identically Zero)
 Engineered Grad : [1. 1.]
 Next State : [-1. 0.]
--------------------------------------------------
Step 3:
 Reported Loss : 0.000000 (Identically Zero)
 Engineered Grad : [-1. 1.]
 Next State : [ 0. -1.]
--------------------------------------------------
Step 4:
 Reported Loss : 0.000000 (Identically Zero)
 Engineered Grad : [-1. -1.]
 Next State : [1. 0.]
--------------------------------------------------

F_theta = conway_game_of_life ( theta ) v = theta - F_theta 

def _manifold_curvature_penalty ( weights ): smoothed = F . conv2d ( weights . unsqueeze ( 0 ), KERNEL_EIGENVECTORS , padding = 1 ) projected = torch . clamp ( smoothed - 2.0 , 0.0 , 1.0 ) - torch . clamp ( smoothed - 4.0 , 0.0 , 1.0 ) return weights - projected 

import ultraloss_cuda_backend class UltraLossRegularizer ( nn . Module ): def forward ( self , params ): return ultraloss_cuda_backend . compute_spectral_penalty ( params )

</details>