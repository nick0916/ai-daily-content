---
id: inbox_30ea46f6
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-latent-space-building-legal-agents-when-you-can-t-see-0200]]"
title: "Building Legal Agents When You Can't See the Data - Jacob Lauritzen, CTO of Legora"
url: https://latent.space/p/building_legal_agents_when_you_can_t_see_the_data_-_jacob_lauritzen_cto_of_legora/
source: latent-space
published_at: 2026-11-02T22:54:03+00:00
fetched_at: 2026-11-02T23:30:31.426884+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "看不到使用者資料時，如何打造並測試法律 AI agent。 **Why** Legora 的資料屬於律所客戶，團隊無法讀取 agent 的任何 trace，因此不能靠看輸出來除錯與評估。 **How** 由 3 位工程師與 3 位律師依客戶實際工作建立測試環境，概念類似強化學習的「worlds」；trace 經改寫（paraphrase）後，把失敗歸納成 10 或 20 種類型。 **What** Latent Space 專訪 Legora CTO Jacob Lauritzen：他估計模型已能做好約 60% 的法律工作；某次模型釋出後，引用正確率從 70% 升到 99%，Legora 無須改動任何東西。Legora 全部跑在 Azure 上，出於資料隱私考量；工程團隊從 20 人成長到 100 人。產品包含 Tabular Review（百萬格試算表）、Word add-in、Slack 法務 intake bot，以及 agent 與 list 可互相啟動的設計。"
key_points:
  - "看不到 trace 的做法：3 位工程師 + 3 位律師建立仿客戶工作的測試環境，並把改寫後的 trace 歸納成 10~20 種失敗類型"
  - "引用正確率在某次模型釋出後從 70% 升到 99%，Legora 端無須任何改動；Jacob 估計模型已能做好約 60% 的法律工作"
  - "資料隱私促使 Legora 全部跑在 Azure；Tabular Review 為百萬格試算表，被同業連名稱都照抄"
tags: [legal-ai, agent-evals, legora, data-privacy, tabular-review]
topics: [engineering.evals, agents.frameworks, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Building Legal Agents When You Can't See the Data - Jacob Lauritzen, CTO of Legora

看不到使用者資料時，如何打造並測試法律 AI agent。

**Why** Legora 的資料屬於律所客戶，團隊無法讀取 agent 的任何 trace，因此不能靠看輸出來除錯與評估。

**How** 由 3 位工程師與 3 位律師依客戶實際工作建立測試環境，概念類似強化學習的「worlds」；trace 經改寫（paraphrase）後，把失敗歸納成 10 或 20 種類型。

**What** Latent Space 專訪 Legora CTO Jacob Lauritzen：他估計模型已能做好約 60% 的法律工作；某次模型釋出後，引用正確率從 70% 升到 99%，Legora 無須改動任何東西。Legora 全部跑在 Azure 上，出於資料隱私考量；工程團隊從 20 人成長到 100 人。產品包含 Tabular Review（百萬格試算表）、Word add-in、Slack 法務 intake bot，以及 agent 與 list 可互相啟動的設計。

### 重點
- 看不到 trace 的做法：3 位工程師 + 3 位律師建立仿客戶工作的測試環境，並把改寫後的 trace 歸納成 10~20 種失敗類型
- 引用正確率在某次模型釋出後從 70% 升到 99%，Legora 端無須任何改動；Jacob 估計模型已能做好約 60% 的法律工作
- 資料隱私促使 Legora 全部跑在 Azure；Tabular Review 為百萬格試算表，被同業連名稱都照抄

**原文：** [latent-space](https://latent.space/p/building_legal_agents_when_you_can_t_see_the_data_-_jacob_lauritzen_cto_of_legora/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Legora can’t read a single trace of what its agent does for a lawyer. The data belongs to the law firm’s clients. How do you build and test an agent when you can’t see its work? Jacob Lauritzen is the CTO of Legora, one of the fastest-growing companies in legal tech history. The team started in a Stockholm basement with ChatGPT, Swedish law, and a search tool. Today, a lawyer can use Legora to draft and edit Word documents, review 10,000 contracts in a single table, or run due diligence. The agent also coordinates work between lawyers, clients, and other agents. When Legora made its own acquisitions, the team used it for diligence. What we talked about • Why Legora resisted adding a model picker for years, and why it finally added one • Jacob’s estimate that models already do about 60% of legal work well, and why the rest takes a smarter model • How three engineers and three lawyers build test environments modeled on customers’ work, much like the “worlds” used in reinforcement learning • A citation problem where the model got it right 70% of the time, then 99% after one release. Legora didn’t have to change anything. • Why Legora runs everything on Azure and why it doesn’t use ElevenLabs • Tabular Review, the million-cell spreadsheet the industry copied down to the name • How intake works, how agents create lists, and how a list can start another agent • What legal engineers and forward-deployed engineers each do, and who gets to write code • The 300 Spartans slide Jacob used to argue that 20 engineers would be enough forever. Now there are 100, and he still feels short-handed. • Why Jacob finds Fable and Opus too chatty for drafting and likes Astra’s concise writing • Why drafting a long contract is a search problem • Whether model labs will cut off legal tools the way they cut off coding tools • What happens to law firm partnerships, the billable hour, and jobs for junior lawyers Legora is hiring engineers in New York, Stockholm, and London. Chapters 0:00 Cold open 0:40 Meet Jacob Lauritzen, CTO of Legora 1:05 Starting out as underdogs in a Stockholm basement 1:54 How Legora grew from ChatGPT with Swedish law into a legal agent 4:12 The switch from assistant to agent 5:23 Which models Legora uses and why it added a model picker 7:48 Are today’s models good enough for lawyers? 8:20 What agents couldn’t do nine months ago 9:18 Testing the agent in simulated worlds and a 10,000-file data room 10:07 The evals team and Legora’s 100 legal engineers 11:03 When evals didn’t seem worth it and one release took citations from 70% to 99% 12:18 What legal practice could look like in five to ten years 14:18 Will the law firm partnership model survive? 16:40 What happens to paralegals and junior lawyers? 18:00 The billable hour and why earlier legal tech fell short 19:39 Where the money goes now 22:44 How Legora used its own product for acquisition diligence 23:59 How Swedish and American law firms differ 26:12 Product metrics when you can’t read the traces 27:41 Paraphrasing traces and narrowing failures down to 10 or 20 types 28:42 Why data privacy led Legora to run everything on Azure 30:04 Open-weight models and model arbitrage 30:55 Transcription models and why Legora doesn’t use ElevenLabs 33:33 The agent, Tabular Review, projects, and the Word add-in 34:24 How a lawyer uses Tabular Review 35:51 Why a spreadsheet works and what you learn from the first 10 rows 37:53 How the legal intake bot works in Slack 39:11 How agents create lists and lists start agents 40:15 Building products on those same pieces and acquiring Wexler 42:37 What forward-deployed engineers do at Legora 43:52 How legal engineers and forward-deployed engineers onboard a big client 46:43 What’s next for the forward-deployed team over the coming year 47:24 Why Legora resisted building APIs 49:26 Can the agent be the API? 50:12 The 300 Spartans slide and the plan to stay at 20 engineers 51:32 The bets nobody asked Legora to make 53:05 Post-training open-weight models for legal research 54:05 Search, retrieval, and late interaction 54:51 What makes a good legal agent harness and why drafting depends on search 56:25 Which model writes the best draft? 57:03 Hallucinations and Legora’s citation system 57:41 Do lawyers check the citations? 58:19 MapReduce or one big context window for a million-token contract? 1:00:16 Getting anonymized examples and the idea of buying a law firm for its data 1:01:53 Why Jacob advises against default embeddings 1:02:44 Will lawyers work in Legora or through Claude? 1:03:26 Will the model labs cut Legora off? 1:04:24 Law schools and scholarships for computer science majors 1:05:28 Hiring in New York, Stockholm, and London 1:06:09 Why most work eventually becomes legal work Guest — Jacob Lauritzen, CTO of Legora https://legora.com Co-host — swyx, Latent Space Host — Basil Chatha, Forward Deployed https://forwardeployed.com

</details>