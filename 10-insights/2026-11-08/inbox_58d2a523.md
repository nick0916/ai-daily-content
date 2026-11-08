---
id: inbox_58d2a523
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2347-substack-register-spill-joy-curiosity-105-7c80]]"
title: "Joy & Curiosity #105"
url: https://registerspill.thorstenball.com/p/joy-and-curiosity-105
source: substack-register-spill
published_at: 2026-11-08T08:24:03+00:00
fetched_at: 2026-11-08T23:52:41.953188+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者說每個人對 AI 寫程式的認知落差很大，並分享 Amp 今年改變工作方式的三個做法。 **Why** 有人只用過少量 token 就認定代理寫不好程式，有人已投入數十億 token 認為代理勝過人類，大家卻用同一套說法談軟體開發。 **How** Amp 全面遠端開發（orbs）、要求代理提出「irrefutable proof」，並讓代理掌控完整 SDLC，讓它看到人看到的、做人能做的事（寫資料庫除外）。 **What** Thorsten Ball 的 Joy & Curiosity #105。作者稱這三項各自讓他重新思考一切，其中要求代理提供無可辯駁的證明是他心中「10x 等級」的改變；Amp 的代理可上線、監控發布、讀 log、開 feature flag、寄信、發 credit。其餘為閱讀與連結推薦。"
key_points:
  - "今年改變 Amp 的三個做法：全面遠端開發（orbs）、要求代理提供 irrefutable proof、讓代理控制完整 SDLC"
  - "Amp 代理可上線、監控發布、讀 log、開 feature flag、寄信、發 credit、調查資料庫問題，唯獨不能寫資料庫"
  - "其他公司的瓶頸多在流程：PR 要等核可、團隊對 AI 持懷疑，或等待 PM 指示"
tags: [coding-agents, amp, sdlc, ai-adoption, newsletter]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Joy & Curiosity #105

作者說每個人對 AI 寫程式的認知落差很大，並分享 Amp 今年改變工作方式的三個做法。

**Why** 有人只用過少量 token 就認定代理寫不好程式，有人已投入數十億 token 認為代理勝過人類，大家卻用同一套說法談軟體開發。

**How** Amp 全面遠端開發（orbs）、要求代理提出「irrefutable proof」，並讓代理掌控完整 SDLC，讓它看到人看到的、做人能做的事（寫資料庫除外）。

**What** Thorsten Ball 的 Joy & Curiosity #105。作者稱這三項各自讓他重新思考一切，其中要求代理提供無可辯駁的證明是他心中「10x 等級」的改變；Amp 的代理可上線、監控發布、讀 log、開 feature flag、寄信、發 credit。其餘為閱讀與連結推薦。

### 重點
- 今年改變 Amp 的三個做法：全面遠端開發（orbs）、要求代理提供 irrefutable proof、讓代理控制完整 SDLC
- Amp 代理可上線、監控發布、讀 log、開 feature flag、寄信、發 credit、調查資料庫問題，唯獨不能寫資料庫
- 其他公司的瓶頸多在流程：PR 要等核可、團隊對 AI 持懷疑，或等待 PM 指示

**原文：** [substack-register-spill](https://registerspill.thorstenball.com/p/joy-and-curiosity-105)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

One of the strangest things nowadays is how everyone lives on a different timeline. Some people haven’t spent more than a hundred thousand tokens with the latest frontier models and conclude that agents can’t write code. Others have spent billions of tokens with them, in just the last week, and say that agents are now better at writing software than humans. In a few months, the first group will catch up. And that’s just the most obvious example, using the latest models to write code. There are many more things like that. Once you try them, your view of software development will be completely changed. Except not a lot of people have tried them and we all talk about software development as if it’s the same thing for all of us. “The future is already here – it’s just not evenly distributed.” I keep thinking of that quote. For me, the game has changed three times this year, with three different practices we’ve established at Amp: Going all-in on remote development and moving everything into orbs . You have to try it to believe it , but it is a change so fundamental that you will start to question everything: from the role of the operating system to what software even is. Asking agents for “ irrefutable proof ”. Made me question everything again: the value of tests, the value of looking at code, what it is we do when we “review” something, what specs are and what not. If there’s a 10x game changer, it’s this one. Letting the agent control the full SDLC. At Amp, the agent can ship things to production, monitor their rollout, read logs, turn on feature flags, send emails, grant credits, investigate database issues, check graphs, ... Everything that I can do, except writing to the database. The models have become too good to keep them boxed in as smart typewriters. Let them see what you can see, let them do what you can do (besides writing code) and you’ll glimpse the future. (Jump to the end of this talk here to see what I mean.) I have so many “wow, I can’t believe my eyes!” moments that I constantly want to post this exact messasge in our Slack, but then I remember that I only posted it yesterday and I can’t spam everyone, they’ll think it’s psychosis. And then I talk to someone at another company and they tell me that if they find a papercut they can’t just fix it, because they’ll have to get the PR approved. And then they have to wait for the review and justify why they changed things. So they have ten pull requests open and constantly rebase them, ready to merge, impatient that it’ll never happen. Or they tell me their team is skeptical of AI and doesn’t want anything that makes life easier for agents in the codebase. Or they now do the work that previously would’ve taken them two weeks in a single day now but now they need to wait for the PM to tell them what to do. So they fiddle their thumbs and build elaborate agent tooling and workflows and slash commands but gettings things done they are not. Or they work in a company where they’re only allowed to spend $50 in GLM 5.3 credits per week and they don’t think that agents really change anything anyway. What a wild time it is! But not everyone has caught up to it yet. They will though. On Craft, Process, and Networks : “The first is don’t let anyone or anything, or anything acting like anyone, or anyone promoting anything, convince you that craft is outdated or will ever be outdated; you will only improve, only make the sounds you imagine in your mind’s ear and feel in yourself, by working steadily to achieve them. Also recognize that expected paths lead to unlikely ends the more patiently and curiously, guided by instinct and experience, you walk those paths. There is always an excuse to not put in the work.” Andy Matuschak: Why books don’t work . Came for the title about books, left thinking about lectures and talks and how “effective” they are at achieving their goals. Peter Thiel on the new Walter Isaacson podcast. Always entertaining hearing him talk about the Antichrist. Second time I’ve done that while driving alone, hoping really hard that I won’t have to stop at a red light where someone could hear what I’m listening to. The internet turns good taste into bad taste : “Algorithmic feeds on digital platforms attempt to serve us content that we like; they filter in search of what an equation predicts will be interesting to us. Yet by guessing in advance what we want, they tend to homogenize what we consume. An algorithm will group you in with millions of other users, slotting your tastes into an easy category, then overdeliver on that category.” *sshole . Okay, this was scary, but then not that scary, but still: good job picking the name. Every Novel Is Boring—Until It Isn’t . I’ve never heard the term “volta”, so this was good, but also: yes, that’s my main concern with stopping books early, even if I don’t enjoy them — maybe I just need to keep going for 50 more pages? Read the new latest Patrick Radden Keefe book, London Falling . Didn’t enjoy it as much as his other books, but still very good. Kirill Nikolaev at Namespace wrote about how they make their macOS cloud work: Mac at any scale . Very, very interesting. I wonder why Apple doesn’t do more with Hypervisor? keep going . We went full circle: memes (as we know them now) started as riffs on motivational posters and now they’ve become motivational posters. The Running Novelist . This is the 2008 piece by Haruki Murakami that lead to (or is an excerpt of?) his What I Talk About When I Talk About Running book, which I read many, many, many years ago. While reading this, I couldn’t help but think that the prose feels so... translated? Fascinating, but strange. Or maybe the But should be an And? Written as if he (or his translator) doesn’t know certain idioms in English. So, fascinated by that, I got his book, Novelist as a Vocation , and, well, there you go: “Needless to say, my ability in English composition didn’t amount to much. My vocabulary was severely limited, as was my command of English syntax. I could only write in short, simple sentences. Which meant that, however complex and numerous the thoughts running around in my head, I couldn’t even attempt to set them down as they came to me. The language had to be simple, my ideas expressed in an easy-to-understand way, the descriptions stripped of all extraneous fat, the form made compact, and everything arranged to fit a container of limited size. The result was a rough, uncultivated kind of prose. As I struggled to express myself in that fashion, however, a distinctive rhythm began to take shape.” Aaron Francis: Caring in the age of AI . “Your job is to eat the pain.” What a quote! Great talk. If you had game-changing moments this year, you should subscribe:

</details>