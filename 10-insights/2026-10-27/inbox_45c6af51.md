---
id: inbox_45c6af51
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2338-lobsters-ai-fuzzers-vs-ai-comparing-fuzzilli-and-big-0b51]]"
title: "Fuzzers vs. AI: Comparing Fuzzilli and BigSleep on JavaScript Engines"
url: https://projectzero.google/2026/10/fuzzing-v-AI.html
source: lobsters-ai
published_at: 2026-10-27T14:08:23-05:00
fetched_at: 2026-10-27T23:51:31.208745+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Fuzzilli 與 BigSleep 比較：兩者在 V8 找到的漏洞重疊有限，互補而非取代。 **Why** 社群想知道 LLM 是否會取代傳統 fuzzing，作者用 2026 年 4 至 9 月的 bug 數據與重現實驗來回答。 **How** 以 Chromium bugtracker 與 ClusterFuzz 資料篩出可行動的漏洞並去重，另做實驗讓 BigSleep 重現 Fuzzilli 過去找到的漏洞。 **What** 可行動的 type:vulnerability 漏洞中，BigSleep 45 個、Fuzzilli 37 個；實際 bug 重疊約 25%（81 個中 20 個），專門實驗估計理論重疊約 60%；作者建議兩種方法並用。"
key_points:
  - "BigSleep 45 個、Fuzzilli 37 個可行動漏洞（2026/4–9，type:vulnerability 且有修復 commit）"
  - "實際 bug 重疊約 25%（81 中 20），專門實驗估計理論重疊約 60%"
  - "Fuzzilli 持續運行，通常數小時內抓到新 commit；BigSleep 每天跑一次，回報延遲約 1–2 天"
tags: [fuzzing, v8, bigsleep, fuzzilli, vulnerability-discovery]
topics: [security]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Fuzzers vs. AI: Comparing Fuzzilli and BigSleep on JavaScript Engines

Fuzzilli 與 BigSleep 比較：兩者在 V8 找到的漏洞重疊有限，互補而非取代。

**Why** 社群想知道 LLM 是否會取代傳統 fuzzing，作者用 2026 年 4 至 9 月的 bug 數據與重現實驗來回答。

**How** 以 Chromium bugtracker 與 ClusterFuzz 資料篩出可行動的漏洞並去重，另做實驗讓 BigSleep 重現 Fuzzilli 過去找到的漏洞。

**What** 可行動的 type:vulnerability 漏洞中，BigSleep 45 個、Fuzzilli 37 個；實際 bug 重疊約 25%（81 個中 20 個），專門實驗估計理論重疊約 60%；作者建議兩種方法並用。

### 重點
- BigSleep 45 個、Fuzzilli 37 個可行動漏洞（2026/4–9，type:vulnerability 且有修復 commit）
- 實際 bug 重疊約 25%（81 中 20），專門實驗估計理論重疊約 60%
- Fuzzilli 持續運行，通常數小時內抓到新 commit；BigSleep 每天跑一次，回報延遲約 1–2 天

**原文：** [lobsters-ai](https://projectzero.google/2026/10/fuzzing-v-AI.html)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Part 1: Production Statistics

Part 2: Overlap

Part 3: Shape of Bugs

Part 4: Conclusion

Summary

Introduction

Bugtracker Overlap

Overlap Experiment

Summary

BigSleep: Chrome Bug 449760249 (October 2025)

BigSleep: Chrome Bug 443765373 (September 2025)

Fuzzilli: Chrome Bug 40076141 (November 2023)

Overview

Memorization

Difficulty

Components

Prompting

Background: TDZ and Hole Check Elision

The Original Vulnerability

Discovery of the Variant

Proof of Concept

Background: Exception handling in V8

The Bug

Background: Value Representation in V8

The Testcase

The Graph Builder

The MaglevPhiRepresentationSelector

The Conflict

Project Zero compared two automated tools used by Google to find vulnerabilities in Chrome’s JavaScript engine, V8, on a regular basis. Fuzzilli is a generative JavaScript engine fuzzer and BigSleep is an LLM-based bug finding system. In the past six months, BigSleep found more vulnerabilities than Fuzzilli (45 versus 37) with a 25% overlap in the specific bugs reported. Since this comparison methodology has a tendency to underestimate overlap, we also performed dedicated experiments to test theoretical overlap in vulnerabilities reported since 2023. These experiments estimated overlap at roughly 60%. Regardless of which value is accurate, a substantial portion of vulnerabilities were discoverable by only LLMs or only fuzzing. While it is extremely promising that LLMs have become able to find so many vulnerabilities so quickly, fuzzing and LLMs are still complementary approaches. We recommend vendors perform both fuzzing and agentic analysis of their code to maximize the number of vulnerabilities that get reported before they impact users.

Fuzzing has long been successfully applied to software projects such as Chrome or V8 (Chrome’s JavaScript engine) to detect bugs. Recently, the arrival of powerful LLMs able to read, reason about, and write code is causing a transformative change to software development and software security. With hundreds, sometimes thousands of new bugs and vulnerabilities having been discovered in well-fuzzed targets, a natural question arises: how do new LLMs compare to “traditional” fuzzers? Are they starting to replace them or do the two approaches complement each other? To help answer this, we look at three key questions:

How many bugs does each approach find in the real world?

What is the overlap between the two approaches?

What is the “shape” of bugs discovered by one system but not the other?

For this blog post, we will limit ourselves to two concrete systems: Fuzzilli , a JavaScript engine fuzzer, and BigSleep , an agentic bug finding system. Both of these systems run in production and automatically look for bugs in newly added code, which makes them fairly directly comparable. Specifically, Fuzzilli runs continuously across many instances, with the first ones usually picking up new changes within a few hours, while BigSleep currently runs once per day and is prompted to review new commits and write proof-of-concept testcases for any bugs it discovers. Both systems report bugs through Clusterfuzz , which will do basic crash triaging, then file bug reports in Chrome’s issue tracker.

We also limit ourselves to V8 as a target, a high-performance JavaScript and WebAssembly engine with a sophisticated and mature testing and fuzzing setup. In particular, Fuzzilli is a special-purpose fuzzing tool designed to find bugs in these engines. The usually complicated nature of these bugs makes for an interesting “playground” to compare the two approaches’ ability to find deep and complex bugs in well-tested software. We leave it to future work to perform similar analysis on a broader set of targets, fuzzers, and agentic bug finding systems.

We will now look into each of the three main questions in a dedicated section. Each section will first summarize the general approach, then describe the methodology in detail (often as bullet points, so you can skip those blocks if you don’t care too much about the details) before exploring the results. We conclude with an attempt at interpreting the results to get a picture of the current state of fuzzing vs. AI.

This is the simplest part to analyze, although with some caveats we’ll see in a bit. The basic idea is to query issues from Chromium’s bugtracker (where V8 bugs are tracked) and extract various statistics from there. This is especially easy since there’s a dedicated hotlist for each of the two systems. We limit our analysis to the six months from April to September 2026 as the automatic BigSleep pipeline only became active in April this year. As such, our raw data comes from the following two bug tracker queries:

Fuzzilli: hotlistid:5433121 created:2026-04-01..2026-09-30

BigSleep: hotlistid:8067258 created:2026-04-01..2026-09-30

From there, the raw numbers of bug reports are:

Fuzzilli: 316

BigSleep: 441

Small win for BigSleep. However, this includes all types of bugs, and BigSleep initially also found a lot of configuration and integration issues in V8, for example crbug.com/503869331 where the unsafe flag blocking mechanism didn’t work properly yet. These are legitimate issues, but less relevant for our comparison since there’s little real-world security impact. One easy way to get rid of these is to look specifically at vulnerabilities by limiting the results to type:vulnerability :

Fuzzilli: 178

BigSleep: 95

Suddenly a clear win for the fuzzers? Not quite. There are still some problems with this data, notably duplicates and unactionable reports (e.g. bugs closed as WAI ). At first, this seems like a simple thing to fix: just include another constraint such as status:(fixed | verified) . Unfortunately, things are a bit more complicated. Take for example Fuzzilli bug crbug.com/511935486 . The events on this bug are basically:

The bug is filed by Clusterfuzz on May 11 and assigned to an engineer

The bug is closed by Clusterfuzz as the testcase no longer reproduces later that same day

As such, this bug received zero developer interactions. Most likely what happened here is that this bug was a duplicate of another bug, crbug.com/511210507 , but Clusterfuzz didn’t realize it as the crash signature (derived from the stack trace) was slightly different. When the other bug received a fix, the testcase stopped reproducing on Clusterfuzz, which closed the issue.

Maybe the best thing we can do is to look at “actionable” bugs, defined as those that are not marked as duplicates or WAI and that received at least one fix commit referencing them. Then, looking at only Type-Vuln bugs filters out a lot of the less-relevant BigSleep bugs, even though these were “actionable”. With that, the final picture looks like this:

So in terms of vulnerabilities, it’s roughly a tie (small advantage BigSleep) at the moment: 45 vs. 37.

This naturally raises the question of cost: how expensive is each of the two approaches and what does that mean in terms of cost-per-bug? Unfortunately, it’s challenging to make a comparison at this stage in the research. While some effort has been dedicated to making Clusterfuzz more efficient, similar effort has not been expended for Big Sleep and neither system is particularly calibrated for an optimal cost-per-bug ratio.

The next question is how much these approaches overlap each other. For this, our approach is twofold: we first attempt to find an answer in the bugtracker, by trying to identify bugs discovered by both systems. Next, we run a dedicated experiment in which we let BigSleep try to rediscover old Fuzzilli bugs.

The basic idea is to see which bugs were found by both systems, so we’re effectively looking for duplicate bug reports. Similar to part 1, there are a few steps we need to take to ensure we get a somewhat accurate picture:

First, we look for bugs filed by one system that get deduplicated into a bug filed by the other. For example crbug.com/522410841 which is a duplicate of crbug.com/522860268 . This is a clear overlap.

Next, we need to take into account that many “unactionable” reports (those with zero associated fixes) are often duplicates. For those reports, we need to find the commit that fixed them, then look at the bug associated with that commit, and treat these two bugs as duplicates. This can be a multi-prong relationship: both bug X found by BigSleep and bug Y found by Fuzzilli might be a duplicate of bug Z reported by someone/something else. In that case, that bug still counts as overlap.

Then, we need to realize that many duplicates never receive a bugtracker entry since they are already deduplicated at the Clusterfuzz level (since both Fuzzilli and BigSleep rely on Clusterfuzz for basic triage and bug filing). As such, we need to query Clusterfuzz’s underlying database to find more duplicates.

Finally, we need to decide what to do with separate bugs that get fixed by the same CL, for example the four bugs fixed by crrev.com/c/7965120 . While this can legitimately happen for distinct bugs, it’s probably more likely for the bugs to be duplicates (such as in this case), and so we count them as such.

With all the different types of deduplication, we get this final picture:

Again, looking at just the actionable vulnerability reports (likely the best measure), we see an overlap of roughly 25% (20 out of a total of 81), with a slight majority of these found first by Fuzzilli and later by BigSleep.

The second way to measure the overlap is to run a dedicated experiment in which we try to re-discover bugs found by one system in the past using the other. Specifically, here we try to re-discover old Fuzzilli bugs using a BigSleep setup that’s as close to the production configuration as possible. For each bug we collect the commit that (likely) introduced the bug, and ask the agent to review those changes just as in the production CI environment. Note that the other direction, trying to rediscover past BigSleep bugs with Fuzzilli is more difficult to set up, since fuzzers cannot easily be given a similar “starting point”. Moreover, for many of these bugs we already know the outcome of such an experiment: the majority of “historic” BigSleep bugs (e.g. those from 2025 ) were found after fuzzers like Fuzzilli had already been fuzzing vulnerable builds for months, sometimes years. So they would most likely also not rediscover them in an experiment (except perhaps in a few cases where Fuzzilli was since updated to support new language features). Similarly, in production, BigSleep only reports crashes with a delay of 1-2 days (as there’s currently only one run per day). As such, fuzzers also get a head-start there.

In more detail, here is how the experiment is set up:

We start with a list of historic Fuzzilli bugs (from early 2023 until mid-2026) by querying the bug tracker hotlist. This gives us around 1150 raw bugs .

We restrict this to only type:vulnerability as these are the types of bugs we care most about and will remove some “noise” as above. We are left with roughly 600 vulnerabilities.

Next, we filter this list down to bugs that reproduce in the environment used by the agent. This involves two parts:

Bugs that reproduce on an x64 debug+asan build of the d8 shell as provided by Chrome’s public build infrastructure . This is important because many bugs only reproduce in special builds, for example because they are architecture-specific or need certain compile-time features.

Bugs that can be reproduced without special flags. The problem here is that fuzzers often set custom flags, either to enable in-development features (e.g. --experimental-wasm-jspi in crbug.com/361123483 ) or to turn on different fuzzing modes that make certain types of bugs easier to discover (e.g. --deopt-every-n-times in crbug.com/362784006 ). However, we can’t let the agent set arbitrary flags on historic V8 builds as these didn’t have a “safe-flags only” mode (leading to many false-positive crashes), and we also don’t want to tell the ag

[... truncated for safety ...]

</details>