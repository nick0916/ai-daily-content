---
id: inbox_4837f622
source: hamel-husain
source_type: rss
url: "https://hamel.dev/blog/posts/evals-faq/"
author: "Shreya Shankar"
published_at: 2026-09-18T07:00:00+00:00
fetched_at: 2026-10-18T02:56:35.137389+00:00
content_hash: "b1a9b2a2b421c29ed9328dd53b7035eea40b095f81985251413661f086ee17f8"
lang: en
caption_quality: None
raw: true
topics: []
---

# AI Evals: Everything You Need to Know

This document curates the most common questions Shreya and I received while teaching 5,000+ engineers and PMs AI Evals. Warning: These are sharp opinions about what works in most cases. They are not universal truths. Use your judgment. 
 
 How to use this FAQ 
 Browse the questions that interest you, or choose a guide below for a curated reading path through the FAQs and related articles. 
 
 
 
 
 Where are you? 
 This sounds like me 
 
 
 
 
 I’m new to evals 
 I’ve heard the term, but I’m not sure what evals involve or whether I need them. 
 
 
 I don’t know what to test 
 I’m building an AI product, but I haven’t figured out which failures to measure or what good performance looks like. 
 
 
 I don’t trust my eval scores 
 We have evals, but the scores don’t match our judgment of the outputs, or tests pass while users still encounter problems. 
 
 
 My product feels too hard to evaluate 
 Our outputs are subjective, long, or involve many steps. Even a knowledgeable person has trouble deciding whether they’re right. 
 
 
 Evals take too much time or money 
 We’re spending too much effort reviewing outputs, maintaining tests, or running evaluators. 
 
 
 
 
 
 All questions 
 Browse all questions by section. 
 
 
 Getting Started &amp; Fundamentals
 
 Q: What are AI Evals? 
 Q: What is a trace? 
 Q: What’s a minimum viable evaluation setup? 
 Q: How much of my development budget should I allocate to evals? 
 Q: Will today’s evaluation methods still be relevant in 5-10 years given how fast AI is changing? 
 Q: How do I make the case for investing in evaluations to my team? 
 
 Error Analysis &amp; Data Collection
 
 Q: Why is "error analysis" so important in AI evals, and how is it performed? 
 Q: Do I need a reference answer or rubric before annotating data? 
 Q: Should I record problems that aren’t the model’s fault? 
 Q: How many examples do I need for an eval? 
 Q: How do I surface problematic traces for review beyond user feedback? 
 Q: How often should I re-run error analysis on my production system? 
 Q: What should I do when my "gold" eval dataset becomes stale? 
 Q: What is the best approach for generating synthetic data? 
 Q: Are there scenarios where synthetic data may not be reliable? 
 Q: How can I do evals when traces contain sensitive data? 
 Q: How do I approach evaluation when my system handles diverse user queries? 
 Q: How can I efficiently sample production traces for review? 
 
 Evaluation Design &amp; Methodology
 
 Q: Why do you recommend binary (pass/fail) evaluations instead of 1-5 ratings (Likert scales)? 
 Q: How do I combine my evals into a single metric? 
 Q: Should I practice eval-driven development? 
 Q: Should I build automated evaluators for every failure mode I find? 
 Q: What model or LLM should I use to build automated evals? 
 Q: Can I use Jev for evals? 
 Q: How do I know if I can trust my automated eval? 
 Q: What should I do when I can’t get my LLM judge to agree with human reviewers? 
 Q: Should I use "ready-to-use" evaluation metrics? 
 Q: Are similarity metrics (BERTScore, ROUGE, etc.) useful for evaluating LLM outputs? 
 Q: Can I use the same model for both the main task and evaluation? 
 Q: How much context should I give a LLM judge? 
 Q: How do we evaluate a model’s ability to express uncertainty or "know what it doesn’t know"? 
 
 Human Annotation &amp; Process
 
 Q: How many people should annotate my LLM outputs? 
 Q: How can I make AI outputs easier for people to evaluate? 
 Q: Should product managers and engineers collaborate on error analysis? How? 
 Q: Can I help with evals if I’m not a domain expert? 
 Q: How do I evaluate outputs in a language I don’t speak? 
 Q: Should I outsource annotation &amp; labeling to a third party? 
 Q: How do you review a trace that is really large? 
 Q: What parts of evals can be automated with LLMs? 
 Q: Should I stop writing prompts manually in favor of automated tools? 
 
 Tools &amp; Infrastructure
 
 Q: Should I build a custom annotation tool or use something off-the-shelf? 
 Q: What makes a good custom interface for reviewing LLM outputs? 
 Q: What gaps in eval tooling should I be prepared to fill myself? 
 Q: What should an internal eval platform standardize across teams? 
 Q: What’s your favorite eval vendor? 
 Q: How should I version and manage prompts? 
 Q: What should go in the system prompt vs.&nbsp;the user prompt? 
 
 Production &amp; Deployment
 
 Q: How are evaluations used differently in CI/CD vs.&nbsp;monitoring production? 
 Q: How often should I run my evals? 
 Q: What’s the difference between guardrails &amp; evaluators? 
 Q: Can my evaluators also be used to automatically fix or correct outputs in production? 
 Q: How much time should I spend on model selection? 
 
 Domain-Specific Applications
 
 Q: Is RAG dead? 
 Q: How should I evaluate a coding agent? 
 Q: How should I approach evaluating my RAG system? 
 Q: How do I choose the right chunk size for my document processing tasks? 
 Q: How do I debug multi-turn conversation traces? 
 Q: How do I evaluate sessions with human handoffs? 
 Q: How do I evaluate complex multi-step workflows? 
 Q: How do I evaluate agentic workflows? 
 
 
 
 
 
 
 Getting Started &amp; Fundamentals 
 
 Q: What are AI Evals? 
 AI evals are tests that tell you whether an AI system is doing what you want. They give your team feedback when the product drifts from user needs or business goals. The failures they catch also become data you can use to improve the system. 
 More formally, evaluation is the systematic measurement of quality. Each eval checks one behavior on relevant examples and returns a score or structured review. Most AI products need several evals because they can fail in different ways. 
 When you hear the word “evals,” it usually refers to one of two things: model benchmarks or product evals. 
 
 Model benchmarks 
 Model benchmarks compare general-purpose models on shared tasks. Model providers publish these benchmark results when they release new models. Common examples include GPQA Diamond for graduate-level science reasoning, Terminal-Bench for agents doing complex work in command-line environments, and MMLU for knowledge and reasoning across a wide range of subjects. These scores can help you choose a promising model as a starting point. To assess quality on your own tasks you need product evals, which we discuss next. 
 
 
 Product evals 
 Product evals measure whether your specific AI product does what you want it to do. They turn your judgment about what a good product experience looks like into metrics you can track. Product evals encompass all components of your product, including the model, prompts, retrieval, tools, and application code. This flavor of evals are focused on capturing failures that matter to users and the business. 
 Consider an order-cancellation agent. Its product evals might check whether it selected the correct order and waited for the cancellation tool to succeed before telling the user the order was canceled. A high score on GPQA Diamond or Terminal-Bench gives you little information on this, because those benchmarks don’t have access to your systems. 
 There are several mechanisms you can use to implement product evals, including code assertions, human review, LLM judges, and online experiments. The right method depends on the failure being measured, and is discussed in greater detail in this series . 
 In the rest of the AI Evals FAQ , we focus on product evals. It starts with analyzing traces to discover real failure modes. We then turn important failures into targeted evals and use the results to guide changes. Finally, rerunning the evals tells us whether the system improved. 
 
 
 Where to start with evals 
 If you are completely new to product-specific evals, see these posts: 
 
 
 
 
 
 
 
 
 
 Guide 
 What it covers 
 
 
 
 
 
 Part 1 : Your AI Product Needs Evals 
 Build a domain-specific evaluation system with scoped tests, trace review, human evaluation, and experiments. 
 
 
 
 Part 2 : Using LLM-as-a-Judge For Evaluation: A Complete Guide 
 Capture a domain expert’s judgment, automate it with an LLM judge, and validate the judge against human labels. 
 
 
 
 Part 3 : A Field Guide to Rapidly Improving AI Products 
 Use error analysis, realistic data, and trustworthy evals to run a sustained product-improvement loop. 
 
 
 
 ↗ Focus view 
 
 
 
 Q: What is a trace? 
 A trace is the complete record of all actions, messages, tool calls, and data retrievals from a single initial user query through to the final response. It includes every step across all agents, tools, and system components in a session: multiple user messages, assistant responses, retrieved documents, and intermediate tool interactions. 
 Note on terminology: Different observability vendors use varying definitions of traces and spans. Alex Strick van Linschoten’s analysis highlights these differences (screenshot below): 
 
 
 
 Vendor differences in trace definitions as of 2025-07-02 
 
 
 ↗ Focus view 
 
 
 Q: What’s a minimum viable evaluation setup? 
 Start with error analysis, not infrastructure. Spend 30 minutes manually reviewing 20-50 LLM outputs whenever you make significant changes. Use one domain expert who understands your users as your quality decision maker (a “benevolent dictator”). 
 Use a notebook to review traces and analyze data, or build your own custom annotation interface with an AI coding assistant like Claude or Codex. Either way, you can write arbitrary code, visualize data, and iterate quickly. The video below shows a simple annotation interface built inside a notebook. 
 
 
 
 
 
 
 
 Watch “Build Your Own Eval Tools With Notebooks!” on YouTube 
 

 ↗ Focus view 
 
 
 Q: How much of my development budget should I allocate to evals? 
 It’s important to recognize that evaluation is part of the development process rather than a distinct line item, similar to how debugging is part of software development. 
 You should always be doing error analysis . When you discover issues through error analysis, many will be straightforward bugs you’ll fix immediately. These fixes don’t require separate evaluation infrastructure as they’re just part of development. 
 The decision to build automated evaluators comes down to cost-benefit analysis. If you can catch an error with a simple assertion or regex check, the cost is minimal and probably worth it. But if you need to align an LLM-as-judge evaluator, consider whether the failure mode warrants that investment. 
 In the projects we’ve worked on, we’ve spent 60-80% of our development time on error analysis and evaluation . Expect most of your effort to go toward understanding failures (i.e.&nbsp;looking at data) rather than building automated checks. 
 Be wary of optimizing for high eval pass rates . If you’re passing 100% of your evals, you’re likely not challenging your system enough. A 70% pass rate might indicate a more meaningful evaluation that’s actually stress-testing your application. Focus on evals that help you catch real issues, not ones that make your metrics look good. 
 ↗ Focus view 
 
 
 Q: Will today’s evaluation methods still be relevant in 5-10 years given how fast AI is changing? 
 Yes. Even with perfect models, you still need to verify they’re solving the right problem. The need for systematic error analysis, domain-specific testing, and monitoring will still be important. 
 Today’s prompt engineering tricks might become obsolete, but you’ll still need to understand failure modes. Additionally, a LLM cannot read your mind, and research shows that people need to observe the LLM’s behavior in order to properly externalize their requirements. 
 For deeper perspective on this debate, see these two viewpoints: “The model is the product” versus “The model is NOT the product” . 
 ↗ Focus view 
 
 
 Q: How do I make the case for investing in evaluations to my team? 
 Don’t try to sell your team on “evals”. Instead, show them what you find when you

[... truncated for safety ...]