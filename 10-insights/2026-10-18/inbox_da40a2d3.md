---
id: inbox_da40a2d3
date: 2026-10-18
source_ref: "[[00-inbox/2026-10-18/0102-lobsters-vibecoding-speeding-up-code-review-with-small-chang-a2dc]]"
title: "Speeding up code review with `small-change`"
url: https://lethain.com/small-changes/
source: lobsters-vibecoding
published_at: 2026-10-18T19:38:15-05:00
fetched_at: 2026-10-25T01:27:20.250520+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "以「小改動快速通道」緩解 PR 審查瓶頸，只讓低風險變更自動核准。 **Why** 合併量大增後，p50 PR 審查時間從約 33 分鐘拉長到約 77 分鐘，審查成為瓶頸。 **How** 由 CI 檢查判定 small-change（小於 1,000 行、無 P1/P2 AI 審查發現、作者在該服務有 10 次以上合併 PR 等條件），`review-small-change` 技能只做核准或忽略、不留言。 **What** 作者所在公司 Imprint 的平均工程師合併 PR 量是兩年前的 4 倍，事故下降 42%、嚴重事故下降 78%（半年對半年）；目前約 10% 的變更符合資格。"
key_points:
  - "small-change 條件：小於 1,000 行、無 P1/P2 AI 審查發現、作者在該服務有 10 次以上合併 PR；共用函式庫不適用，每個 repo 有 .small_change 檔做路徑排除"
  - "review-small-change 技能只能核准或忽略、不留言，目的是避免「meat proxy review」（只當人工代理的審查）成為瓶頸"
  - "目前約 10% 變更符合資格；作者表示仍處早期，成敗取決於擴大比例並同步強化驗證機制"
tags: [code-review, pull-requests, small-change, ai-code-review, engineering-velocity]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Speeding up code review with `small-change`

以「小改動快速通道」緩解 PR 審查瓶頸，只讓低風險變更自動核准。

**Why** 合併量大增後，p50 PR 審查時間從約 33 分鐘拉長到約 77 分鐘，審查成為瓶頸。

**How** 由 CI 檢查判定 small-change（小於 1,000 行、無 P1/P2 AI 審查發現、作者在該服務有 10 次以上合併 PR 等條件），`review-small-change` 技能只做核准或忽略、不留言。

**What** 作者所在公司 Imprint 的平均工程師合併 PR 量是兩年前的 4 倍，事故下降 42%、嚴重事故下降 78%（半年對半年）；目前約 10% 的變更符合資格。

### 重點
- small-change 條件：小於 1,000 行、無 P1/P2 AI 審查發現、作者在該服務有 10 次以上合併 PR；共用函式庫不適用，每個 repo 有 .small_change 檔做路徑排除
- review-small-change 技能只能核准或忽略、不留言，目的是避免「meat proxy review」（只當人工代理的審查）成為瓶頸
- 目前約 10% 變更符合資格；作者表示仍處早期，成敗取決於擴大比例並同步強化驗證機制

**原文：** [lobsters-vibecoding](https://lethain.com/small-changes/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Why review pull requests?

Small steps with small-change

Meat proxy review

fleet : centrally orchestrated harness

Results / next steps / reception

Imprint’s average engineer is merging 4x more PRs than 2 years ago. Yay.
Aggregated behind the average is something even more interesting:
we have two teams that are merging 10x their PRs over that period.
One engineer is merging 25x the PRs per week of our average engineer two years ago,
and a number of others are closing in on that number.
That’s pretty neat, and the slope of the line suggests our average in a year is going to look much closer to
today’s p90 than today’s p50.
Even more importantly, we aren’t just shipping more, our quality has improved:
incidents are down 42% half-over-half, and critical incidents are down 78% half-over-half.
I think we’ve always known the quality/velocity tradeoff wasn’t a particularly useful
construct, but that’s undeniable today.

As we’ve walked this path, we– like everyone else progressing down it–have run into the problem of pull request review. The p50 pull request review took about 33 minutes to complete
2 years ago, but now takes us about 77 minutes. The slope here correlates tightly with the number of
pull requests getting merged. Tightly enough that addressing it became one of my priorities for the week.

We solved it! Just kidding, we’ve absolutely not solved it, but I think our current
approach is an interesting one, which we call the small-change .

The work discussed here was shaped and done by many folks at Imprint including Dan, Joy, Daniel, Lenny, Taylor, Ted, and Annie, among many others.

There are four reasons we review pull requests:

In the modern development paradigm, we think there is a better solution for each of these problems.
But, we also want to make these changes very cautiously.

We believe we move fast by finding narrow, contained ways to validate new practices,
so to iterate our way into an effective solution, we’ve developed the concept of a small-change . Here’s how it works:

review-small-change which takes a list of repositories and reviews all open, non-draft, small-changes,
including providing approval if they meet the review’s criteria (all checks pass including small-change check,
and not touching on sensitive topics such as payments and security).

Importantly, this skill has only two options: approve or ignore. It never comments on the PR to avoid
the proliferation of “ meat proxy review”
which has become a bottleneck-pretending-to-be-a-solution on some teams

review-pr-cluster which reviews batches of pull requests to identify common themes that came up, and suggest opportunities
for discussion and adding verifications

This took about two days of infrequent attention to implement and rollout,
although I imagine we will be tuning the knobs here for a long time. Maybe forever.

I mentioned this in 4.1 above, but meat proxy review has become
an interesting bottleneck for many teams. It’s a particularly difficult bottleneck because it initially looks like a solution,
but it makes things worse. The pattern is roughly:

In every case that meat proxy review is performed, the team would get better outcomes by
investing into the centralized review mechanism, the harness’ loop for addressing the centralized review’s feedback,
and simply stamping approval.

I’ll briefly mention our other approach to reducing code review
volume, which anchors on our centrally-orchestrated harness, fleet .
(Which is similar to Stripe’s Minions although not following the one-shot approach in particular).
We rely on fleet to implement and verify software in a highly controlled harness running in the cloud, with independent
evaluation mechanisms to identify the correct number of independent reviewers for
any given change. That number can be as low as one (e.g. fleet writes, one human reviews)
for changes evaluated as safe.

I’ll be honest, it’s too early to give a useful result here.
From early results, about 10% of changes qualify as a small-change .
Those are now eligible for very fast approval, and generally get it unless
they trip a flag, generally due to touching a security or money adjacent topic.

While 10% is a small percentage, the core concept here is working,
and ultimately will succeed or fail based on our ability to expand
that percentage over the next few months in tandem with expanding
our verification mechanisms to be increasingly comprehensive.
This is ultimately going to fail or succeed depending on our ability
to improve our verifications, which does require more difficult sorts of techniques
to accomplish in low scale-complexity, high domain-complexity software
than in the high scale-complexity, low domain-complexity products where many techniques
like incremental rollouts are exceptionally effective. (Don’t get me wrong,
they still work, they just provide less coverage when most users have different configuration and behavior.)

Folks have not been uniformly excited about this,
it’s a substantial change from how we’ve learned to be good engineers,
and it’s uncomfortable to reevaluate whether a long-held best practice has become merely dogma.
The most energizing part of the current cycle is that we get to reevaluate these
practices we grew up on every week; the most painful part of the current cycle is that
we’re likely to fall behind if we ever stop reevaluating them.

Knowledge sharing between author and reviewer – software engineering is generally learned via
apprenticeship, and reviews are a primary mechanism of experienced engineers teaching others what
good software looks like. We believe the current volume means that this knowledge sharing
will have to move towards operating on clusters of pull requests, rather than individual pull requests

Preventing errors – review has always been an expensive time to catch errors,
and we believe that effective CICD along with harness verification techniques like poteto’s pstack are more effective mechanisms
for preventing errors than review

Preventing malicious behavior – my experience is that even careful code review will generally
miss competent malicious behavior, although fortunately most malicious behavior is incompetent.
We believe both sorts of behavior are best identified using a combination of fixed rules (modifying
these specific objects/classes/files requires review), anti-abuse mechanisms that we’ve refined in
our LLM-based member support experiences, auditing, and audit log inspection

Compliance obligations in our documented controls – these can be changed, but today they require that
an independent human reviews changes in a subset of our repositories

When a pull request is marked ready, CICD determines whether it is eligible to be a small-change .
This is represented as a passing Github check. There is also a label for visibility,
but it is the check itself, managed by the build and not human modifiable, that determines eligibility.
(The label is used for initial filtering, but the check is still independently verified.)

Something is a small-change if it meets all of these criteria: It is less than 1,000 lines of code There are no p1 or p2 findings from our ai-code-review automated review bot The author has “experience” in the service or application, defined as 10+ prior merged pull requests
into that service or application’s directories.
For changes working across multiple services or applications, the author must have experience in all of them to qualify Impacts fewer than N distinct services or applications. N is 1 on our frontend monorepo,
and N is 3 in our backend monorepo, where typical changes will modify both a gRPC service and a common HTTP gateway Shared libraries and utilities files are not eligible for small-change Each repository has a .small_change file which allows per-path customization while we continue to tune the behaviors.
For example, a service dealing with money movement can be excluded

It is less than 1,000 lines of code

There are no p1 or p2 findings from our ai-code-review automated review bot

The author has “experience” in the service or application, defined as 10+ prior merged pull requests
into that service or application’s directories.
For changes working across multiple services or applications, the author must have experience in all of them to qualify

Impacts fewer than N distinct services or applications. N is 1 on our frontend monorepo,
and N is 3 in our backend monorepo, where typical changes will modify both a gRPC service and a common HTTP gateway

Shared libraries and utilities files are not eligible for small-change

Each repository has a .small_change file which allows per-path customization while we continue to tune the behaviors.
For example, a service dealing with money movement can be excluded

Our Slack automation tags every reference to a pull request with reacji labeling the state of that pull request,
for example if it has failing tests, if it has been approved but tests are still running, or if it is ready to merge.
We added a small-change reacji that indicates which of those pull requests meet the small-change criteria

In our internal skills repository, we created two skills that have been distributed across harnesses: review-small-change which takes a list of repositories and reviews all open, non-draft, small-changes,
including providing approval if they meet the review’s criteria (all checks pass including small-change check,
and not touching on sensitive topics such as payments and security). Importantly, this skill has only two options: approve or ignore. It never comments on the PR to avoid
the proliferation of “ meat proxy review”
which has become a bottleneck-pretending-to-be-a-solution on some teams review-pr-cluster which reviews batches of pull requests to identify common themes that came up, and suggest opportunities
for discussion and adding verifications

review-small-change which takes a list of repositories and reviews all open, non-draft, small-changes,
including providing approval if they meet the review’s criteria (all checks pass including small-change check,
and not touching on sensitive topics such as payments and security). Importantly, this skill has only two options: approve or ignore. It never comments on the PR to avoid
the proliferation of “ meat proxy review”
which has become a bottleneck-pretending-to-be-a-solution on some teams

review-pr-cluster which reviews batches of pull requests to identify common themes that came up, and suggest opportunities
for discussion and adding verifications

We set the social expectation that any error caused by a small-change is a failure in our system,
and has to be solved at the system level: improvements to ai-code-review , to our verification mechanisms,
to our CICD, to our harness, etc.

Team is overwhelmed with reviews

Team decides to review pull requests with their local harness

Pull requests get a large number of comments, some of which make sense, and some of which don’t.
It’s unclear which is which without study, and you don’t know which comments reflect the reviewer’s
point of view. So you end up having to do substantial work to disprove comments that the reviewer may
not even agree with

Those teams then start using harnesses to respond to the harness-generated comments,
making the entire review process an illusion that doesn’t facilitate learning,
and most importantly could be done without the involvement of the other team members

</details>