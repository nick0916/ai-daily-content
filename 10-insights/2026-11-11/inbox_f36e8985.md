---
id: inbox_f36e8985
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/youtube/0255-youtube-ai-engineer-your-spec-has-bugs-catch-them-before-you-8373]]"
title: "Your Spec Has Bugs. Catch Them Before Your Agent Codes. - Rajath Mahendrappa Kotyal, AWS"
url: https://www.youtube.com/watch?v=0EnLxIbAvYk
source: youtube-ai-engineer
published_at: 2026-11-11T23:00:00+00:00
fetched_at: 2026-11-12T03:00:22.274087+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在 agent 開始寫程式前，先用形式化方法檢查規格本身有沒有互相矛盾或遺漏。 **Why** 規格中單看合理的句子合在一起可能衝突；引用的公開研究指出模糊 prompt 會使程式碼準確度下降 20–40%，且產生兩倍的 regression。 **How** 三步流程：LLM 先自行精煉措辭；失敗則把英文規則轉成 SMT 公式交給 solver 檢查；偵測到歧義時讓 LLM 多次（7 或 10 次）翻譯，按邏輯等價分群，再請使用者釐清或棄權不實作。 **What** AWS 自動推理團隊的 Kiro specification analyzer，可找出規格中的歧義、衝突（如「缺貨時轉為 back order」vs「不得有 back order」）與缺口（某狀態沒有規則涵蓋）。分工是 LLM 翻譯、solver 檢查、人類決定，因為領域知識只有使用者能保證。"
key_points:
  - "範例：「缺貨時下 back order」與「不得下 back order」兩條規則單看合理、合併則互斥"
  - "對同一句規格多次翻譯成 SMT 並按邏輯等價分群，判斷是模型本身歧義還是規格不清"
  - "分工原則：LLM 翻譯、solver 檢查、人類決定；無答案時用 LLM judge 或放棄實作該部分"
tags: [spec-driven-development, formal-methods, smt-solver, kiro, automated-reasoning]
topics: [agents.coding_agents, engineering.evals]
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Your Spec Has Bugs. Catch Them Before Your Agent Codes. - Rajath Mahendrappa Kotyal, AWS

在 agent 開始寫程式前，先用形式化方法檢查規格本身有沒有互相矛盾或遺漏。

**Why** 規格中單看合理的句子合在一起可能衝突；引用的公開研究指出模糊 prompt 會使程式碼準確度下降 20–40%，且產生兩倍的 regression。

**How** 三步流程：LLM 先自行精煉措辭；失敗則把英文規則轉成 SMT 公式交給 solver 檢查；偵測到歧義時讓 LLM 多次（7 或 10 次）翻譯，按邏輯等價分群，再請使用者釐清或棄權不實作。

**What** AWS 自動推理團隊的 Kiro specification analyzer，可找出規格中的歧義、衝突（如「缺貨時轉為 back order」vs「不得有 back order」）與缺口（某狀態沒有規則涵蓋）。分工是 LLM 翻譯、solver 檢查、人類決定，因為領域知識只有使用者能保證。

### 重點
- 範例：「缺貨時下 back order」與「不得下 back order」兩條規則單看合理、合併則互斥
- 對同一句規格多次翻譯成 SMT 並按邏輯等價分群，判斷是模型本身歧義還是規格不清
- 分工原則：LLM 翻譯、solver 檢查、人類決定；無答案時用 LLM judge 或放棄實作該部分

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=0EnLxIbAvYk)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hi everyone, my name is Rajat Kotial. I'm part of the automated reasoning group at AWS. And today I'm going to talk about a project I worked on recently called KO specification analyzer. And um we use certain techniques which involves formal methods and automated reasoning to prove specification that goes to your coding agent before it writes code. So let's take a certain bug right this is a specification uh snippet and there are two rules for example and uh the rule two says when an order is submitted and this is for a a general e-commerce website let's say when an order is submitted and the inventory is unavailable we place the order as a back order which makes sense when you read it individually and there's also another rule in the same specification file uh which you hand to the coding agent which says u no order shall be placed as a back order and this is a rule we've set so individually read these two lines make sense right but in when an LLM reads this reads both the rules together both cannot hold true at the same time so we need to make sure the we resolve this ambiguity that the LLM is observing. And uh the scope and the reason we uh put an effort into this project is based on public research and recent research, we've observed there's a 20 to 40% drop with unclear prompts on the accuracy the LLM uh generates on the code accuracy, right? and 60 to 90% of valid code is still wrong after it writes it. And also in that case we observe two times the more more regressions when we uh deploy that code. So where do bugs like these hide? Right? We want to detect these bugs before they reach the codebase. And the way only way to do that it's similar to how we write design docs. Similar to how we draw diagrams and flowcharts to make sure the flow is set before we write any code. We want to verify that without a human or anyone reading these files as the first reviewer in one sentence. Let's say the ambiguity and wording wrong level of detail but across sentences we can observe conflicts and gaps in the specification or rules. Right? sentences need reviews that need search in between them and ambiguity searches. So we have a three-step process to do this where the LLM will first refine it. It'll try to clean up the wording on its own and u if it succeeds then well and good but if it cannot we then formalize the um English language into SMT formulas. So, SMT lib is a certain set of type of function which we pass to a SAT solver a satisfiability checker where it's going to give out a boolean saying this expression that you've given me is valid true or false invalid and then once the solver gets back to us if that expression is valid then we don't do anything. But if it detects any ambiguity between two sentences or within a sentence where there's two meanings to a sentence, then we detect that and tell the LLM to recheck that sentence and it's going to reiterate on that. For example, the rules we saw we've seen when order is submitted and inventory is unavailable, we shall place the order as a back order. And in SMT format, it kind of looks like this. This is like a math formula, right? Once we go deeper, we once we detect this, we also do a three-step process again where we sample the translations again and again. We ask the LLM to translate it seven times or 10 times and to understand whether this LLM is behaving this way uh based on its inherent capabilities or is something affecting it to behave this way and then based on logical equivalence of these seven or 10 um different set of interpretations by the LLM we cluster them on logical equivalence which sets which uh um entries came under which uh assumptions that the LLM made for itself and then we accept or ask the user to clear out the ambiguity or abstain from implementing that in the codebase. This is an example of asking the human um what you want to do with that spec rule that was um perhaps contradicting. remove the record is very a very vague statement. The LLM cannot can interpret anything it wants but we shouldn't allow that to happen and we either give two options we keep it as is the record is deleted or we retain it and but hide it from the users which one does the user prefer. Um a conflict is when the examples we example we saw rule one is conflicting with rule three and a gap is where no rule covers an idle order in this example where the LLM detected an actual sorry process or pipeline detected there's no um entry for this rule where you are missing something all in Well, it cannot do a lot of things. End of the day, we want to make sure there is no oracle uh for for specification correctness other than the user. User needs to make sure to check every part of the snippet part of the rule book before sending it to the LLM. And um we as a tool only can help them and the user is more important here because of implicit domain knowledge. The LLM doesn't know a lot of domain knowledge and there's no guarantee I mean LLM only uh user can give that guarantee right and there's thin evidence right now for formalization and how it can be used in agents we are emerging in this technology what do we take back from this um talk check the spec always before you pass it down to the agent uh cluster the translation We what we do is we cluster the translation by logical equivalent to determine the different LLM interpretations and where it's genuinely going wrong. The LLM translates, the solver checks and the human decides. We give the human uh options and if there's no answer to that, we use LLM judges or abstain from implementing that piece. Here are the references and u this work has been majorly contributed by my team um Andrea Jin Stefan and Delmos. You can check out their blog in the website link provided and um del deeper into this. Thank you.

</details>