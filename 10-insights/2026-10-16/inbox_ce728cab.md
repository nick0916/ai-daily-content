---
id: inbox_ce728cab
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0256-infoq-main-presentation-exploding-gpus-2644]]"
title: "Presentation: Exploding GPUs"
url: https://www.infoq.com/presentations/ai-security-kubernetes-gpu-threats/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-16T11:00:00+00:00
fetched_at: 2026-10-18T03:14:14.197471+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Andrew Martin 在 InfoQ 簡報中論述 AI 安全與 Kubernetes 安全密不可分。內容涵蓋演進中的 AI 威脅態勢，包括 agent 行為的非確定性、GPU 供應鏈漏洞、共享運算資源風險。防禦策略方面提到從 prompt firewalling 到 agentic identity 的實務作法，目標是保護 production 環境中的 cloud-native AI 工作負載。原文摘要未提供具體數據、漏洞編號或工具名稱。對負責在 Kubernetes 上跑 AI workload 的平台與資安團隊有參考價值。"
key_points:
  - "AI 安全與 Kubernetes 安全本質相連"
  - "威脅面向：agent 非確定性行為、GPU 供應鏈漏洞、共享運算風險"
  - "防禦手段：prompt firewalling、agentic identity"
tags: [kubernetes, gpu-security, ai-security, prompt-firewall, agentic-identity]
topics: [security, engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Exploding GPUs

Andrew Martin 在 InfoQ 簡報中論述 AI 安全與 Kubernetes 安全密不可分。內容涵蓋演進中的 AI 威脅態勢，包括 agent 行為的非確定性、GPU 供應鏈漏洞、共享運算資源風險。防禦策略方面提到從 prompt firewalling 到 agentic identity 的實務作法，目標是保護 production 環境中的 cloud-native AI 工作負載。原文摘要未提供具體數據、漏洞編號或工具名稱。對負責在 Kubernetes 上跑 AI workload 的平台與資安團隊有參考價值。

### 重點
- AI 安全與 Kubernetes 安全本質相連
- 威脅面向：agent 非確定性行為、GPU 供應鏈漏洞、共享運算風險
- 防禦手段：prompt firewalling、agentic identity

**原文：** [infoq-main](https://www.infoq.com/presentations/ai-security-kubernetes-gpu-threats/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Andrew Martin discusses why AI security is fundamentally tied to Kubernetes security. He shares insights into the evolving AI threat landscape, covering non-deterministic agent behavior, GPU supply chain vulnerabilities, shared compute risks, and practical defense strategies - from prompt firewalling to agentic identity - to help secure cloud-native AI workloads in production environments. By Andrew Martin

</details>