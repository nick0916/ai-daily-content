---
id: inbox_54b5990b
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-infoq-main-yelp-migrates-cassandra-to-eks-by-moving-c85e]]"
title: "Yelp Migrates Cassandra to EKS by Moving EBS Volumes"
url: https://www.infoq.com/news/2026/11/kubernetes-cassandra-eks/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-18T09:00:00+00:00
fetched_at: 2026-11-19T08:18:32.250021+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Yelp 搬 Cassandra 到 EKS 時，直接把硬碟卷掛到新機器，而不是把資料一筆筆複製過去。 **Why** 原本跑在自行管理的舊 Kubernetes 叢集上，需要遷移到 Amazon EKS。 **How** 將既有 EBS volume 重新指向新的 pod，省去節點之間串流資料。 **What** Yelp 以此方式把整個 Cassandra fleet 從舊的自管 Kubernetes 叢集遷到 Amazon EKS。"
key_points:
  - "Yelp 將 Cassandra fleet 從自管 Kubernetes 遷到 Amazon EKS"
  - "作法是把既有 EBS volume 重新指向新 pod，而非節點間串流資料"
tags: [yelp, cassandra, eks, kubernetes, ebs, migration]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Yelp Migrates Cassandra to EKS by Moving EBS Volumes

Yelp 搬 Cassandra 到 EKS 時，直接把硬碟卷掛到新機器，而不是把資料一筆筆複製過去。

**Why** 原本跑在自行管理的舊 Kubernetes 叢集上，需要遷移到 Amazon EKS。

**How** 將既有 EBS volume 重新指向新的 pod，省去節點之間串流資料。

**What** Yelp 以此方式把整個 Cassandra fleet 從舊的自管 Kubernetes 叢集遷到 Amazon EKS。

### 重點
- Yelp 將 Cassandra fleet 從自管 Kubernetes 遷到 Amazon EKS
- 作法是把既有 EBS volume 重新指向新 pod，而非節點間串流資料

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/kubernetes-cassandra-eks/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Yelp has moved its Cassandra fleet from legacy self-managed Kubernetes clusters to Amazon EKS by re-pointing existing EBS volumes at new pods, rather than streaming data between nodes. By Claudio Masolo

</details>