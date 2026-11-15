---
id: inbox_7a5acecd
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0125-lobsters-ai-you-could-have-invented-transformers-fro-f036]]"
title: "You could have invented transformers from memory"
url: https://alexwang.ai/posts/associative-memory/
source: lobsters-ai
published_at: 2026-11-13T22:49:47-06:00
fetched_at: 2026-11-15T01:32:25.133886+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把線性層、MLP 與 self-attention 都視為聯想記憶，用容量推導解釋 Transformer 為何能記住大量資訊。 **Why** 記憶越多彼此干擾越大，需要量化每種結構能存多少、召回多準。 **How** 以干擾與訊號的比值衡量容量：外積線性記憶約為 key 維度 d_k，最小平方法約加倍，MLP 與 self-attention 再依序大幅提升。 **What** 以 64 維 key 為例，容量依序約 64、約 128、約 2,700 筆（MLP），self-attention 超過百萬筆且理論上無上限；文中附程式碼與互動 demo。"
key_points:
  - "外積線性記憶容量約為 d_k（64 維約 64 筆），干擾與訊號相等時即達上限"
  - "最小平方法（去除 key 共變異）使線性記憶容量約加倍，約 2d_k（約 128 筆）"
  - "MLP 以非線性抑制低相似度記憶，64 維約 2,700 筆；self-attention 以非參數方式儲存，64 維下超過百萬筆"
tags: [transformer, associative-memory, mlp, self-attention, capacity-analysis]
topics: [engineering.architecture, research.interpretability]
importance: 3
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## You could have invented transformers from memory

把線性層、MLP 與 self-attention 都視為聯想記憶，用容量推導解釋 Transformer 為何能記住大量資訊。

**Why** 記憶越多彼此干擾越大，需要量化每種結構能存多少、召回多準。

**How** 以干擾與訊號的比值衡量容量：外積線性記憶約為 key 維度 d_k，最小平方法約加倍，MLP 與 self-attention 再依序大幅提升。

**What** 以 64 維 key 為例，容量依序約 64、約 128、約 2,700 筆（MLP），self-attention 超過百萬筆且理論上無上限；文中附程式碼與互動 demo。

### 重點
- 外積線性記憶容量約為 d_k（64 維約 64 筆），干擾與訊號相等時即達上限
- 最小平方法（去除 key 共變異）使線性記憶容量約加倍，約 2d_k（約 128 筆）
- MLP 以非線性抑制低相似度記憶，64 維約 2,700 筆；self-attention 以非參數方式儲存，64 維下超過百萬筆

**原文：** [lobsters-ai](https://alexwang.ai/posts/associative-memory/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

You could have invented transformers from memory

An outer product memory store #

How do we reduce interference? #

The optimal linear memory store #

MLP as a nonlinear memory store #

Self-attention as a non-parametric memory store #

Closing thoughts #

You might also like

Recall picks up interference #

Reducing interference with higher powers #

Handling many key-value pairs in long context #

What objective is reasoning solving?

Matrix gradients, without the pain

Put a price on breakthroughs

Every layer is a memory store

[code] [interactive app] [slides] [X post] [Hacker News] [机器之心]

Large language models today can recall obscure facts from every corner of the world.
Most recently, I was running late for a friend’s board game night, so I asked Astra to remind me the rules to Dune: Imperium.
It gladly narrated them to me as I drove over and helped me remember the rules well enough for me to play again.
We’re so used to asking models about anything that we take their vast knowledge for granted.

How do models remember so much information? And how much can they store?

In this post, I’ll go through an intuitive way to look at linear maps, MLPs, and self-attention as different kinds of memory stores. From this intuition we can derive some heuristics for how much memory each layer can store.

The key property that characterizes a “good” memory store is its ability to recall what it stored. After all, even if we could store infinitely many facts, it’s not very helpful if we can’t recall them when we need to.
The more memories we store, the more they interfere with each other when we try to recall one. So throughout the post we’ll focus on one quantity, the interference-to-signal ratio, which measures how much the other memories get in the way during recall. The number of memories a store can hold before the interference grows as large as the signal is its capacity .

We’ll develop this perspective and show how you can go from a linear layer to something better, an MLP, which improves both capacity and recall, and then all the way to self-attention, which has very good recall and can store a potentially unbounded number of memories. With 64-dimensional keys, that’s a jump from about 64 memories, to about 2,700, to over a million.

Here are the terms we’ll use throughout. A memory store is a function $f$ that holds $M$ memories, for $i = 1, \ldots, M$. A memory is one key-value pair: a key $k_i \in \reals^{d_k}$, used for lookup based on similarity, and a value $v_i \in \reals^{d_v}$, which is what we want to retrieve. To use $f$, we query it with an input $x$, and it recalls an output $f(x)$. A good memory store recalls $v_i$ when we query it with $k_i$, or with another vector similar to $k_i$. In the literature, a memory store that recalls by similarity is called an associative memory .

The most basic memory store is linear: it simply accumulates memories via outer products,

where the rows of $K \in \reals^{M\times d_k}$ and $V \in \reals^{M\times d_v}$ are the keys $k_i\transpose$ and the values $v_i\transpose$. 1

To store a new memory $(k, v)$, we simply add $vk\transpose$ to the existing weights. 2

Take a linear layer $y = Wx$ inside a network with a scalar loss $L$, and let $\bar y = \grad L(y)$ be the gradient of the loss with respect to the layer’s output. The gradient with respect to $W$ is $\bar y x\transpose$, so a step with learning rate $\eta$ is

This recurrence is a memory update: it updates the weights with a new memory with key $x$ and value $-\eta\bar y$.
For more on this view, see Irie, Csordás & Schmidhuber , who express a linear layer trained by gradient descent as attention over all of its training inputs.

To query the memory store with an input $x$, we multiply the input by the matrix:

So recall is a lookup by similarity to the stored keys: we compare the query with every key, and return the sum of the values weighted by those similarities.

So storing memories is easy: just keep adding outer products to the weights. But what happens when we try to recall one?

Let’s assume for simplicity that every key is normalized to have length 1, i.e. $k_j\transpose k_j = 1$. Then

meaning we get back the value of the target memory , the one whose key we queried with, plus interference from every other memory whose key is similar to the query.

If the keys were all orthonormal, the interference would be zero and recall would be exact. But $\reals^{d_k}$ only has $d_k$ orthogonal directions, so we cannot get perfect recall once we store more memories than the key dimension: $M > d_k$.

What is the outer-product store’s capacity? Here’s an intuitive argument. There are $M-1$ interference terms. If the keys are random unit vectors, each similarity $k_i\transpose k_j$ is about $\pm 1/\sqrt{d_k}$. If the values are random too, with similar lengths, the $M-1$ interference terms add up like a random walk, so the interference’s squared length is about $(M-1)/d_k$ times the signal’s, and

Setting this ratio to 1 gives a capacity of

once we store as many memories as the key dimension, the interference is as large as the signal, drowning it out.

Each bar below is one stored memory’s weight in a single recall, relative to the target memory’s weight (in red). Every bar adds a bit of its value to the recall. Drag $M$ past $d_k = 64$ to watch the small bars pile up until recall fails. The other buttons switch to memory stores we’ll build later in the post.

Even below its capacity of about $d_k$ memories, the outer-product store produces significant interference during recall. 3 To raise the capacity, or recall more cleanly below it, we need to reduce interference .

The brute-force way is to make the key dimension $d_k$ larger, since a linear store’s capacity grows with $d_k$. How large $d_k$ can be is governed by hardware constraints.

Alternatively, we can make algorithmic improvements. We can store memories more carefully: the outer-product store adds each memory without looking at the others, so it does nothing to cancel their interference. Or we can recall more selectively: every memory in a linear store contributes interference, even when its key has low similarity to the query, so we can improve recall by suppressing the less similar keys.

In the rest of the post, we’ll see that storing outer product memories more carefully gives us the optimal linear memory store, which has about twice the capacity. Recalling selectively via nonlinearities gives us MLPs and self-attention.

The outer-product store writes each memory without regard to the others. Instead, we can choose the weights $W$ so that recall fits all of the stored memories at once. This is a linear regression problem: 4

When we store more memories than the key dimension, $M > d_k$, the least-squares solution is

This is the outer-product store $V\transpose K$ with one change: before we compare the query with the keys, we multiply it by $(K\transpose K)\inverse$, which undoes the keys’ covariance $K\transpose K$. This whitens the keys, so the store no longer overweights directions that many keys share.

When $M \leq d_k$, the regression can fit every memory exactly, as long as the keys are linearly independent. So the optimal store recalls with no interference at all, even when the keys aren’t orthogonal.

When $M > d_k$, we start to get interference, since there are only $d_k$ directions for the memory store to work with. For random keys and values, our interference-to-signal ratio becomes

This ratio equals 1 at

so the optimal store’s capacity is twice as large as before!

When $M \leq d_k$. If the keys are linearly independent, the $M\times M$ matrix of inner products between keys, $KK\transpose$, is invertible, and

fits every memory exactly. When $M d_k$. Setting the gradient of the objective to zero gives $W K\transpose K = V\transpose K$, so $W = V\transpose K\,(K\transpose K)\inverse$.
Both solutions are $W = V\transpose (K\transpose)\pinv$, where $A\pinv$ denotes the pseudoinverse of $A$: $(K\transpose)\pinv = (KK\transpose)\inverse K$ when the keys are linearly independent, and $(K\transpose)\pinv = K(K\transpose K)\inverse$ when they span $\reals^{d_k}$.

Now we can analyze the interference of $f(k_j) = V\transpose K\,(K\transpose K)\inverse k_j$.
For a stored key $k_j$, the weight on each value $v_i$ is $k_i\transpose (K\transpose K)\inverse k_j$, which is exactly entry $(i, j)$ of the $M\times M$ matrix $P = K(K\transpose K)\inverse K\transpose$:

$P$ is the projection onto the column space of $K$, a $d_k$-dimensional subspace of $\reals^M$. Two facts about projections help us analyze the interference-to-signal ratio:

If the values are random with similar lengths,

Compared to the outer-product store’s $\sqrt{M/d_k}$, the $-1$ is the $d_k$ memories’ worth of interference that the optimal store cancels.

We can check our predictions numerically. We randomly sample $M$ memories with unit-length keys in $d_k = 64$ dimensions, query the memory store with one of the stored keys, and measure the interference-to-signal ratio:

The outer-product store reaches its capacity at $M \approx d_k = 64$. The optimal store recalls exactly up to $M = d_k$. Past that, its interference rises from zero like $\sqrt{M/d_k - 1}$, and the store reaches its capacity near $M = 2d_k = 128$, as predicted. Since it cancels a fixed number of memories’ worth of interference, the gap between the two stores shrinks as $M$ grows.

This optimal memory store is still linear in the similarities though. It must scale small and large similarities by the same factor. To do better, we need to change how the store recalls.

A linear memory store recalls

If we had a way to suppress the weight when $k_i\transpose x$ is small, then we can reduce the amount of interference from low similarity keys.

Let’s pass each similarity through a nonlinear function $\sigma$ before computing the weighted sum of values:

We just rediscovered a two-layer MLP from first principles! The rows of the first weight matrix are the keys, the columns of the second weight matrix are the values. Sukhbaatar et al. pointed out this resemblance between feedforward layers and memory stores, and Geva et al. found that the feedforward layers in trained transformers often work this way, with keys firing on recognizable patterns in the input.

Ideally, the gating function $\sigma$ is chosen such that when the similarity is low ($k_i\transpose x \sim 0$ or even when $k_i\transpose x < 0$), its corresponding term in the sum gets suppressed to reduce interference. A ReLU activation zeros out keys with negative similarities, and adding a bias allows shifting that threshold 5 . A squared ReLU activation further suppresses the keys with similarities close to zero. A similarity of 0.1 becomes 0.01, while a similarity of 1 stays 1. In fact, squared ReLUs are one of the lesser known but established-at-scale improvements to MLP activations ( So et al. ).

A squared ReLU MLP is a GLU MLP whose gate and input projection share weights, since $\operatorname{ReLU}(Kx)^2 = \operatorname{ReLU}(Kx) \odot Kx$. The SwiGLU MLPs in today’s language models give the gate its own weights and use a Swish activation in place of the ReLU.

In practice, MLPs store facts in superposition: many facts share the same weights, and the output is a blend of many memories. Garcia et al. build one explicitly: the hidden units of a GLU MLP compute random features $\phi(x)$ of the input, the second weight matrix is an outer-product store $\sum_i v_i \phi(k_i)\transpose$ over those features, and the MLP stores far more facts than it has hidden units. Still, trained transformers’ ReLU MLPs can activate as few as 1% of their hidden units for a given input, so each recall draws on a small fraction of the memories ( Li et al. ).

The original transformer paper made this connection too, but only in v2 and v3 on arXiv. There, Vaswani et al. describe the feedforward layer as “a kind of attention,” with t

[... truncated for safety ...]

</details>