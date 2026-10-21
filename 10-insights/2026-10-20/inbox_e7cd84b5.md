---
id: inbox_e7cd84b5
date: 2026-10-20
source_ref: "[[00-inbox/.../inbox_e7cd84b5]]"
title: "How To Use Decision Models for Evals"
url: https://hamel.dev/blog/posts/decision-model-evals/
source: hamel-husain
published_at: 2026-10-20T07:00:00+00:00
fetched_at: 2026-10-21T00:15:46.496968+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用小型分類模型當便宜的 AI 評審，但要先調整判定門檻，別直接用預設 0.50。 **Why** 決策模型（decision models）是 LLM 評審的低成本替代，但許多人不檢查就沿用預設 0.50 門檻，會浪費效能。 **How** 用 100 筆公寓租賃 agent 的 trace，先設定最低 precision/recall 80%，再用分層五折交叉驗證調整門檻、以 F1 為目標，並用 Platt scaling 校準機率。 **What** 測試 Jev 1.13、Perplexity Decider 1.1 27B、Liquid d1 / d1-ultra、Cloudflare Clef Flash、OpenAI Decisions（GPT-6 Luna）。Perplexity、Liquid d1-ultra、OpenAI 達到 80% 門檻；Perplexity 最便宜，每 100 次 eval 0.82 美分、F1 0.79，OpenAI F1 0.87、3.72 美分（約 4.5 倍成本）。"
key_points:
  - "預設門檻 0.50 可能完全失效：例如失敗 trace 都給 0.40、正常給 0.10，0.30 可完美分類，0.50 一個都抓不到；Liquid d1 與 Clef Flash 調整後仍低於 80% 最低要求"
  - "成本對比：Perplexity 0.82 美分 / 100 次 eval（F1 0.79）vs OpenAI Decisions 3.72 美分（F1 0.87），約 4.5 倍"
  - "校準：Clef Flash 某組平均預測失敗率約 8%，實際 60% 含失敗；Perplexity、Liquid d1、Clef Flash 經 Platt scaling 改善，Jev 與 d1-ultra 本來就校準良好，OpenAI 用 Platt scaling 反而略差"
tags: [evals, decision-models, threshold-tuning, calibration, llm-judge]
topics: [engineering.evals]
importance: 3
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How To Use Decision Models for Evals

用小型分類模型當便宜的 AI 評審，但要先調整判定門檻，別直接用預設 0.50。 **Why** 決策模型（decision models）是 LLM 評審的低成本替代，但許多人不檢查就沿用預設 0.50 門檻，會浪費效能。 **How** 用 100 筆公寓租賃 agent 的 trace，先設定最低 precision/recall 80%，再用分層五折交叉驗證調整門檻、以 F1 為目標，並用 Platt scaling 校準機率。 **What** 測試 Jev 1.13、Perplexity Decider 1.1 27B、Liquid d1 / d1-ultra、Cloudflare Clef Flash、OpenAI Decisions（GPT-6 Luna）。Perplexity、Liquid d1-ultra、OpenAI 達到 80% 門檻；Perplexity 最便宜，每 100 次 eval 0.82 美分、F1 0.79，OpenAI F1 0.87、3.72 美分（約 4.5 倍成本）。

### 重點
- 預設門檻 0.50 可能完全失效：例如失敗 trace 都給 0.40、正常給 0.10，0.30 可完美分類，0.50 一個都抓不到；Liquid d1 與 Clef Flash 調整後仍低於 80% 最低要求
- 成本對比：Perplexity 0.82 美分 / 100 次 eval（F1 0.79）vs OpenAI Decisions 3.72 美分（F1 0.87），約 4.5 倍
- 校準：Clef Flash 某組平均預測失敗率約 8%，實際 60% 含失敗；Perplexity、Liquid d1、Clef Flash 經 Platt scaling 改善，Jev 與 d1-ultra 本來就校準良好，OpenAI 用 Platt scaling 反而略差

**原文：** [hamel-husain](https://hamel.dev/blog/posts/decision-model-evals/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# How To Use Decision Models for Evals

Decision models have exploded onto the scene recently, starting with TypeSafe’s Jev, followed by Perplexity’s Decider, Liquid’s d1, Cloudflare’s Clef, and OpenAI’s Decisions API 1 . These models promise fast, inexpensive classification. 
 Decision models are an appealing low-cost alternative to LLM judges 2 for automated evals. But whether they’re the right choice depends on the cost, performance, and latency requirements of your use case. 
 We’ve also noticed people using the default decision threshold of 0.50 without checking whether it works well for their task. This can leave a lot of performance on the table. 
 In this post, we’ll start by showing how to tune thresholds to get the best results from decision models. With those thresholds tuned, we’ll compare cost and performance to help you assess which model fits your use case. Finally, we’ll explore how to interpret model scores when deciding whether to act, and how calibration can make them more useful as confidence estimates. 
 
 What we tested 
 We used 100 traces, or logs of conversations and actions, from an apartment leasing agent. The task is to identify traces containing an error, such as a failed booking or a missed handoff to a human. 3 We used the same dataset and broad failure-finding task in our prior post on automated evals . Here, each decision model returns a failure probability for each trace. 
 We tested Jev 1.13, Perplexity Decider 1.1 27B, Liquid d1 and d1-ultra, Cloudflare Clef Flash, and OpenAI Decisions (GPT-6 Luna) 1 . Each model received the same evaluation criteria. The appendix shows the prompt and the structured version used for Jev. 
 We compare models on two dimensions: 
 
 Performance: We compare each model’s predictions with traces that people have reviewed and labeled as passing or failing. This measures how well the model catches failures while avoiding false alarms. 
 Cost: We calculate API cost from token usage and the provider’s prices. 4 
 
 For brevity, we leave latency aside because it depends on factors outside this experiment’s control. 5 
 
 
 Understanding decision thresholds 
 We assign each trace one of two labels, pass or fail. This is a binary pass/fail eval , which we recommend because it encourages clear criteria and is easier to align with human preferences. 
 Each decision model returns a score from 0 to 1 that estimates how likely a trace is to contain a failure. The APIs turn this score into a decision using a default decision threshold of 0.50 . Traces with scores at or above the threshold are flagged as failures. Using this default without checking it against your data can give you subpar results. 
 For example, a model could assign every failure a score of 0.40 and every passing trace a score of 0.10. Even though this model classifies traces perfectly at a threshold of 0.30, the default threshold of 0.50 would catch nothing. 
 In practice, scores for failures and passing traces will overlap. Lowering the threshold catches more failures but can also raise more false alarms. Choosing a threshold means balancing: 
 
 Precision: The share of flagged traces that contain a known failure. 
 Recall: The share of known failures that the model catches. 
 
 The right tradeoff depends on your business goals. For example, criminal trials set a high bar for conviction to avoid convicting innocent people, emphasizing precision. Cancer screening may emphasize recall, accepting more false alarms to miss fewer cases. 6 For this comparison, we’ll give precision and recall equal weight using the F1 score , their harmonic mean. F1 ranges from 0 to 1, and higher is better. 
 The curves below show how each model scores failures (orange) and passing traces (blue). Taller parts of a curve mean more scores from that class fall in that range. Scores at or above the dashed threshold line are flagged. Use the toggle to compare 0.50 with Optimized for best F1 , which chooses a threshold for each model. 7 

 OpenAI separates the two classes best on this task, which is also reflected in its higher F1 score. 
 It’s also important not to blindly maximize F1 without thinking about your minimum requirements for the classifier to be useful. For example, if this classifier is used for an automated alerting system, I would want a minimum of 80% on both precision and recall so that I’m minimizing false alarms while catching a sufficient number of failures. 
 The chart below shows how precision and recall change at different thresholds. 8 The shaded region marks where both reach at least 80%. 

 Perplexity, Liquid d1-ultra, and OpenAI Decisions meet our requirements, but we still need to choose a decision threshold within the shaded region for each model. In the next section, we’ll discuss how to tune those thresholds. 
 
 Tuning the decision threshold 
 For this example, we’ll optimize F1. For our candidates, we’ll restrict tuning to thresholds that meet both 80% minimums on the training data whenever possible. We leave the other models unconstrained to illustrate the effect of tuning. 9 
 With labeled traces and saved model scores, you can ask a coding agent to tune the thresholds. Below is an example prompt you can modify for your use case: 
 
 Using my saved model scores and binary labels (1 means failure), tune a decision threshold to maximize F1 while requiring at least 80% precision and 80% recall. Use stratified five-fold cross-validation, choosing thresholds on the training examples and measuring performance on the remaining examples. If comparing models, use the same splits for each. Only select thresholds that meet both minimums on the training examples. If none qualifies, report that rather than relaxing either requirement. Report validation precision, recall, and F1, along with any splits where no threshold qualified or validation performance fell below my minimums. Compare with the default threshold of 0.50. Reuse the saved scores without making new model calls. 
 
 Here’s how tuning for F1 changed each model’s performance. We group the three candidates from the precision-recall chart together and show the other models in gray to illustrate how much tuning can help. 

 Our candidate models gained less from F1 tuning than Liquid d1 and Clef Flash, which fell below our minimums. However, even a small shift in precision and recall can affect business costs or the user experience, so choose the tradeoff deliberately. In practice, it’s unlikely that precision and recall are equally important (as we assumed in this post with F1). For example, the F-beta score lets you give precision more weight with beta below 1, or recall more weight with beta above 1. Optimizing a different metric could lead to different thresholds and results. 
 
 
 
 Performance versus cost 
 The chart below compares each model’s F1 (after tuning) against cost, focused on our remaining candidates: 

 The dashed line shows the Pareto frontier among our remaining candidates. For any given F1 score, it identifies the cheapest candidate that meets or exceeds that score. This particular chart is a bit silly as there are only three options, but it’s a useful illustration for how to think about cost vs.&nbsp;performance. 
 Perplexity was the cheapest of these candidates at 0.82 cents per 100 eval runs, with an F1 of 0.79. OpenAI Decisions reached an F1 of 0.87 at 3.72 cents per 100 eval runs, about 4.5 times the cost. 
 
 
 Can we trust the probabilities? 
 Beyond pass/fail evals, you may want to use a decision model’s score as a confidence estimate. But can you take that number literally? For a score of 0.80 to mean an 80% chance of failure, roughly 80% of traces with similar scores should contain failures. 
 The chart below shows each model’s probability calibration : how closely its predicted probabilities match observed outcomes. 10 Each point represents about 20 traces with similar scores. A point on the diagonal means the predicted probability matches the failure rate in that group. Above the line, the model underestimates the risk of failure. Below it, the model overestimates that risk. 
 If the predicted probabilities don’t match the observed outcomes, we can adjust them using another model. The second panel shows one method, Platt scaling , which fits a simple curve to make that adjustment. 11 

 Perplexity, Liquid d1, and Clef Flash move closer to the diagonal after calibration. For example, one group of Clef Flash traces had an average predicted failure probability of about 8%, but 60% contained failures. 
 Jev and Liquid d1-ultra were already well calibrated on this dataset and needed little adjustment. 
 Platt scaling isn’t always the best fit. For example, OpenAI’s probabilities got slightly worse with the version of Platt scaling we used. 12 You can direct your coding agent to perform calibration with the following prompt: 
 
 Using my saved failure probabilities and binary labels (1 means failure), test whether Platt scaling improves each model’s probabilities. Use stratified five-fold cross-validation with the same splits for every model. Fit the calibration mapping on each training split and apply it to the remaining traces. Fit on log-odds, clipping probabilities away from 0 and 1 first. Plot predicted probabilities against observed failure rates before and after calibration. Report Brier scores (lower is better), and explain which models improved or got worse. Reuse the saved scores without making new model calls. 
 
 
 
 Prompt tuning and evaluator scope 
 We kept the eval task in this post broad to make the differences between models easier to see. In practice, we recommend building a separate judge for each failure mode . With a narrower task and more specific guidance, we expect the performance gaps between models to shrink. 
 I like to start with a larger model that has acceptable performance on a task and then try smaller models to see if they can match the larger model’s performance for less cost. Prompt tuning can also be helpful if you have high-quality labels. 13 I discuss how to craft a good judge prompt in this post . 
 
 
 Putting these ideas into practice 
 For this particular dataset, OpenAI had breakout performance at a higher cost. Perplexity and Liquid d1-ultra offer lower-cost options with lower performance. We have observed that model performance varies substantially across tasks and datasets, which means it’s important to measure things yourself. 
 To recap: 
 
 Once you’re satisfied with your judge’s prompt , set minimum precision and recall requirements for your use case. Rule out models that cannot meet these. 
 Tune each model’s decision threshold before comparing performance. Choose a precision-recall tradeoff that fits your business goals. Be intentional, don’t just use F1 score because this post did! 
 If you want to use scores as confidence estimates, check whether the probabilities match observed outcomes. Calibration can help, but you need to measure whether it improves them. 
 Weigh performance against cost and latency for your workload. 
 
 This process is iterative. You may improve the prompt, then need to tune the threshold again or revisit calibration. In this post, we focused on threshold tuning and calibration because we’ve seen many people use decision models off the shelf without considering these factors. 
 You might also be wondering how decision models stack up to LLMs. OpenAI Decisions uses GPT-6 Luna, which delivered our highest F1 at the highest cost, suggesting that harder eval tasks may justify paying more for an LLM. In a broader comparison , Randy Olson found that decision models could match LLMs on classification and routing at lower cost, while LLMs pulled ahead on tasks requiring knowledge and reasoning. 
 None of the ideas discussed in this post are new. Choosing a precision-recall tradeoff, tuning thresholds and comparing performance vs.&nbsp;cost are part of evaluating any classifier. To learn more about these fu

[... truncated for safety ...]

</details>