---
id: inbox_8e0389e2
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-substack-product-for-engineers-jobs-every-engineer-should-automate-with-3233]]"
title: "Jobs every engineer should automate with agents"
url: https://newsletter.posthog.com/p/scheduled-agents
source: substack-product-for-engineers
published_at: 2026-10-26T18:35:35+00:00
fetched_at: 2026-10-27T01:32:27.399068+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把重複又模糊、寫腳本很難處理的工程雜事，交給定時啟動且有長期記憶的 AI agent 自動做。 **Why** 有些工作（驗證小修正、整理使用者回饋）太瑣碎，不值得每次手動下 prompt，但又太模糊，無法用固定腳本處理。 **How** PostHog 用 Scouts（以 cron 觸發、具長期記憶的排程 agent）；agent 產出報告，需要改程式時交給另一個 coding agent 開 PR，agent 提出的 prompt 修改須經人工審核並附過往執行的證據。 **What** 文中列出 6 項自動化：prod 小修正驗證（Andy Maguire 的修正由 agent 隔天以 20 萬行 log 確認；另一案例發現錯誤在 Node SDK 反而增加）、依緊急度 0–100 評分的 feature request 擷取、補漏事件追蹤、每 3 小時診斷 flaky test（自 7 月起 72 份報告、11 份帶來合併修正）、每月人工抽查 agent 回饋（數千份報告）、以及 agent 依人工駁回意見提議修改自身 skill（把「移除 flag＝GA」改成「rollout，非 GA 宣告」）。每項都附可複製的 prompt。"
key_points:
  - "Flaky test 排程 agent 每 3 小時檢查 Trunk 新隔離的測試，自 7 月起產出 72 份診斷報告，其中 11 份促成已合併的修復 PR；價值在降低人類開始修復的成本"
  - "Feature request 彙整加入 0–100 緊急度評分（依客戶原話而非帳戶規模，附一句證據），並讓 agent 在後續執行中參考自己過往的評分"
  - "自我改進 prompt 的條件：提案必須附過往執行的真實證據、經人工審核，並用有版本控管的 skill store 追蹤變更；範例是把「移除 feature flag＝GA」修正為「只代表 rollout」"
tags: [scheduled-agents, posthog, automation, flaky-tests, agent-memory]
topics: [agents.coding_agents, agents.frameworks, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Jobs every engineer should automate with agents

把重複又模糊、寫腳本很難處理的工程雜事，交給定時啟動且有長期記憶的 AI agent 自動做。

**Why** 有些工作（驗證小修正、整理使用者回饋）太瑣碎，不值得每次手動下 prompt，但又太模糊，無法用固定腳本處理。

**How** PostHog 用 Scouts（以 cron 觸發、具長期記憶的排程 agent）；agent 產出報告，需要改程式時交給另一個 coding agent 開 PR，agent 提出的 prompt 修改須經人工審核並附過往執行的證據。

**What** 文中列出 6 項自動化：prod 小修正驗證（Andy Maguire 的修正由 agent 隔天以 20 萬行 log 確認；另一案例發現錯誤在 Node SDK 反而增加）、依緊急度 0–100 評分的 feature request 擷取、補漏事件追蹤、每 3 小時診斷 flaky test（自 7 月起 72 份報告、11 份帶來合併修正）、每月人工抽查 agent 回饋（數千份報告）、以及 agent 依人工駁回意見提議修改自身 skill（把「移除 flag＝GA」改成「rollout，非 GA 宣告」）。每項都附可複製的 prompt。

### 重點
- Flaky test 排程 agent 每 3 小時檢查 Trunk 新隔離的測試，自 7 月起產出 72 份診斷報告，其中 11 份促成已合併的修復 PR；價值在降低人類開始修復的成本
- Feature request 彙整加入 0–100 緊急度評分（依客戶原話而非帳戶規模，附一句證據），並讓 agent 在後續執行中參考自己過往的評分
- 自我改進 prompt 的條件：提案必須附過往執行的真實證據、經人工審核，並用有版本控管的 skill store 追蹤變更；範例是把「移除 feature flag＝GA」修正為「只代表 rollout」

**原文：** [substack-product-for-engineers](https://newsletter.posthog.com/p/scheduled-agents)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Some engineering tasks are too repetitive to be worth prompting every time by hand, but too fuzzy for a script. We've been using Scouts at PostHog to do these instead – scheduled agents with long-term memory that run on a cron trigger. 1 Here are 6 chores we’ve automated this way, with prompts you can copy to build your own version of each. 1. Validating small fixes in prod Everyone's merging more code than ever. And the smaller the PR, the more annoying it is to stop what you’re doing to check it in prod – especially if you already did that in dev. Take this agent-generated string length limit fix that Andy Maguire from our self-driving team merged. It's a tiny change that takes more effort to validate than to push: he'd have to check back for when it hits prod, open error logs, and verify traffic is still flowing. Instead, Andy queued it to merge at 09:19 UTC and moved on to other tasks. It reached prod about an hour later, and the next morning a scheduled agent confirmed the fix held across 200K sandbox-creation log lines using a prompt similar to our PR follow-up skill . It's even more useful in the opposite case. One time, an agent fixed an error that looked like it came from our browser SDK, affecting about 45k users a week. A later validation report showed the error was firing more than before from our Node SDK, which has its own copy of the same utility – exactly the kind of thing a human might not have remembered to check. Steal this prompt: Read https://github.com/PostHog/posthog/blob/master/products/signals/skills/signals-scout-pr-follow-up/SKILL.md and build the equivalent as a scheduled agent for my stack.

Ask me where my deploys, logs, and errors live and where reports should go before writing anything. 2. Capturing feature requests We use agents to find recurring themes in user feedback from in-app surveys, support tickets, Discord, Gong, and Slack. A lesson we recently re-learned was the importance of prioritizing that feedback . When our sales team set up a scheduled agent to post to #feature-request-feed, Raquel from our Blitzscale team said that these automations had been less than useful in her experience: Tyler Crandall , the TAM who created the feed, updated the prompts to factor in urgency. Each one now gets rated based on the call transcript and customer history, which makes up for the facial expressions and voice cues we'd rely on if we did this manually. Plus, the agent can reference its own ratings as context for future runs, too: Steal this prompt: Set up a scheduled agent that runs every weekday morning and pulls feature requests from yesterday's customer calls and Slack channels. Count only what customers said, and skip anything an existing feature already solves.

Log each request with the problem, the ask, a verbatim quote, and a link. Score urgency 0–100 from the customer's own words, not account size, with one sentence of evidence.

Ask me where transcripts and channels live before writing anything. 3. Adding event tracking There are times where even we forget to add instrumentation for product analytics. We added a rule in our AGENTS.md to make AI do this for us moving forward, but we also have a scheduled agent that catches gaps retroactively. It works through recently merged PRs and looks for user-facing actions that are missing event tracking. When it finds one, it cross-checks our live PostHog data to confirm the event never fires, and then files a report with a fix. A coding agent then picks up that report and opens a PR to add the instrumentation . It's useful to have a separate agent doing the actual implementation work. The scheduled agent's original report recommended adding 2 different capture calls in the frontend for this PR . The coding agent, which has more specialized context, found that multiple sources (including MCP and API callers) sent the same request. It chose a better pattern to instrument these as a single capture on server-side, with session IDs and access method. Steal this prompt: Set up a scheduled agent that runs daily and checks recently merged PRs for new user actions shipped without analytics tracking – like a signup, an export, or a server-side API call. Confirm each gap against live event data, and skip anything already flagged.

File one report per gap with the file, line, and a fix for a coding agent to implement with this skill: https://github.com/PostHog/ai-plugin/blob/main/skills/instrument-product-analytics/SKILL.md

Ask me where our code, analytics, and reports live before writing anything. 4. Diagnosing flaky tests Flaky tests are a huge bottleneck for engineers working with AI. They cause intermittent CI failures (usually from hard-to-control factors like timing, shared state, or dependencies). These two were the biggest obstacles slowing down our engineers according to our Q2 internal DevEx survey: To help with this, we added a scheduled agent that checks for newly quarantined Trunk flaky tests every 3 hours and creates (or updates) reports that are actionable enough to be turned into PRs. Since July, it's filed 72 diagnostic reports, and 11 of those have led to merged fixes like this one , which a coding agent wrote using our skill for fixing flaky tests . Even though this loop isn't fully automatable, we still consider it a win because it lowers the cost and friction for a human to start a fix. The diagnostic reports are always kept up to date in the background so that anyone can quickly pick one up at any time. And that's way more likely to happen than if our engineers had to start each one from scratch. Steal this prompt: Set up a scheduled agent that runs every three hours and checks CI for newly flaky or quarantined tests. Diagnose each one with this skill, but stop at a report instead of a PR: https://github.com/PostHog/posthog/blob/master/.agents/skills/fixing-flaky-tests/SKILL.md

Only report what you can back with source or log evidence, and update an existing report for the same test instead of filing a new one.

Ask me where our CI and flaky-test data live before writing anything. 5. Triaging our own agent feedback Another type of feedback we take seriously is the responses from our internal coding agents using our dev environment, which we call hogli . Our monorepo's AGENTS.md instructs agents to use hogli devex:feedback to send a report whenever a hogli command or local dev workflow is broken, slow, or confusing. We have similar systems in place for our PostHog MCP and our AI onboarding wizard . The problem with all of these is that if you prompt agents to send reports, they'll always try to send something . We already have a few thousand reports written by our agents since we shipped it in July, and that’s way too many for anyone on the team to read. Raúl , an engineer on our DevEx team, used to have an automation to triage these by grouping reports into themes, checking if the root issue has already been fixed, roughly ranking by frequency and impact, then committing the notes to a file in our private DevEx repo. Instead, he now just checks on these once a month for a couple of hours, and the reports still lead to low-hanging fixes from across the team, like rewording a preflight warning or updating how code owners are labeled . It's a good example of how some tasks are still better suited for AI-assisted human review, even if they could be solved with scheduled automations. Steal this prompt: Read https://github.com/PostHog/posthog/blob/master/tools/hogli-commands/hogli_commands/feedback.py and add an equivalent feedback command to my repo, plus an AGENTS.md rule telling agents to use it when a dev tool is broken, slow, or confusing.

Then write a monthly triage skill that groups new reports by what actually broke and checks whether each theme still happens on the latest code or was fixed in a merged PR – a theme that stopped being reported is unverified, not fixed. It should give me the top three themes to act on, what's already fixed, and a few rare reports worth reading, and save notes for the next run.

Ask me where reports should go before writing anything. 6. Self-improving prompts With enough data, some of our scheduled agents can even suggest improvements to their own prompts. The key is that they have to include real evidence from past runs, and proposals have to go through human review. We also have a versioned skill store that makes it easy to track these changes. For example, one scheduled agent proactively checks that our product docs are up to date. It once flagged that we should remove the "in beta" notices from two of our docs after a cleanup PR deleted both features' flags. What the agent didn't know was that even though both features were visible to all PostHog users, the team didn't consider them GA yet. When a human reviewer dismissed its reports with handwritten feedback, the agent filed a report suggesting a fix to its own skill: Before: A flag removed from FEATURE_FLAGS in the window usually means the feature shipped to everyone (went GA). After: A flag removed from FEATURE_FLAGS in the window usually means the feature reached everyone, which is rollout, not a GA declaration. Steal this prompt: Set up a scheduled agent that runs daily and flags docs that newly merged code made wrong – removed or renamed features, changed defaults, stale beta labels – with the page, the PR, and a suggested edit. A removed feature flag means a rollout, not a release, so ask before calling anything generally available.

End every run with this self-improvement step, and send me proposed changes for review: https://github.com/PostHog/posthog/blob/master/products/signals/backend/scout_harness/prompt.py#L793-L839

Ask me where our docs and code live before writing anything. Words by Jina Yoon , who is still waiting for agents that can fold her laundry. 🕰️ Scheduled reads How I use skills for everything – Andy Maguire Stanford CS146S: How always-on agents work – Lee Robinson 6 things I’ve learned in 6 years at PostHog – Charles Cook What is Toil in SRE: Understanding Its Impact – Vivek Rau More engineers should consider working in sales – Ryan McCrary How we made claude.ai 3x faster in two weeks – Raymond Wang, Sam Attard, and Issac G. Put us on your cron 💼 Tasks we can’t automate Technical Customer Success Manager - EMEA Technical Customer Success Manager - Americas AI Research Engineer Animator & Motion Graphics Designer Product Manager (ex-founder or ex-product engineer) Site Reliability Engineer (US Pacific Time) 1 Some people call these "background agents," "ambient agents," or "always-on agents." Others describe them as a type of loop or cron.

</details>