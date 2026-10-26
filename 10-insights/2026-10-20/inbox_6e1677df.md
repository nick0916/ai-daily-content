---
id: inbox_6e1677df
date: 2026-10-20
source_ref: "[[00-inbox/.../inbox_6e1677df]]"
title: "📉 98% GPU Utilization and a 6x Speedup Left on the Table"
url: https://read.bytesizeddesign.com/p/98-percent-gpu-utilization-6x-speedup
source: substack-byte-sized-design
published_at: 2026-10-20T16:16:53+00:00
fetched_at: 2026-10-21T00:16:05.103027+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GPU 使用率顯示 98% 不代表跑得有效率，微調訓練可能白白慢 6 倍。 **Why** 「GPU utilization」只表示 GPU 有在忙，並不代表算力被有效利用，所以高使用率仍可能隱藏嚴重的效能浪費。 **How** Databricks 提出兩個修正：安裝 fused kernels，以及把 batch 做 packing。 **What** 案例是 Qwen 27B 的 fine-tune，顯示 98% GPU 使用率卻比應有速度慢 6 倍；套用上述兩項修正後可取回這 6 倍的加速空間。"
key_points:
  - "Qwen 27B fine-tune 顯示 98% GPU utilization，卻比應有速度慢 6 倍"
  - "修正一：安裝 fused kernels"
  - "修正二：對 batch 做 packing"
tags: [gpu-utilization, fine-tuning, fused-kernels, batch-packing, databricks]
topics: [research.training, engineering.inference]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## 📉 98% GPU Utilization and a 6x Speedup Left on the Table

GPU 使用率顯示 98% 不代表跑得有效率，微調訓練可能白白慢 6 倍。

**Why** 「GPU utilization」只表示 GPU 有在忙，並不代表算力被有效利用，所以高使用率仍可能隱藏嚴重的效能浪費。

**How** Databricks 提出兩個修正：安裝 fused kernels，以及把 batch 做 packing。

**What** 案例是 Qwen 27B 的 fine-tune，顯示 98% GPU 使用率卻比應有速度慢 6 倍；套用上述兩項修正後可取回這 6 倍的加速空間。

### 重點
- Qwen 27B fine-tune 顯示 98% GPU utilization，卻比應有速度慢 6 倍
- 修正一：安裝 fused kernels
- 修正二：對 batch 做 packing

**原文：** [substack-byte-sized-design](https://read.bytesizeddesign.com/p/98-percent-gpu-utilization-6x-speedup)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 📉 98% GPU Utilization and a 6x Speedup Left on the Table

A Qwen 27B fine-tune showed 98% GPU utilization and ran 6x slower than it should. Two fixes from Databricks: install the fused kernels, pack the batches.

</details>