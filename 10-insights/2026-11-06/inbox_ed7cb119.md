---
id: inbox_ed7cb119
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0003-github-trending-agent-tools-google-skills-22-358-211-838d]]"
title: "google/skills ⭐ 22,358(今日 +211)"
url: https://github.com/google/skills
source: github-trending-agent-tools
published_at: 2026-11-06T00:03:12.009832+00:00
fetched_at: 2026-11-06T00:14:24.033582+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 提供給 coding agent 的 Agent Skills 套件，涵蓋 Google Cloud 與 Gemini 相關產品。 **How** 以 npx 安裝，可選擇技能、目標 agent 與安裝範圍（專案或全域），並可更新既有技能。 **What** 分類包括 AI/ML（Agent Platform、Gemini API、Genkit 的 Dart/Go/JS/Python、BigQuery AI）與基礎設施（GKE、Compute Engine、Cloud Storage、Filestore、網路）；採 Apache 2.0 授權，另提供同時含 Skills 與 MCP server 的產品 plugin。"
key_points:
  - "README 列出的技能涵蓋 Agent Platform 的模型部署、調校、RAG Engine 與 eval 流程，以及 GKE 的 TPU 疑難排解與升級維運。"
  - "多產品解決方案類技能包含 AlloyDB 混合搜尋、GKE 上的 RAG 企業搜尋，以及 secure n-tier serverless 網站架構。"
  - "若安裝需求為 Node.js，因 npx 隨 npm 提供；問題回報走 GitHub Issue Tracker。"
tags: [google-cloud, agent-skills, gemini, gke, kubernetes]
topics: [agents.frameworks, foundation_models.gemini]
importance: 3
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## google/skills ⭐ 22,358(今日 +211)

Google 提供給 coding agent 的 Agent Skills 套件，涵蓋 Google Cloud 與 Gemini 相關產品。

**How** 以 npx 安裝，可選擇技能、目標 agent 與安裝範圍（專案或全域），並可更新既有技能。

**What** 分類包括 AI/ML（Agent Platform、Gemini API、Genkit 的 Dart/Go/JS/Python、BigQuery AI）與基礎設施（GKE、Compute Engine、Cloud Storage、Filestore、網路）；採 Apache 2.0 授權，另提供同時含 Skills 與 MCP server 的產品 plugin。

### 重點
- README 列出的技能涵蓋 Agent Platform 的模型部署、調校、RAG Engine 與 eval 流程，以及 GKE 的 TPU 疑難排解與升級維運。
- 多產品解決方案類技能包含 AlloyDB 混合搜尋、GKE 上的 RAG 企業搜尋，以及 secure n-tier serverless 網站架構。
- 若安裝需求為 Node.js，因 npx 隨 npm 提供；問題回報走 GitHub Issue Tracker。

**原文：** [github-trending-agent-tools](https://github.com/google/skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Agent Skills for Google products and technologies

Agent Skills

Installation

Updating Skills

Available Skills

Additional Google skills

Plugins

Support

Contributing

License

This repository contains Agent Skills for Google
products and technologies, including Google Cloud .

When prompted, select specific skills or all skills, the target agents to
configure, and the installation scope (project or global).

If npx is not available in your environment, install Node.js , which includes npm and npx .

To update previously installed skills to the latest versions, run the following
command.

This command gives you an option to also remove obsolete skills.

This repo also bundles Google product plugins (Skills + MCP servers) for agent harnesses.

If you need help or encounter issues with these skills, search for existing
issues or open a new one in the GitHub Issue Tracker .

We welcome contributions to improve our skills. You can help by:

You are free to copy, modify, and distribute these skills under the terms of the
Apache 2.0 license. See the LICENSE file for details.

Getting started with Google Cloud Authenticating and Authorizing to Google Cloud (IAM) Google Cloud Recipe: Foundation Builder Onboarding to Google Cloud 

Authenticating and Authorizing to Google Cloud (IAM)

Google Cloud Recipe: Foundation Builder

Onboarding to Google Cloud

Multi-product solution skills Google Cloud solution-architecture workflow Agent Gateway multi-agent security Agentic analytics across cloud providers and data types Borderless open data lakehouse agentic AI system Build and deploy AI agents on Google Cloud Data science workflow with AI agents solution Dynamic Hybrid Search using AlloyDB Google Skill Finder Live bidirectional multimodal streaming agentic AI solution Migrate AI Workloads to GKE Inference RAG for enterprise search using GKE and AlloyDB Secure n-tier serverless web application with strict private application tiers 

Google Cloud solution-architecture workflow

Agent Gateway multi-agent security

Agentic analytics across cloud providers and data types

Borderless open data lakehouse agentic AI system

Build and deploy AI agents on Google Cloud

Data science workflow with AI agents solution

Dynamic Hybrid Search using AlloyDB

Google Skill Finder

Live bidirectional multimodal streaming agentic AI solution

Migrate AI Workloads to GKE Inference

RAG for enterprise search using GKE and AlloyDB

Secure n-tier serverless web application with strict private application tiers

AI/ML Agent Access Audit Agent Platform Alert Configuration Agent Platform Endpoint Management Agent Platform Eval Flywheel Skill Agent Platform GenAI Inference Skill Agent Platform Model Garden Deploy Skill Agent Platform Model Registry Management Agent Platform Model Tuning Agent Platform Prompt Management Agent Platform RAG Engine Management Agent Platform Troubleshooting Agent Platform Tuning Management API Gateway Remote MCP Server (Public Preview) Apigee as an Agent Gateway Service Extension BigQuery AI & ML Gemini API in Agent Platform Gemini Enterprise Agent Platform - Managed Agents API Skill Gemini Interactions API Skill Gemini platform Architecture and Engineering Guide Genkit Dart Genkit Go Genkit JS Genkit Python LiveAPI Service Skill Migrating from Gemini API in AI Studio to Agent Platform Skill Registry Troubleshoot GKE TPU multi-slice hangs with the MXLA Hang Analyzer Troubleshoot GKE TPU performance degradation with ML Diagnostics Workload Monitoring 

Agent Access Audit

Agent Platform Alert Configuration

Agent Platform Endpoint Management

Agent Platform Eval Flywheel Skill

Agent Platform GenAI Inference Skill

Agent Platform Model Garden Deploy Skill

Agent Platform Model Registry Management

Agent Platform Model Tuning

Agent Platform Prompt Management

Agent Platform RAG Engine Management

Agent Platform Troubleshooting

Agent Platform Tuning Management

API Gateway Remote MCP Server (Public Preview)

Apigee as an Agent Gateway Service Extension

BigQuery AI & ML

Gemini API in Agent Platform

Gemini Enterprise Agent Platform - Managed Agents API Skill

Gemini Interactions API Skill

Gemini platform Architecture and Engineering Guide

Genkit Dart

Genkit Go

Genkit JS

Genkit Python

LiveAPI Service Skill

Migrating from Gemini API in AI Studio to Agent Platform

Skill Registry

Troubleshoot GKE TPU multi-slice hangs with the MXLA Hang Analyzer

Troubleshoot GKE TPU performance degradation with ML Diagnostics Workload Monitoring

Infrastructure Cloud Network Insights Cloud Storage Basics Cloud Storage Bucket Architect Cloud Storage Diagnostic Cloud Storage FUSE Compute Engine Future Reservations & Calendar-Mode Feasibility Compute Engine On-Demand Reservations Designing and Deploying GCP Infrastructure with Application Design Center Filestore Auditing Skill Filestore Autoscale Filestore Log-Based Troubleshooting Filestore NFS File Browser GKE AI/ML Inference GKE Alert Configuration GKE App Onboarding GKE Backup & Disaster Recovery GKE Basics & Critical Gotchas GKE Batch & HPC Workloads GKE Cluster Autoscaler GKE Cluster Creation GKE ComputeClasses GKE Golden Base Image Discovery Expert GKE Golden Path Configuration GKE JobSet Interruption Troubleshooting GKE Manifest Generation Skill GKE Multi-Tenancy GKE Networking GKE Node NotReady Troubleshooting Skill GKE Productionize Skill GKE Reliability GKE Service Networking Skill GKE Storage GKE Storage Troubleshooting Skill GKE TPU Dynamic Slices Monitoring & Management GKE Upgrades & Maintenance GKE Workload Scaling GKE Workload Scaling Troubleshooting Skill GKE Workload Troubleshooting Skill Google Cloud global external Application Load Balancer Configuration Skill Google Cloud Networking Observability Expert Troubleshoot GKE TPU reservation stockouts caused by leaked node pool capacity Troubleshoot GKE TPU slice creation blocked by an unstable MIG Troubleshoot GKE TPU VMs stuck in Compute Engine repair

</details>