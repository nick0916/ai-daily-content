---
id: inbox_21cfaacb
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-simon-willison-aws-emulator-16d4]]"
title: "aws-emulator"
url: https://simonwillison.net/2026/Nov/11/aws-emulator/
source: simon-willison
published_at: 2026-11-11T21:18:30+00:00
fetched_at: 2026-11-12T02:58:27.299816+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 官方推出本機模擬器，讓測試不必呼叫付費的真實雲端服務。 **Why** 過去要對 AWS 服務跑測試，得佈建並付費使用真實 API。 **What** aws-emulator 是 AWS 官方的本機服務複製品，以 Rust 撰寫，由大量 agent 協作完成，前三週共 29,684 個 commit；Swami Sivasubramanian 在 Werner Vogels 的 blog 客座文章中談了來由。目前在 macOS 或 Windows 上需要 Docker，Simon 希望未來能提供單一執行檔。"
key_points:
  - "官方 AWS 模擬器，可對本機多種服務複本跑測試，無需付費 API key"
  - "Rust 撰寫，由一大群 agent 完成，專案前三週 29,684 個 commit"
  - "目前 macOS/Windows 需 Docker；Simon 期望未來提供單一 binary"
tags: [aws, aws-emulator, rust, testing, agentic-engineering]
topics: [agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## aws-emulator

AWS 官方推出本機模擬器，讓測試不必呼叫付費的真實雲端服務。

**Why** 過去要對 AWS 服務跑測試，得佈建並付費使用真實 API。

**What** aws-emulator 是 AWS 官方的本機服務複製品，以 Rust 撰寫，由大量 agent 協作完成，前三週共 29,684 個 commit；Swami Sivasubramanian 在 Werner Vogels 的 blog 客座文章中談了來由。目前在 macOS 或 Windows 上需要 Docker，Simon 希望未來能提供單一執行檔。

### 重點
- 官方 AWS 模擬器，可對本機多種服務複本跑測試，無需付費 API key
- Rust 撰寫，由一大群 agent 完成，專案前三週 29,684 個 commit
- 目前 macOS/Windows 需 Docker；Simon 期望未來提供單一 binary

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/11/aws-emulator/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

aws-emulator 
Finally, an official emulator from AWS to run tests against a local clone of their many different services without having to provision a paid API key to do so. 
 It's written in Rust by a huge swarm of agents - 29,684 commits in the first three weeks of the project. Swaminathan (Swami) Sivasubramanian wrote about how it came to be in a guest post on Werner Vogels' blog. 
 It currently requires Docker to run on macOS or Windows. I'm hoping they fix that in the future - it would be great if you could download a single binary and use that as part of a standard test suite in other languages and on other platforms.

 Tags: amazon , amazon-web-services , testing , werner-vogels , ai , rust , docker , generative-ai , llms , agentic-engineering

</details>