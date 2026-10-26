---
id: inbox_de97d5b2
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0102-lobsters-vibecoding-the-brain-sandwich-a2fb]]"
title: "The Brain Sandwich"
url: https://terriblesoftware.org/2026/10/02/the-brain-sandwich/
source: lobsters-vibecoding
published_at: 2026-10-17T22:03:36-05:00
fetched_at: 2026-10-25T01:27:20.257534+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "先自己讀懂問題、再讓 AI 執行、最後自己審查，避免把大腦完全移出流程。 **Why** 作者提到有工程師把整個工作委派給 AI（即所謂 Meat Proxy），會讓工程技能退化。 **How** 「Brain Sandwich」三段式：先由人閱讀理解並掌握大方向，再完全委派 AI 實作，最後回到人工讀 diff、檢查複雜度並改寫 PR 描述。 **What** 此框架由作者的同事 Emily 提出；文中給出送審判準：若說不清楚改了什麼、為什麼改，就還沒準備好請他人審查。"
key_points:
  - "動手前先閱讀理解，因為 AI 可能先把你導向錯誤方向，甚至讓你解決不需要解決的問題"
  - "AI 執行階段可完全委派，之後人必須回來判斷方案是否正確、是否過度複雜或解錯問題"
  - "送審判準：若說不清楚改了什麼、為什麼改，就還不該送給他人審查"
tags: [ai-workflow, code-review, skill-atrophy, meat-proxy, human-in-the-loop]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Brain Sandwich

先自己讀懂問題、再讓 AI 執行、最後自己審查，避免把大腦完全移出流程。

**Why** 作者提到有工程師把整個工作委派給 AI（即所謂 Meat Proxy），會讓工程技能退化。

**How** 「Brain Sandwich」三段式：先由人閱讀理解並掌握大方向，再完全委派 AI 實作，最後回到人工讀 diff、檢查複雜度並改寫 PR 描述。

**What** 此框架由作者的同事 Emily 提出；文中給出送審判準：若說不清楚改了什麼、為什麼改，就還沒準備好請他人審查。

### 重點
- 動手前先閱讀理解，因為 AI 可能先把你導向錯誤方向，甚至讓你解決不需要解決的問題
- AI 執行階段可完全委派，之後人必須回來判斷方案是否正確、是否過度複雜或解錯問題
- 送審判準：若說不清楚改了什麼、為什麼改，就還不該送給他人審查

**原文：** [lobsters-vibecoding](https://terriblesoftware.org/2026/10/02/the-brain-sandwich/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The Brain Sandwich

Share this:

Like this:

Discover more from Terrible Software

I was on a 1:1 with Emily, one of our strongest engineers, and we were mostly venting about some of the negatives about AI these days: the crazy amount of code reviews, how the job is changing, and the last one (which is the most relevant for this post), how engineers are sometimes completely removing their brains from the equation and just delegating their entire work to AI.

(Btw, I heard that the cool kids are calling this a Meat Proxy .)

But anyway, the reason I decided to post about this is that Emily has a very simple framework that she uses for working with AI, which she calls the “Brain Sandwich”, that solves this. It’s both about taking full advantage of AI without letting your engineering skills atrophy.

The idea is very simple, and can be summarized by: whenever you work on something, you should use:

Explaining a bit more...

Before you tell the agent to start building anything, you go there and read and understand it first .

You don’t need a complete implementation plan, but you need a rough idea of where you’re going. Otherwise, AI can bias you in the wrong direction. Or even worse, it can nudge you into building something that wasn’t even a problem you needed to solve in the first place!

Now that you have all this context, that’s the time to bring AI. By all means, do it. Fully delegate this part with no shame! And when the agent brings you the solution, you will know if it’s right, or if it’s too much, or if it’s completely solving the wrong problem, etc.

Then, at the end, your brain comes back. Because before sending your stuff to other people for review, you need to make the work reviewable . Read the diff, check if the complexity is worth it in this case, improve the freaking PR description, etc. The rule of thumb is: if you can’t explain what’s changing and why, it’s not ready for someone else to take a look.

Subscribe to get the latest posts sent to your email.

Your brain, and then

AI, and then

Your brain

 Share on Facebook (Opens in new window) Facebook 

 Share on LinkedIn (Opens in new window) LinkedIn 

 Share on Threads (Opens in new window) Threads 

 Share on Bluesky (Opens in new window) Bluesky 

 Share on Mastodon (Opens in new window) Mastodon 

 Share on X (Opens in new window) X

</details>