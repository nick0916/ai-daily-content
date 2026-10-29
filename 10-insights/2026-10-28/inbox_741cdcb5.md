---
id: inbox_741cdcb5
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0017-substack-byte-sized-design-meta-s-smartest-agent-was-the-problem-th-ec7c]]"
title: "🧠 Meta&#39;s Smartest Agent Was the Problem. The Dumb One Fixed It"
url: https://read.bytesizeddesign.com/p/meta-thin-orchestrator-agent-router
source: substack-byte-sized-design
published_at: 2026-10-28T02:40:41+00:00
fetched_at: 2026-10-29T00:22:17.195414+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把總管 agent 的知識拿掉、只讓它派工，反而讓整個系統更準。 **Why** Meta 原本用一個什麼都知道的 agent 處理推薦管線的欄位上線，但 context 太大後開始幻覺，把一個子系統的命名慣例套到另一個。 **How** 用 1,300 行的 orchestrator 只做分類意圖、收集欄位、可靠性檢查與路由，不做任何領域推理；14 個專家 subagent 各自只載入自己的領域。orchestrator 每次請求跑七個步驟，只有一步呼叫模型。 **What** 欄位設定準備時間從人工 3–4 天，降到早期設定驅動系統的約一天，再降到一小時內，約三分之二的變更不需大幅人工修改。工作流模板是固定狀態機，為 20 多種用例排列這 14 個 agent。原則是：路由決策用確定性程式碼，推理決策才交給 LLM，且放在最小的 context 內。"
key_points:
  - "單一 agent 加人工手寫 prompt 可達 70–80% 成功率，拿掉人工 prompt 後掉到 10–20%"
  - "1,300 行 orchestrator 路由 14 個 subagent、支援 20 多種用例，七個步驟中只有第六步呼叫模型"
  - "欄位設定準備時間從 3–4 天降到一小時內，約三分之二變更無需大幅人工編輯"
tags: [multi-agent, orchestrator, context-isolation, meta, deterministic-routing]
topics: [agents.frameworks, engineering.architecture]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## 🧠 Meta's Smartest Agent Was the Problem. The Dumb One Fixed It

把總管 agent 的知識拿掉、只讓它派工，反而讓整個系統更準。

**Why** Meta 原本用一個什麼都知道的 agent 處理推薦管線的欄位上線，但 context 太大後開始幻覺，把一個子系統的命名慣例套到另一個。

**How** 用 1,300 行的 orchestrator 只做分類意圖、收集欄位、可靠性檢查與路由，不做任何領域推理；14 個專家 subagent 各自只載入自己的領域。orchestrator 每次請求跑七個步驟，只有一步呼叫模型。

**What** 欄位設定準備時間從人工 3–4 天，降到早期設定驅動系統的約一天，再降到一小時內，約三分之二的變更不需大幅人工修改。工作流模板是固定狀態機，為 20 多種用例排列這 14 個 agent。原則是：路由決策用確定性程式碼，推理決策才交給 LLM，且放在最小的 context 內。

### 重點
- 單一 agent 加人工手寫 prompt 可達 70–80% 成功率，拿掉人工 prompt 後掉到 10–20%
- 1,300 行 orchestrator 路由 14 個 subagent、支援 20 多種用例，七個步驟中只有第六步呼叫模型
- 欄位設定準備時間從 3–4 天降到一小時內，約三分之二變更無需大幅人工編輯

**原文：** [substack-byte-sized-design](https://read.bytesizeddesign.com/p/meta-thin-orchestrator-agent-router)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

⚡ TLDR Meta built one AI agent that knew everything about onboarding a data column into its recommendation pipelines: three repos, three languages, up to six pipeline stages, config schemas, codegen rules, population patterns for ten-plus data sources. It worked in demos. In production it started hallucinating, applying one subsystem’s naming conventions to another and using the wrong codegen pattern for the wrong data source. The fix was to take knowledge away from the central agent. What replaced it: A 1,300-line orchestrator that does zero domain work. It classifies intent, gathers fields, runs reliability checks, and routes 14 specialist subagents, each loaded with only its own domain and nothing else Workflow templates, which are fixed state machines that sequence those 14 agents differently for each of 20+ use cases Column config prep went from three to four days by hand, to about a day with an earlier config-driven system, to under an hour. Around two-thirds of the system’s changes land without significant human edits. The rule underneath, which transfers to any agent system: for every component, decide whether it’s making a routing decision or a reasoning decision. Routing is deterministic and gets code. Reasoning gets an LLM, inside the smallest context that can do the job. Meta’s orchestrator follows seven steps per request and exactly one of them calls a model. 🫠 More context, worse agent The pipeline is config-as-code. Python configs drive C++ code generation, which feeds data processing services, which populate analytics systems. One new column means coordinated edits across configuration registries, backend services, and pipelines, in the right order, kept in sync. The first version was the obvious one. One agent, one giant prompt, every schema and rule and pattern loaded. It had everything it needed, and past some context size that became the problem. Knowledge from one subsystem leaked into decisions about another. The agent had plenty of information and was mixing it up. A second attempt, still single-agent, got to 70 to 80 percent success, with a catch: an engineer had to hand-write a custom system prompt for each specific job. Take the handholding away and success fell to 10 to 20 percent. A system that only works when a human pre-chews the prompt per task is a system where the human is doing the orchestration. Meta cites a Mount Sinai preprint on the same effect in a different domain: orchestrated multi-agent systems held 65.3% accuracy at 80-task batches where single agents fell to 16.6%, with up to 65x less token usage, attributed to task isolation preventing context interference. Different field, same shape of failure. If you’ve read the agents-are-microservices edition , this is the monolith problem. A single agent with 40 tools and a 6,000-token system prompt degrades the way a 400,000-line app does. Every capability you add makes every other one slightly worse. 🚦 A router that refuses to think The replacement has two layers, and the split between them is the whole idea. The orchestrator is deterministic and does no domain work at all. It never reasons about code, never generates a config, never touches the codebase. For every request it runs the same seven steps: Read the relevant subagent’s instruction file Check whether the target already exists, to prevent duplicates Gather required fields from the user Auto-discover what can be inferred (repo type, existing configs) Reliability gate: active warnings, required reviewers Delegate to the subagent with full context Handle results, surface errors, confirm success Steps 1 through 5 and step 7 are plain code. Step 6 is the only place a model reasons, and it does so inside a subagent that has only its own domain loaded. The 14 subagents are each a complete domain expert with isolated context. A schema agent knows the configuration registries. A population agent knows how to generate code for each of the ten data sources. A validation agent knows build systems and quality checks. No single agent sees the whole picture, which is what stops the cross-contamination that killed v1. The population agent for data source A has never seen data source B’s patterns, so it can’t apply them by mistake. 
 
 
 Read more

</details>