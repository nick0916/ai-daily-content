---
id: inbox_62e5acaf
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-infoq-main-cilium-1-20-expands-gateway-api-and-open-e4c3]]"
title: "Cilium 1.20 Expands Gateway API and Opens eBPF Datapath for Kubernetes"
url: https://www.infoq.com/news/2026/10/cilium-120-kubernetes-networking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-21T09:00:00+00:00
fetched_at: 2026-10-21T23:42:18.418033+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Kubernetes 網路元件 Cilium 發布新版，擴大 Gateway API 支援並讓底層更好擴充。 **What** Cilium 1.20 提供更廣的 Kubernetes Gateway API 支援、可擴充的 eBPF datapath，以及 sidecarless mutual TLS 的進一步進展；也讓 netkit 網路裝置更容易在 Linux 核心版本不一的叢集中導入。"
key_points:
  - "更完整的 Kubernetes Gateway API 支援"
  - "可擴充的 eBPF datapath"
  - "sidecarless mutual TLS 持續推進；netkit 更易跨不同 kernel 版本導入"
tags: [cilium, kubernetes, ebpf, gateway-api, networking]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Cilium 1.20 Expands Gateway API and Opens eBPF Datapath for Kubernetes

Kubernetes 網路元件 Cilium 發布新版，擴大 Gateway API 支援並讓底層更好擴充。 **What** Cilium 1.20 提供更廣的 Kubernetes Gateway API 支援、可擴充的 eBPF datapath，以及 sidecarless mutual TLS 的進一步進展；也讓 netkit 網路裝置更容易在 Linux 核心版本不一的叢集中導入。

### 重點
- 更完整的 Kubernetes Gateway API 支援
- 可擴充的 eBPF datapath
- sidecarless mutual TLS 持續推進；netkit 更易跨不同 kernel 版本導入

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/cilium-120-kubernetes-networking/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cilium 1.20 has been released with broader Kubernetes Gateway API support, an extensible eBPF datapath and further work on sidecarless mutual TLS. The release also makes the newer netkit network device easier to introduce across Kubernetes fleets that run different Linux kernel versions. By Matt Saunders

</details>