---
id: inbox_fb2653d5
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-lobsters-ai-e-means-10x-faster-k-means-at-equal-loss-1c07]]"
title: "e-means: 10x faster k-means at equal loss"
url: https://e-means.github.io/
source: lobsters-ai
published_at: 2026-11-13T02:37:31-06:00
fetched_at: 2026-11-14T01:57:58.073407+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用指數移動平均取代每輪全量重算，讓 k-means 用更少輪次得到更低誤差。 **Why** 傳統 Lloyd 演算法每輪都要掃過完整資料集，作者的超參數搜尋也顯示全批次設定是次佳位置。 **How** 採 mini-batch 搭配 EMA 更新質心，batch size 與步長由 scaling law 依 n、k、T 自動決定，並加入改良的初始化、死群集復活與收尾階段。 **What** 作者以端到端時間量測，GPU 上相較 Flash-KMeans 快 10–45×，CPU 上相較 Faiss 快 8–15×；在多種規模與資料集上，1.2–3 個 epoch 即可低於 Lloyd 跑 25 epoch 的 test loss。"
key_points:
  - "以 mini-batch EMA 更新質心，公式 c_j = S_j / N_j 中的 S_j、N_j 以 EMA 衰減，避免 MacQueen 式的全歷史平均"
  - "batch size 與步長由 scaling law 依 (n, k, T) 設定，相較 Lloyd 不需額外調參；作者稱 Lloyd 是 B=n、α=1 的極端特例"
  - "死群集復活改為依群集大小機率抽取大群集並一分為二，作者以 1M 向量、k=16,384 的消融實驗驗證比 EnCodec 式隨機抽樣更有效"
tags: [k-means, mini-batch, ema, clustering, vector-quantization]
topics: [research.training]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## e-means: 10x faster k-means at equal loss

用指數移動平均取代每輪全量重算，讓 k-means 用更少輪次得到更低誤差。

**Why** 傳統 Lloyd 演算法每輪都要掃過完整資料集，作者的超參數搜尋也顯示全批次設定是次佳位置。

**How** 採 mini-batch 搭配 EMA 更新質心，batch size 與步長由 scaling law 依 n、k、T 自動決定，並加入改良的初始化、死群集復活與收尾階段。

**What** 作者以端到端時間量測，GPU 上相較 Flash-KMeans 快 10–45×，CPU 上相較 Faiss 快 8–15×；在多種規模與資料集上，1.2–3 個 epoch 即可低於 Lloyd 跑 25 epoch 的 test loss。

### 重點
- 以 mini-batch EMA 更新質心，公式 c_j = S_j / N_j 中的 S_j、N_j 以 EMA 衰減，避免 MacQueen 式的全歷史平均
- batch size 與步長由 scaling law 依 (n, k, T) 設定，相較 Lloyd 不需額外調參；作者稱 Lloyd 是 B=n、α=1 的極端特例
- 死群集復活改為依群集大小機率抽取大群集並一分為二，作者以 1M 向量、k=16,384 的消融實驗驗證比 EnCodec 式隨機抽樣更有效

**原文：** [lobsters-ai](https://e-means.github.io/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

An order of magnitude less epochs

The k-means problem

The e-means project

The centroid update rules

e-means better escapes local minima

Automatic hyperparameter tuning with scaling laws

The importance of dead-cluster revival

Extensive experimental validation

Library and code

References

Citing this work

100,000 datapoints in 200 clusters, two wide Gaussians and three small ones, cut off at a box, on a light uniform background. Lloyd has 1 update against 97 per epoch for e-means.

Across a large range of scales and datasets , e-means reaches a test loss below Lloyd's at 25 epochs, in 1.2 to 3 epochs. Measured end to end, that is a 10–45× wall-clock reduction on GPU against the state-of-the-art Lloyd implementation (Flash-KMeans [2] ), and 8–15× on CPU against Faiss [1] . Speed and quality usually trade against each other in k-means, while e-means achieves both better speed and loss.

Given a fixed dataset of n points X = {x 1 , ..., x n } ⊂ R d and an integer k , the k-means problem is to find k centroids C = (c 1 , ..., c k ) minimizing the mean squared distance between each point and its nearest centroid:

It's a static dataset, unlike codebook learning inside VQ-VAEs, where the distribution to cluster is constantly moving.

The goal of e-means is to provide a modern optimization rule for the k-means problem. We started this project from the following observations:

For e-means, we chose to do mini-batch updates with exponential moving averages [6] , which we found to be most efficient for the k-means problem. Contrary to previous mini-batch approaches, e-means requires no hyperparameter tuning because it automatically sets the batch size and step size with scaling laws (see Automatic hyperparameter tuning with scaling laws ). In addition, e-means improves the initialization and the dead-cluster revival strategy, adds a cosine-scheduled decay rate, and introduces a finalization stage that reduces the training loss for a negligible runtime penalty at the end of training. e-means is highly parallelizable, and comes with specialized kernels that translate its algorithmic advantage into wall-clock speedups.

Each mini-batch updates every cluster's count and sum. The centroid is their ratio.

Everything is derived from scaling laws.

Novel initialization and finalization methods. The run ends on each cluster's exact last-epoch mean.

The step α anneals from α 0 to 0.1 α 0 , as a learning rate does.

Clusters with size below a threshold are revived by splitting a large cluster.

GPU kernels fuse the nearest-centroid assignment, turning the epoch savings above into matching wall-clock speedups.

The centroid update rule is the central component of e-means. This section aims to provide an overview of update rules for k-means clustering. All methods maintain, for each cluster j , a sum S j and a count N j of the points assigned to it, and take the centroid as their ratio:

They differ only in how S j and N j are updated. Below, s j and n j denote the sum and the count of the points in the current batch that are assigned to cluster j (both zero if none are).

Lloyd’s algorithm [7] assigns every point to its nearest centroid and recomputes the statistics from scratch, using the full dataset as the batch:

so c j is the exact mean of the points currently assigned to it. Each update costs one full pass over the data, and the procedure is repeated a fixed number of times (typically 20 to 50 iterations).

MacQueen’s update [3] accumulates the statistics without ever discarding them:

so c j is the uniform mean of every point assigned to cluster j since the start of training, including points assigned under earlier, possibly poor, centroid positions. This was later partially addressed by Staleness-Reduction Mini-Batch K-Means [8] , a hybrid method between k-means and MacQueen. They obtained important speedups, but only on very low numbers of clusters.

e-means works on mini-batches and replaces this sum with an exponential moving average:

so older assignments are forgotten at rate α , and the centroid tracks recent assignments rather than the whole history. This update rule is typically used for moving distributions, hence their adoption for training VQ-VAEs [6] . What we found is that it’s also extremely efficient for static datasets if it’s combined with e-means’ other components, and hyperparameters are properly tuned.

The e-means project started from previous work at Meta FAIR by Hugo Touvron and Hervé Jégou, who had found that mini-batch k-means by gradient descent could beat Lloyd’s algorithm. While I could reproduce these results, I found that the performance of gradient-descent based centroid updates is unstable at large learning rates, unlike exponential moving average updates. I suspect that is because EMA updates guarantee that the centroid is always in the convex hull of points assigned to it, while gradient descent updates may overshoot past that hull.

In order to achieve the lowest loss at a fixed number of epochs, we chose exponential moving average updates, hence the name e-means for our method.

If you set the batch to the full dataset, B = n , and α = 1, then N j and S j become exactly the count and sum of the whole cluster, so one e-means iteration becomes exactly one Lloyd iteration. Lloyd is an extreme case of e-means without cosine scheduling on the learning rate. However, our hyperparameter search found that this extreme setting is highly suboptimal, which explains why e-means largely outperforms Lloyd. Below, the loss is measured for every batch size B and step α : Lloyd lands in a corner, well outside the region where the loss is lowest.

This hyperparameter study motivated us to derive scaling laws that automatically pick the optimal batch size B and step size α .

To better understand why e-means reaches better losses than Lloyd at convergence, we plotted a few trainings on toy datasets to evaluate their ability to escape local minima. Repeating trainings over 200 seeds, we found that e-means is much less likely to fall in pathological configurations compared to Lloyd.

Our explanation for that is that mini-batches provide more noisy updates that are more likely to explore the optimization landscape and escape local minima. Lloyd, with its always decreasing loss, is more likely to exploit found local minima and never escape them.

An essential property of e-means is that practitioners don't need to set any additional hyperparameter compared to Lloyd's algorithm. We fitted two scaling laws to set the batch size B and step size α 0 from any problem's characteristics (n, k, T) , and found them to exhibit strong generalization on unseen datasets and problem scales.

Regret = (MSE with the law − best MSE over the grid) / best MSE, median over configurations. Held-out datasets: SIFT, SPACEV, and the VIBE [9] datasets arXiv and AG-News. Held-out size: one value of n left out of the fit and predicted.

We propose two equations to choose the batch, the default law and the quality law. The “quality law” trades off throughput for better clustering quality against the “default” law. Below we plot the training data for our scaling laws: validation MSE against step size α 0 (left) and batch size B (right).

Toy example showing the importance of dead-cluster revival.

The main issue with mini-batch k-means is that it is prone to “dead” clusters, centroids that end up with zero assigned points during optimization. This reduces the effective size of the codebook, which is especially problematic for the large codebooks increasingly used today.

A common mitigation is to reinitialize clusters that fall below a certain size threshold, as done in EnCodec [10] , where dead centroids are simply replaced by random samples drawn from the incoming batch. While this helps, it does not fully resolve the issue. Instead of sampling arbitrary points from the batch, we revive dead clusters by splitting large, existing ones: we sample an active cluster with probability proportional to its size and split it into two. We found this approach, adapted from Faiss k-means, to be significantly more effective at eliminating dead clusters and preserving codebook capacity.

1 million vectors, k = 16,384, 5 epochs, mean over 5 seeds; only the revival policy varies. A cluster counts as dead when fewer than ten vectors are assigned to it at the end, a thousandth of an average cluster. Imbalance: how uneven the cluster sizes are (1 = all equal). From the paper ’s revival ablation table.

We validated e-means on 24 different embedding and synthetic datasets and configurations (see paper ). For the video we ran 234 configurations of e-means against k-means (16 datasets, 100k to 100M points): explore every curve in the results map .

Repo: faiss/contrib/e_means .

If you use e-means, please cite the paper ( arXiv:2611.09501 ):

k-means is one of the rare problems in machine learning where full-batch optimization is still widely used.

Mini-batch k-means methods in the literature exist [3] , [4] , [5] , but are mostly based on the MacQueen update rule, released in 1967.

Modern deep learning offers optimization tools that can enhance mini-batch methods.

M. Douze, A. Guzhva, C. Deng, J. Johnson, G. Szilvasy, P.-E. Mazaré, M. Lomeli, L. Hosseini, H. Jégou. "The Faiss library." arXiv:2401.08281 , 2024. ↑

S. Yang, H. Xi, Y. Zhao, M. Li, X. Fan, J. Zhang, H. Cai, Y. Lin, X. Li, K. Keutzer, S. Han, C. Xu, I. Stoica. "Flash-KMeans: Fast and Memory-Efficient Exact K-Means." arXiv:2603.09229 , 2026. ↑

J. MacQueen. "Some Methods for Classification and Analysis of Multivariate Observations." Proceedings of the Fifth Berkeley Symposium on Mathematical Statistics and Probability , 1:281–297, 1967. ↑

D. Sculley. "Web-Scale K-Means Clustering." WWW , 2010. ↑

J. Newling, F. Fleuret. "Nested Mini-Batch K-Means." NeurIPS , 2016. ↑

A. van den Oord, O. Vinyals, K. Kavukcuoglu. "Neural Discrete Representation Learning." NeurIPS , 2017. ↑

S. Lloyd. "Least squares quantization in PCM." IEEE Transactions on Information Theory , 28(2):129–137, 1982 (circulated as a Bell Labs technical note since 1957). ↑

X. Zhu, J. Sun, Z. He, J. Jiang, Z. Wang. "Staleness-Reduction Mini-Batch K-Means." IEEE Transactions on Neural Networks and Learning Systems , 35(10):14424–14436, 2024. ↑

E. Jääsaari, V. Hyvönen, M. Ceccarello, T. Roos, M. Aumüller. "VIBE: Vector Index Benchmark for Embeddings." arXiv:2505.17810 , 2025. ↑

A. Défossez, J. Copet, G. Synnaeve, Y. Adi. "High Fidelity Neural Audio Compression." Transactions on Machine Learning Research , 2023. arXiv:2210.13438. ↑

</details>