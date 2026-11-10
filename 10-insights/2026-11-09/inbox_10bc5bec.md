---
id: inbox_10bc5bec
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/youtube/2344-youtube-ai-engineer-your-kv-cache-can-spot-attacks-on-your-a-da98]]"
title: "Your KV Cache Can Spot Attacks on Your AI Agents - Ari Azarafrooz, Intrinsec AI"
url: https://www.youtube.com/watch?v=1NWnSwCB4NM
source: youtube-ai-engineer
published_at: 2026-11-09T09:00:00+00:00
fetched_at: 2026-11-10T00:05:28.867807+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把推論引擎本來就會算出的 KV cache 當成安全訊號，偵測 AI agent 是否被攻擊。 **Why** 現有防線多在入口與出口用 judge model 或分類器檢查文字，擋不住漏網的攻擊，也不適用於不能讀取輸入輸出內容的隱私場景；但任何輸入最終都會變成模型內部的運算並留在 KV cache。 **How** 三步驟：以自己的 AI 流量學出 KV page 的基準線，找出相對基準線罕見的 page 當異常，再對異常做分類與解釋；可直接整合進 vLLM 等推論引擎做即時偵測，或接在 LMCache 這類 KV 管理層讀取已儲存的 page，告警還能回饋給後續的 tool call 與 policy。 **What** 講者 Ari Azarafrooz（Intrinsec AI）展示兩個示範：語音 agent（Gemma E4B，基準為 72 段、4 位說話者的音檔，以 16 token 為一個 page）能找出夾帶隱藏指令的音檔及其異常 page，並用 KV page 訓練的模型標出個資類別；文字 agent（Qwen3 14B，LMCache 上實際運行）用 ATBench 資料集的 8 類 agent 失效測試，異常偵測前 10 筆告警中約 7～8 筆是有意義的異常。正式環境的難題是模型常換、各自的 KV 座標不同，且 Qwen3 14B 單一 token chunk 約 40MB，即時搬運很慢；講者表示他們正在解決這兩點。"
key_points:
  - "KV-first 安全訊號三步驟：學習流量基準線、找罕見 KV page、分類並解釋異常；不需讀取原始文字，適合隱私場景"
  - "文字 agent 實驗（Qwen3 14B + LMCache、ATBench 8 類失效）：前 10 筆告警約 7～8 筆有意義；語音示範可定位到夾帶隱藏指令的 page"
  - "落地障礙：模型與微調版本更換導致 KV 表示空間不一致，且 Qwen3 14B 一個 token chunk 約 40MB 難以即時搬運"
tags: [kv-cache, anomaly-detection, agent-security, prompt-injection, lmcache]
topics: [security, engineering.inference]
importance: 3
novelty: 4
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Your KV Cache Can Spot Attacks on Your AI Agents - Ari Azarafrooz, Intrinsec AI

把推論引擎本來就會算出的 KV cache 當成安全訊號，偵測 AI agent 是否被攻擊。

**Why** 現有防線多在入口與出口用 judge model 或分類器檢查文字，擋不住漏網的攻擊，也不適用於不能讀取輸入輸出內容的隱私場景；但任何輸入最終都會變成模型內部的運算並留在 KV cache。

**How** 三步驟：以自己的 AI 流量學出 KV page 的基準線，找出相對基準線罕見的 page 當異常，再對異常做分類與解釋；可直接整合進 vLLM 等推論引擎做即時偵測，或接在 LMCache 這類 KV 管理層讀取已儲存的 page，告警還能回饋給後續的 tool call 與 policy。

**What** 講者 Ari Azarafrooz（Intrinsec AI）展示兩個示範：語音 agent（Gemma E4B，基準為 72 段、4 位說話者的音檔，以 16 token 為一個 page）能找出夾帶隱藏指令的音檔及其異常 page，並用 KV page 訓練的模型標出個資類別；文字 agent（Qwen3 14B，LMCache 上實際運行）用 ATBench 資料集的 8 類 agent 失效測試，異常偵測前 10 筆告警中約 7～8 筆是有意義的異常。正式環境的難題是模型常換、各自的 KV 座標不同，且 Qwen3 14B 單一 token chunk 約 40MB，即時搬運很慢；講者表示他們正在解決這兩點。

### 重點
- KV-first 安全訊號三步驟：學習流量基準線、找罕見 KV page、分類並解釋異常；不需讀取原始文字，適合隱私場景
- 文字 agent 實驗（Qwen3 14B + LMCache、ATBench 8 類失效）：前 10 筆告警約 7～8 筆有意義；語音示範可定位到夾帶隱藏指令的 page
- 落地障礙：模型與微調版本更換導致 KV 表示空間不一致，且 Qwen3 14B 一個 token chunk 約 40MB 難以即時搬運

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=1NWnSwCB4NM)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi, I'm Arius, founder of Pinterse AI. Um, this talk is for people who build agents and run their own inference stack or plan to. And if that's you, you associate typically the KB cache, the bird and butter of modern inference engines, usually as a throughput optimization, the keys and values computed per token kept so the model doesn't compute them again. Today, I'll like to show KV cache in a different light. The way agents agent AI agent application could go wrong are keep growing, right? Prom injection, jailbreaks, broken tool calls, sensitive tool calls, sensitive data exposures, hidden back doors and drifts and so forth, right? So the way right now we typically guard against against this numerous ways that an AI agent application could go wrong is by guarding the edge by perhaps passing a judge model that checks the prompts, the inputs and the response outputs against your policy. All right? or you build a classifier for each case. But here is a different light. The model turns every input into a computation before it acts before it decodes before it generates the response before that response becomes another tool call. The KV cache is your engine's record of that computation that modern inference engine for free are using it and reading it. And therefore in this talk I would like to suggest as as a complement to the way Are you already using your own guardrails to use this data and integrate it with your KV cache infrastructure? I refer to this as a KB first security signals and basically three reasons that matters, right? So the data is already there. You pick the gems from the pile your inference stack already was throwing away. It covers the guardrails blind spots because whatever slips past those guardrails, it still becomes computation and it stays in place. So it's perfect for data privacy application for cases where you do not have the luxury to read the inputs and outputs. And the recipe is pretty straightforward, right? It has three steps. You learn a baseline for your AI workload, for your AI inference traffic, how your KB page typically look like, and then find the KV pages that are rare against your baseline, typically your anomalies, and then you can even classify and explain those. So first let's start with where in this stack this integration could happen. The interesting thing about the KV cache is that in a way existence of those had made the inference in a way stateful right. So for example, things like KBK cache management layers such as LM cache stores them from GPU down to remote storage or LLMD and Nvidia dynamo route each new request towards the worker that already holds perhaps that cached KV page. So there are two integration points you you you can integrate those anomaly detection or those classifiers into either you can implement it directly inside of your inference engines vg so forth. The beauty of this approach is that it's real time and and the the the alert that it would perhaps generate could ride along your future tool calls or your future policies. So you can harden basically your policies or guardrails by just generating the computational anomalies that you observe within your inference engines and perhaps you can integrate it with as a as a way of thread discovery in a sense. So you can integrate with your LM cache. So it reads the stored KB pages and find things that don't belong with the rest. Right? So now I want to show you some numbers and and just a very simple hello world use case. if this is actually working and this is a valid approach and for that let me use a use case that has no text to filter at all a voice agent. So here's a case study of a voice agent. In this case it was a gem for E4B. Our baseline was 72 ordinary clips and spoken four voices. We're looking at 16 token pages. Obviously this granular granularity could change but here we just use shorter pages. So we could have more data in the baseline. And then on the test we have different voices and one clean voice and the other one has a hidden instruction within it. And as you can as is shown here not only you can detect these cases just using simple anomaly detection but also you would know which part of um which page which part of your request had this anomalous event. We even went further and we trained a model that uses the KD pages as features and we then we're trying to explain it or tag it with things that are useful. In this case, although it wasn't even trained on audio is able to generate correct information about personal information, home address, location data, travel information, and destination. So now back to text agents. In this case, it was a quan 3 14 billion served live on 11 cache. The one on the left shows you an idea of how attacks and normal traffic would typically separate from each other. And then the one on the right, which is perhaps more meaningful, it was using the AT bench and hogging face. It has its own baseline of benign agent traces and eight kind of agent failure from injected tools description to misinformation and so forth. We look at the top 10 alerts that anomalous anomaly detection would generate and about seven to eight times of out of 10 of these alerts are actually anomalous meaningful and useful anomalous activities. We even went further and we looked at whether there's any kind of anomalous events that stand out more than the rest. Um, two make things hard in production. First models change finetunes and new releases, but also agents that each run on a different model and routers that pick a specialist model per request. That means each model writes its pages its own coordinates. So either you learn every baseline, classifier and explainer which is computationally prohibitive or you have to find a way to map them all into one shared representation space. Second real time means moving big objects. For example, a 1256 token chunk of quen 314 billion is about 40 megabytes of KV compression and the streaming like hashgen could help but moving that for security analysis and acting in real times is still a slow and that's what we solve at in AI. We are looking for teams building their own inference stacks who treat security as a foundational design decision. I hope this was helpful for you. Thank you so much for listening.

</details>