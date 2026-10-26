---
id: inbox_7884ce47
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-infoq-main-article-ai-changes-the-data-interface-no-7896]]"
title: "Article: AI Changes the Data Interface, Not the Query Engine"
url: https://www.infoq.com/articles/ai-changes-data-interface/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-22T09:00:00+00:00
fetched_at: 2026-10-23T00:55:43.005855+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 只負責「寫查詢與解讀結果」，真正算數字交給確定性的資料庫引擎，結果才可重現。 **Why** 若讓 LLM 直接給出數字，答案無法重現也難以稽核；災害復原分析需要可驗證的事實。 **How** 把工作拆成確定性與非確定性兩段：AI agent 產生受限的 SQL 或 Python，DuckDB 在 Parquet 上計算可重現的事實，再由 agent 解讀結果，整個分析可重播。 **What** InfoQ 文章（作者 Peihao Yuan）以災害復原分析流程為例，說明 determinism split 與 replayable analysis，並提出四個訊號，用來判斷嵌入式引擎（DuckDB）已足夠，或需要上託管式 lakehouse。"
key_points:
  - "確定性分工：AI agent 產生受限 SQL/Python，DuckDB 在 Parquet 上計算事實，agent 只負責解讀結果"
  - "分析流程可重播（replayable analysis），讓結果可重現、可稽核"
  - "提供四個訊號判斷何時嵌入式引擎足夠、何時才需要託管 lakehouse"
tags: [duckdb, parquet, ai-agent, text-to-sql, determinism, lakehouse]
topics: [agents.frameworks, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: AI Changes the Data Interface, Not the Query Engine

讓 AI 只負責「寫查詢與解讀結果」，真正算數字交給確定性的資料庫引擎，結果才可重現。

**Why** 若讓 LLM 直接給出數字，答案無法重現也難以稽核；災害復原分析需要可驗證的事實。

**How** 把工作拆成確定性與非確定性兩段：AI agent 產生受限的 SQL 或 Python，DuckDB 在 Parquet 上計算可重現的事實，再由 agent 解讀結果，整個分析可重播。

**What** InfoQ 文章（作者 Peihao Yuan）以災害復原分析流程為例，說明 determinism split 與 replayable analysis，並提出四個訊號，用來判斷嵌入式引擎（DuckDB）已足夠，或需要上託管式 lakehouse。

### 重點
- 確定性分工：AI agent 產生受限 SQL/Python，DuckDB 在 Parquet 上計算事實，agent 只負責解讀結果
- 分析流程可重播（replayable analysis），讓結果可重現、可稽核
- 提供四個訊號判斷何時嵌入式引擎足夠、何時才需要託管 lakehouse

**原文：** [infoq-main](https://www.infoq.com/articles/ai-changes-data-interface/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This article presents a disaster-recovery analytics workflow in which an AI agent generates constrained SQL or Python, DuckDB computes reproducible facts from Parquet, and the agent interprets the results. It explains the determinism split, replayable analysis, and four signals for deciding when an embedded engine is sufficient or a managed lakehouse is justified. By Peihao Yuan

</details>