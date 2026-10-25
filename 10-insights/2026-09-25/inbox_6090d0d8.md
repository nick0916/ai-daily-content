---
id: inbox_6090d0d8
date: 2026-09-25
source_ref: "[[00-inbox/2026-09-25/0102-lobsters-ai-goodbye-google-76e0]]"
title: "Goodbye Google"
url: https://robert.ocallahan.org/2026/09/goodbye-google.html
source: lobsters-ai
published_at: 2026-09-25T00:51:12-05:00
fetched_at: 2026-10-25T01:26:32.363636+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位 Google 工程師因工作會加速 AI 晶片而離職，轉而維護 rr 與 Pernosco 並研究 AI 除錯。 **Why** 他認為 AI 進展過快、風險真實但不確定，且自己參與的晶片設計工具會讓 AI 更便宜、更快。 **What** 文中宣布於 2026-09-24 離開 Google，未來將繼續維護 Pernosco 與 rr，並計畫研究 AI agents 如何除錯及相關工具；他表示希望未來工作「明確站在人類這邊」。"
key_points:
  - "2026-09-24 離開 Google，原工作為晶片設計工具，他認為該工具會加速 AI 晶片"
  - "將繼續維護 Pernosco 與 rr，並計畫研究 AI agents 如何除錯及可用的除錯工具"
  - "認為 AI 風險真實但不確定，且 AI 能力發展速度已超過人類理解與調適的速度"
tags: [ai-safety, career, debugging-tools]
topics: [product_and_org.leadership]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Goodbye Google

一位 Google 工程師因工作會加速 AI 晶片而離職，轉而維護 rr 與 Pernosco 並研究 AI 除錯。 **Why** 他認為 AI 進展過快、風險真實但不確定，且自己參與的晶片設計工具會讓 AI 更便宜、更快。 **What** 文中宣布於 2026-09-24 離開 Google，未來將繼續維護 Pernosco 與 rr，並計畫研究 AI agents 如何除錯及相關工具；他表示希望未來工作「明確站在人類這邊」。

### 重點
- 2026-09-24 離開 Google，原工作為晶片設計工具，他認為該工具會加速 AI 晶片
- 將繼續維護 Pernosco 與 rr，並計畫研究 AI agents 如何除錯及可用的除錯工具
- 認為 AI 風險真實但不確定，且 AI 能力發展速度已超過人類理解與調適的速度

**原文：** [lobsters-ai](https://robert.ocallahan.org/2026/09/goodbye-google.html)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Eyes Above The Waves

Archive

Goodbye Google

Robert O'Callahan. Christian. Kiwi. Software guy. All content human-authored unless otherwise noted.

robert@ocallahan.org ...
 Follow on X ,
 Follow on Bluesky 

Thursday 24 September 2026

Today I’m sending the following email:

I’m resigning from Google today.

This has not been an easy decision. I love my colleagues and my work environment, and being paid handsomely to solve fun puzzles has been amazing. But my team’s goal is ultimately to make AI much cheaper and lower-latency, and I don’t think that’s good for people right now: I firmly believe AI progress is currently far too rapid (and I have doubts about the destination too). It’s practically impossible for me to move to a different Google project that wouldn’t accelerate AI (partly due to my ties to New Zealand, where Google prefers not to do engineering), so my hands are tied.

There are millions of people contributing to AI acceleration and taking my foot off the accelerator will have a very small impact ... but not no impact; some of my skills are rare. I explored trying to positively influence events from within GDM, but that effect does not seem to be strong, and I can have influence outside Google too. It’s tempting to just turn a blind eye to the impact of my work, but that would not be a Jesus-following thing to do. I have written more about these tradeoffs on my blog.

I don’t know exactly what I will do next. I will continue maintaining Pernosco and rr , and relatedly I plan to investigate how AIs debug code today and whether and how debugging tools could help. I have other project ideas I want to work on, some potentially lucrative, some not. Maybe I’ll find an existing project that’s compelling. I definitely want my future work to be unambiguously pro-human.

Discussion thread on HN

First, for those who don’t know me: I’ve been in the tech industry a long time and I have a lot of Silicon Valley connections, but I live in New Zealand so I live outside the industry bubble and also outside the American bubble. I’m a Christian, and actually an elder and occasional lay preacher in the English-speaking congregation of Auckland Chinese Presbyterian Church in Auckland’s inner city. That is, I am not a “tech bro”, nor do I fit into the self-described “rationalist community” ... but I do think many of their arguments deserve to be taken seriously.

I have a lot of thoughts about AI, but I’m not going to elucidate them all in this post. In summary, I think the existential risks many people are warning about deserve to be taken seriously; a lot of the phenomena predicted by the “doomers” have come to pass (e.g., reward hacking, misalignment, deceptive models, model eval awareness, psychotic swarms). However, I am not convinced the chance of ASI doom is 100%. Rather, I think the risk is real but uncertain — but that itself is very alarming! We are morally obliged to make a massive effort to minimise such risk, and most likely the risk is high enough that aiming for ASI in the near future is inherently irresponsible. I’m also very concerned about other AI-related issues: cognitive surrender , AI-induced psychosis and loneliness, power concentration, economic disruption, cybersecurity, lack of accountability, and so on. I think the potential benefits of AI are quite unclear and currently, if I had to bet, I’d bet the negatives will outweigh the benefits ... but I’m uncertain about that too.

Here are some things I’m confident about. I’m confident that the people in AI labs who are issuing warnings about AI are generally sincere. I’ve talked to many people in Google Deepmind about these issues and almost all of them have sincere and serious concerns, whether or not they voice them in public. I have seen no hard evidence that people are hyping AI risk as a means to boost company stock prices or regulate away their competitors. (I think national and international regulation is desperately needed!) I’ve seen a lot of arguments of the form “you can’t trust those people”, and maybe that’s true, but such distrust is not a good reason to disregard their warnings, as Russell Moore eloquently explained recently.

I’m confident that AI capability will continue to keep increasing steadily as long as we keep working on it. I wish that AI would hit some kind of plateau, or that we would identify important human cognitive abilities that AI will never replicate without a paradigm shift, but I don’t expect those wishes to come true. Model progress on benchmarks seems as fast or faster than ever, and with it, qualitatively new capabilities keep emerging. Even if model progress stopped today, we could spend years effectively unlocking new capabilities via new prompts and harnesses. Many prominent AI detractors (looking at you, Zitron and Doctorow) seem to think that AI is some kind of scam that won’t really work. I think it will.

I’m very confident that even if there is a path to a better future through AI, the current rate of change is far too high . AI is developing faster than humans can individually and collectively understand it and adapt to it. People trying to plan their futures, e.g. trying to plan for a world several years in the future as they enter university, can no longer do so the way previous generations could. I don’t think we’ve seen anything like this before, certainly not in the previous technological shifts I have lived through (PCs, the Internet, smartphones). Even during the Industrial Revolution, not only was change much slower but there were large swathes of human activity that were not and could not be directly impacted by the new machines. That is not very true anymore.

Why leave now and not earlier? It’s nothing to do with the recent spate of viral resignations or “AI slowdown” warnings; that’s a coincidence. I’ve had this date in mind for a while, because I have a long-planned ten-day backpacking trip with my friends starting Monday ( Abel Tasman and Wangapeka tracks) and I wanted to go before that.

I did not work directly on AI capability, but on improved tools for hardware chip design. I really enjoyed the work, and for a while I told myself it was relatively harmless, but over time God forced me to confront the reality that the main impact of these tools will be to accelerate the design of a new breed of AI chips, which if successful will make AI much cheaper and faster — making AI more pervasive, and also more capable since we’ve learned to boost capabilities by burning more inference tokens. My duty to be a good employee meant I had to have an honest conversation with my skip manager and tell them I was at best reluctant to see their project succeed! Even after that I wanted to be really confident in my decision, because the great deal I had working for Google in New Zealand will probably never be available again. (Staying at Google and switching to a different engineering team not accelerating AI was impractical, because Google doesn’t have other engineering teams in New Zealand.) My aforementioned duty to my employer, and my respect for the people, was also a factor for not leaving too abruptly and trying to hand over my work in a reasonable state.

What next? The most important thing I’m confident about is that the Jesus of the Bible is real and therefore God has a plan that’s good for us. I don’t know what that plan is (and wish I did) but it lets me sleep at night in spite of the AI chaos. I expect his plan involves me continuing to make the best use of my talents. Even if the plan is for Jesus to return to rescue us from our folly, we’d better be busy when he returns! So, as long as the talent God gave me is valuable, I want to keep working. As I mentioned above, I plan to continue maintaining Pernosco and rr . Under the Pernosco umbrella, I plan to study how AI agents debug code and whether debugging tools that can make them more effective at that. I want to use AI agents to bring some of my hobby project ideas to life. I’m keen to reap the benefits of AI, but cautiously, in ways that benefit humans and keep my own mind sharp. As much as I can, I will continue practicing and advocating for that here in New Zealand.

Wangapeka Track

Abel Tasman 2026

Goodbye Google

A Meta-Meditation On The Lord's Prayer (And DNA)

A Meditation On The Lord's Prayer

Queenstown Walks

Thoughts on 'Pacing The Frontier'

Karangahake Gorge To Te Aroha

Anthropic And AI Principles

Why Trump Is An Antichrist

Taiwan

Pouakai Circuit 2025

AI And Jesus In Late 2025: A Road Trip Report

Some Thoughts About Money From A Christian In Big Tech

Crosbies Hut 2025

Not Joking About AI

Building A PC

Rakiura Northwest Circuit

Tongariro Northern Circuit 2025

Pararaha Valley 2025

Mt Arthur/Tablelands/Cobb Valley

Queen Charlotte Track 2024

Auckland Half Marathon 2024

Advanced Debugging Technology In Practice

Waihohonu Hut 2024

So You Want To Build A Browser Engine

Real-Time Settlers Of Catan

Auckland Waterfront Half Marathon 2024

Whanganui River Journey 2024

Rees-Dart Track 2023

Caples/Routeburn Track 2023

Abel Tasman Kayaking

Mount Pirongia 2023

Blog Migrated

Why I Signed The "Pause" Letter

Auckland Waterfront Half Marathon 2023

Travers-Sabine Circuit 2022

Paparoa Track

Aotea Track 2022

Success, Privilege And God

Tūrangi Road Trip

Round The Mountain Track: Ups and Downs and a Twist Ending

New Zealand's COVID Strategy Worked (But It Could Have Been Better)

Motutapu Island Camping Trip

Motatapu Track

Hump Ridge Track

The End Of The Runway

Mt Pirongia 2021

Do We Really Need A Link Step?

Some Observations On The NZ CovidPass System

How WHO Failed

Emulating AMD Approximate Arithmetic Instructions On Intel

rr Trace Portability: Diverging Behavior of RSQRTSS in AMD vs Intel

Spectre Mitigations Murder *Userspace* Performance In The Presence Of Frequent Syscalls

Tama Lakes Winter Tramp 2021

Forward Compatibility Of rr Recordings

Lake Waikaremoana 2021

Print Debugging Should Go Away

Demoing The Pernosco Omniscient Debugger: Debugging Crashes In Node.js And GDB

Visualizing Control Flow In Pernosco

On-Premises Pernosco Now Available; Reflecting On Application Confinement

What Would Jesus Do ... About Vaccination?

Mercer Bay

Dehydration

Tongariro Northern Circuit 2021

Rees-Dart Track

Kepler Track 2020

Exploiting Precognition In Binary Instrumentation Of rr Replays

rr remix: Efficient Replay-Only Binary Instrumentation

DOM Recording For Web Application Demos

Debugging With Screenshots In Pernosco

rr Repository Moved To Independent Organisation

Pernosco Now Available For Individual Developers

Auckland Half Marathon 2020

Pouakai Circuit 2020

The Parable Of The Two Bus Drivers

New Zealand's Long Term COVID19 Strategy

Surprising Words In Luke 1:16-17

What's So Amazing About Mark 10:32

Scaling Debuginfo For Zero-Cost Abstractions

What Is The Minimal Set Of Optimizations Needed For Zero-Cost Abstraction?

Cape Brett 2020

My Google Maps Disaster

Why Forking HTML Into A Static Language Doesn't Make Sense

Omniscient JS Debugging In Pernosco

Have Some Humility, Mike Hosking

What If C++ Abandoned Backward Compatibility?

Debugging Gdb Using rr: Ptrace Emulation

Static Customization Of Function Signatures In Rust

Updating Pernosco To Rust Futures 0.3

A Risk Of Transactional Politics For Christians

Nelson Lakes Tramping: Lessons And Observations

Nelson Lakes Tramping: Travers-Sabine Circuit

Nelson Lakes Tramping: Angelus Basin

Your Debugger Sucks

Supercharging Gdb With Pernosco

The Power Of Collaborative Debugging

Omniscient Printf Debugging In Pernosco

The BBC's "War Of The Worlds"

Explaining Dataflow In Pernosco

Improving Debugging Workflow With Pernosco

Auckland Half Marathon 2019

Pernosco Demo Video

Food In Auckland 2019

Pouakai Circuit

Is Richard Dawkins A Moral Realist?

Dissatisfied With Docker

Cape Brett 2019

Auckland Rust Meetup: "Building An Omniscient Debugger In Rust"

Stack Write Traffic In Firefox B

[... truncated for safety ...]

</details>