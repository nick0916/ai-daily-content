---
id: inbox_533ee7ce
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/0002-github-trending-agent-tools-beenuar-aisoc-6-198-446-55a5]]"
title: "beenuar/AiSOC ⭐ 6,198(今日 +446)"
url: https://github.com/beenuar/AiSOC
source: github-trending-agent-tools
published_at: 2026-11-02T00:02:27.376020+00:00
fetched_at: 2026-11-02T00:08:49.975682+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "開源、可自架的 AI 資安營運中心，由 AI agent 調查告警，且每一步可稽核。 **Why** 原文強調 AI 的推理過程需可稽核，且對外部系統的動作需人工核准後才執行。 **How** 遙測資料先標準化，再跑偵測規則並把告警關聯成事件，由 LLM agent 逐一調查；每個 agent 的 prompt 與工具呼叫都會被記錄並可重播，建議的回應需人工批准。 **What** 內含 2534 條可執行規則（規則庫共 7015 條）與 76 條滑動視窗規則，附 MCP server 供 Claude、Cursor、Continue 使用，MIT 授權；部署需 Docker Compose v2、8GB 記憶體與 20GB 磁碟，遷移工具 aisoc-migrate 可翻譯 Splunk SPL、Sentinel KQL、Elastic EQL（2005 條 Splunk 規則中 1734 條可翻譯，其中 1711 條為部分翻譯）。GitHub 星數 6,198（今日 +446）。"
key_points:
  - "偵測流程：標準化遙測後執行 2534 條可執行規則，加上 76 條滑動視窗規則，把告警分組為事件，再交給 LLM agent 調查"
  - "可稽核設計：每個 agent 步驟的 prompt 與工具呼叫都被記錄並可重播，建議的回應需人工核准後才送往廠商系統"
  - "遷移與部署：aisoc-migrate 翻譯 SPL/KQL/EQL，無法精確轉換時會拒絕；2005 條 Splunk 規則中 1734 條可翻譯；部署需 Docker Compose v2、8GB 記憶體、20GB 磁碟"
tags: [ai-soc, security-operations, mcp, agent-audit, siem, open-source]
topics: [security, agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## beenuar/AiSOC ⭐ 6,198(今日 +446)

開源、可自架的 AI 資安營運中心，由 AI agent 調查告警，且每一步可稽核。

**Why** 原文強調 AI 的推理過程需可稽核，且對外部系統的動作需人工核准後才執行。

**How** 遙測資料先標準化，再跑偵測規則並把告警關聯成事件，由 LLM agent 逐一調查；每個 agent 的 prompt 與工具呼叫都會被記錄並可重播，建議的回應需人工批准。

**What** 內含 2534 條可執行規則（規則庫共 7015 條）與 76 條滑動視窗規則，附 MCP server 供 Claude、Cursor、Continue 使用，MIT 授權；部署需 Docker Compose v2、8GB 記憶體與 20GB 磁碟，遷移工具 aisoc-migrate 可翻譯 Splunk SPL、Sentinel KQL、Elastic EQL（2005 條 Splunk 規則中 1734 條可翻譯，其中 1711 條為部分翻譯）。GitHub 星數 6,198（今日 +446）。

### 重點
- 偵測流程：標準化遙測後執行 2534 條可執行規則，加上 76 條滑動視窗規則，把告警分組為事件，再交給 LLM agent 調查
- 可稽核設計：每個 agent 步驟的 prompt 與工具呼叫都被記錄並可重播，建議的回應需人工核准後才送往廠商系統
- 遷移與部署：aisoc-migrate 翻譯 SPL/KQL/EQL，無法精確轉換時會拒絕；2005 條 Splunk 規則中 1734 條可翻譯；部署需 Docker Compose v2、8GB 記憶體、20GB 磁碟

**原文：** [github-trending-agent-tools](https://github.com/beenuar/AiSOC)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Open-source AI Security Operations Center: alert fusion, LLM-agent triage, MITRE ATT&CK investigation, and a replayable decision ledger for every agent step. Self-hostable, runs with no API keys, MIT licensed. Ships an MCP server for Claude, Cursor and Continue.

AiSOC

What AiSOC does

What it looks like running

Quick start

Connect real data

How it works

Deployment profiles

Evaluation, reflex and replay

AI agents

Project maturity

What AiSOC is not

Troubleshooting

Security

Developing

Funding · Roadmap · Contributing · License

An open-source, self-hostable AI Security Operations Center. It ingests your security telemetry, detects and correlates threats, investigates them with AI agents whose reasoning is fully auditable, and proposes responses a human approves.

 

Technical Guide (PDF) · Docs · Architecture · What actually works · Discussions

Telemetry arrives from your security tools. AiSOC normalizes it, runs the 2534 executable rules of
its 7015-rule library, groups what fires into incidents, investigates each one with an AI agent whose
every prompt and tool call is recorded, and proposes an action. New threat intelligence re-sweeps the
history you already collected, and a human approves before anything reaches a vendor.

Watch the full three minutes — install to AI verdict on one
server against the published images, terminal waits shortened and the recording saying so on screen.
The stills below are from a v20.1.0 run under the same rules — the recording is older than they are.
( step by step · what is real )

On Windows , or on a machine with nothing installed yet, one line does the prerequisites too: iwr -useb https://raw.githubusercontent.com/beenuar/AiSOC/main/install.ps1 | iex ( curl -fsSL https://raw.githubusercontent.com/beenuar/AiSOC/main/install.sh | bash on Linux and macOS). Without Docker at all , pip install aisoc-sandbox && aisoc-sandbox demo walks one alert through the agent funnel offline in under 30 seconds. Without your own machine , open the repo in GitHub Codespaces and run make up in its terminal. All four end at the same console; only the first three install anything.

The Technical Guide covers this in depth: server sizing, where the model runs, every failure mode with its cause and fix, the REST API, MCP, and every console surface.

Needs Docker Compose v2 with 8 GB memory and 20 GB free disk in the Docker VM , plus python3 (3.9+) and bash ; make doctor checks all of it and Installation says what each number was measured against. The first run downloads a ~2 GB model into a volume only make clean clears.

make up also creates .env and generates the fifteen secrets in it — the credential vault, the
session signing key, five service-to-service credentials and four datastore passwords — then creates an
administrator and prints its password, generated on your machine, shown once and stored nowhere. Lost
it? make bootstrap ARGS=--reset-password mints another.

A port already in use does not stop the install. AiSOC publishes on a free one, names what held the
old one, and moves the console address with it: 64 seconds to a signed-in console on a bare clone with
5432 and 11434 both taken.

Then prove it works . make smoke posts one real event to the ingest API and follows it through
Kafka, detection, correlation and Postgres, then reads the alert back out of the public API. Every
stage reports PASS or FAIL:

Sign in at the address make up printed. A tenant with nothing connected lands on a setup
wizard rather than an all-zero dashboard, and its state is read from your own data so it stays
right if you connect a source through the API. The spec is docs/openapi.yaml — interactive docs are off in this production-class stack.
Stuck? make doctor , which on a host where you have not run make up yet says exactly that.

Press Load sample data in the wizard. Five scenarios take the same ingest path a real connector uses — not inserted rows — so watching them become alerts means watching the pipeline work. They span low to critical on purpose, because a first run where everything is a crisis teaches you nothing about how triage separates signal from routine. They are attributed to AiSOC in the source column, refuse to load into a tenant that already has real alerts, and do not mark setup complete. ( what each step proves ) For the larger fixed corpus used by demos and evals, make demo loads a synthetic dataset — the pipeline shape, never a benchmark, a customer or an incident. Every row is is_synthetic = true and labelled in the console.

Push, with a credential from make ingest-token (the tenant comes from it, not a header):

Or pull, by configuring one of 90 click-and-connect data connectors in Settings → Connectors — Splunk, Sentinel, Elastic, CrowdStrike, Okta, AWS and Kubernetes audit among those with
vendor-specific normalization and setup docs
( coverage ). Without a vendor profile
a connector still ingests through a generic mapping that resolves host, user and source IP.

A real cloud estate does not hand you its logs over a REST call. Four collectors read the
surfaces one actually emits to: a CloudTrail organisation trail on S3 notified over SQS (management events, data events and VPC flow logs), a GCP Pub/Sub subscription on a Cloud Logging
sink, an Azure Event Hubs capture, and a syslog/CEF listener. Each keeps a resumable cursor
and a bounded per-poll budget, so a backlog applies backpressure instead of flooding ingest.

Bringing existing detections? packages/aisoc-migrate translates Splunk SPL, Sentinel KQL and
Elastic EQL and refuses rather than approximating what it cannot carry, because an almost-right
rule is harder to find than a missing one: of the 2,005 Splunk rules bundled here 1,734 translate and
1,711 of those are partial ( what that means ).

Ingest normalizes to a common shape and stamps an activity projection on every event — actor, action, resource, location, outcome, with actor.kind read from each vendor's own documented field rather than inferred — then Kafka carries it.
Then fusion runs 2534 executable detection rules, of 7015 on disk, plus 76 sliding-window rules (73 count across events; 3 match an ordered sequence), applies your tenant's own tuning on top — the disables, floors and suppres

</details>