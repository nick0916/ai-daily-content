---
id: inbox_e95de78a
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-infoq-main-aws-nitro-sandboxes-put-each-eks-pod-in-9d9f]]"
title: "AWS Nitro Sandboxes Put Each EKS Pod in Its Own MicroVM with One RuntimeClass Field"
url: https://www.infoq.com/news/2026/11/aws-nitro-sandboxes-eks/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-16T09:07:00+00:00
fetched_at: 2026-11-17T23:25:04.131247+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 讓每個 Kubernetes pod 用一行設定就跑在獨立的微型虛擬機裡，隔離更強。 **Why** 一般容器共用主機 kernel，隔離較弱，多租戶或不受信任的程式碼（如 agent 產生的程式）風險較高。 **How** 在 pod 設定加上一個 runtimeClassName 欄位，即讓該 pod、ECS task 或 EC2 workload 跑在各自擁有獨立 kernel 的 Firecracker microVM 中；confidential 模式再加上 attestation 通過才釋出金鑰。 **What** AWS Nitro Sandboxes 無額外費用；限制包括不支援 GPU passthrough、每 vCPU 最多 5 個 sandbox、SMT 執行個體只有一半算力。"
key_points:
  - "以單一 runtimeClassName 欄位啟用，每個 pod 獨立 Firecracker microVM 與 kernel，無額外費用"
  - "confidential 模式加入 attestation 把關的金鑰釋出"
  - "限制：無 GPU passthrough、每 vCPU 最多 5 個 sandbox、SMT 執行個體僅一半算力"
tags: [aws, nitro-sandboxes, firecracker, eks, isolation]
topics: [security, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Nitro Sandboxes Put Each EKS Pod in Its Own MicroVM with One RuntimeClass Field

AWS 讓每個 Kubernetes pod 用一行設定就跑在獨立的微型虛擬機裡，隔離更強。

**Why** 一般容器共用主機 kernel，隔離較弱，多租戶或不受信任的程式碼（如 agent 產生的程式）風險較高。

**How** 在 pod 設定加上一個 runtimeClassName 欄位，即讓該 pod、ECS task 或 EC2 workload 跑在各自擁有獨立 kernel 的 Firecracker microVM 中；confidential 模式再加上 attestation 通過才釋出金鑰。

**What** AWS Nitro Sandboxes 無額外費用；限制包括不支援 GPU passthrough、每 vCPU 最多 5 個 sandbox、SMT 執行個體只有一半算力。

### 重點
- 以單一 runtimeClassName 欄位啟用，每個 pod 獨立 Firecracker microVM 與 kernel，無額外費用
- confidential 模式加入 attestation 把關的金鑰釋出
- 限制：無 GPU passthrough、每 vCPU 最多 5 個 sandbox、SMT 執行個體僅一半算力

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-nitro-sandboxes-eks/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has launched Nitro Sandboxes, running each opted-in EKS pod, ECS task or EC2 workload in its own Firecracker microVM with a separate kernel, enabled by one runtimeClassName field at no extra charge. A confidential mode adds attestation-gated key release. The documentation lists the trade-offs: no GPU passthrough, at most five sandboxes per vCPU, and half the compute on SMT instances. By Steef-Jan Wiggers

</details>