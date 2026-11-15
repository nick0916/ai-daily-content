---
id: inbox_e0fc2726
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-interconnects-open-source-ai-without-jensen-e4c8]]"
title: "Open-source AI without Jensen"
url: https://www.interconnects.ai/p/open-source-ai-without-jensen
source: interconnects
published_at: 2026-11-14T12:23:15+00:00
fetched_at: 2026-11-15T01:29:18.583109+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Nvidia CEO 黃仁勳辭職，讓美國開放模型生態失去最重要的資金與政治靠山。 **Why** 作者認為開放模型經濟仍在萌芽期，需要時間確立用例與營收，而黃仁勳不只出資，還會在監管等風險出現時出面擋下。 **How** 作者論點：Nvidia 支持開放模型符合其利益（避免權力集中在自行開發晶片的少數客戶），但 Nvidia 現在首要是穩住公司；長期解法是在美國培養真正的前沿開放模型玩家。 **What** 作者引述 Dylan Patel 的看法：問題不在錢而在人才，頂尖人才多在 Anthropic、OpenAI、DeepMind 與 Meta TBD，其餘分散於上百家新創；Thinking Machines 的 Inkling 2 Small 是近期最佳西方開放權重模型，但仍遠落後 Kimi K3.1 Pro。作者最擔心州層級的草率監管，並呼籲開放模型支持者建立新的聯盟與平台。"
key_points:
  - "黃仁勳辭職被視為美國開放模型生態的重大挫折；作者預期他原本大量投入的資金將會枯竭"
  - "Dylan Patel：差距在人才而非資金，Moonshot 技術不輸美國實驗室，缺的是算力與部署規模"
  - "作者最擔心的是州層級的草率監管，並認為「一個強大中國開放權重模型」引發危機只是時間問題；解方是在美國培養真正前沿的開放模型玩家"
tags: [open-weights, nvidia, jensen-huang, open-model-economy, ai-policy]
topics: [foundation_models.open_weights, product_and_org.leadership]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Open-source AI without Jensen

Nvidia CEO 黃仁勳辭職，讓美國開放模型生態失去最重要的資金與政治靠山。

**Why** 作者認為開放模型經濟仍在萌芽期，需要時間確立用例與營收，而黃仁勳不只出資，還會在監管等風險出現時出面擋下。

**How** 作者論點：Nvidia 支持開放模型符合其利益（避免權力集中在自行開發晶片的少數客戶），但 Nvidia 現在首要是穩住公司；長期解法是在美國培養真正的前沿開放模型玩家。

**What** 作者引述 Dylan Patel 的看法：問題不在錢而在人才，頂尖人才多在 Anthropic、OpenAI、DeepMind 與 Meta TBD，其餘分散於上百家新創；Thinking Machines 的 Inkling 2 Small 是近期最佳西方開放權重模型，但仍遠落後 Kimi K3.1 Pro。作者最擔心州層級的草率監管，並呼籲開放模型支持者建立新的聯盟與平台。

### 重點
- 黃仁勳辭職被視為美國開放模型生態的重大挫折；作者預期他原本大量投入的資金將會枯竭
- Dylan Patel：差距在人才而非資金，Moonshot 技術不輸美國實驗室，缺的是算力與部署規模
- 作者最擔心的是州層級的草率監管，並認為「一個強大中國開放權重模型」引發危機只是時間問題；解方是在美國培養真正前沿的開放模型玩家

**原文：** [interconnects](https://www.interconnects.ai/p/open-source-ai-without-jensen)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The resignation of Nvidia CEO Jensen Huang is a major setback for the US development of an open model ecosystem. Nvidia still has the financial interests in supporting open models, which are to avoid concentration in power among a few customers who would develop their own chips and reduce Nvidia’s profits, but supporting the open ecosystem is a tricky puzzle more than an engineering problem to grind out a solution on. Nvidia’s business operations are famously extremely dependent on Jensen as an operator, so it is a consensus opinion that there are challenges ahead (or even more high-profile departures through chip-smuggling investigations or plain-old sharks circling more poachable talent). Nvidia’s number one goal is to stabilize the ship, deliver to customers in the next 24 months, and prevent implosion. Open models have been one of Jensen’s more ambitious, founder-style bets. He has been flooding the zone with funding in a way that will very likely dry up. Interconnects AI is a reader-supported publication. To receive new posts and support my work, consider becoming a free or paid subscriber. In this period, the open model economy is in its nascency. These are crucial years for establishing use-cases, revenue flow, and motives to continue training the next generation models. I discussed the sensitivity of these early years in my recent talk at Fireworks Forge ( slides , recording ). The core of the argument is one upside for open models, a reason to be optimistic, and one downside. The positive case is that the open model economy has correctly latched onto “ownership of intelligence” and enterprise post-training as a crucial lane. What is to be determined is exactly how big the downstream market is. The downside is that the true long-term benefit of open models, as truly commoditized intelligence, is very far from realization with compute in such short supply. In the near term, where inference startups are also struggling to get enough chips (because Anthropic and OpenAI are buying so much capacity), there’s little margin competition on open-weight models. If open-source models are also served at giant inference margins, as we learned with DeepSeek’s DeepInfer release, they’re far from a commodity. In this paradigm, the closed labs with better economies of scale and integration from model to datacenter and chips will win. I expanded on this challenge in my recent piece on the open model economy . Together, a lot still needs to go right for open models to be a meaningful economic engine. Jensen’s support, and protection, gave the ecosystem time to figure this out. Jensen was more than a cheerleader. He would stop a lot of shit from going wrong once early winds were stirring. He was willing to use his power on open models. There’s a major swell in Democratic government funding towards candidates that want to regulate the AI industry, fostering “safety” . Many of these people feel a need to do something and have general opinions that open models are unsafe, while not being educated on the complexities of their benefits. My biggest near-term worry is sloppy regulation at the state level, followed by national regulation. We’ve been one, strong Chinese open-weight model away from a crisis since this summer. It still holds – especially as we enter a new, turbulent equilibrium of cybersecurity. We have not seen a major hack driven by a popular Chinese open-weight model, but it is a matter of when, not if. We need someone to encourage caution and an ecosystem perspective when the “open-weight hawks” come hunting. Knocking over the open-source AI domino today is easy — if done, unwinding the downstream concentration of power, reduction in safety research, and stifling of long-term innovation is far harder. On public data, it looks like balancing long-term innovation versus short term risks, but this is due to how horribly hard it is to measure the open model economy (e.g. the most valuable aspects of it run on private infrastructure). It’s a recurring challenge facing the ecosystem and my work. As a brief aside, the extent to which the media ecosystem is revolving around timing today, rather than exact availability of information, is incredible. All of these Jensen affairs were known, but getting them out at the right time, right after the midterm political swing, took down the king. The same goes for the Jacob Coxon brouhaha this summer. All of that safety culture around top labs was well known, but the right timing around datacenters and the Overton window made it a national issue. This could very well happen at some point for open model safety, as it tends to be harm, risk, or safety-related narratives that drive the modern media algorithms. I cannot imagine my work on open-science driving such a media cycle, because it will never happen. Share The only lasting solution to this is to incubate a truly frontier open model player in the US. For example, I agree completely with Dylan Patel, CEO of SemiAnalysis, on a core problem in the US open model ecosystem. From a recent ChinaTalk + SemiAnalysis emergency podcast : Jordan Schneider: I do want your guys’ take on just how bad this is, that Jensen’s now off the table for the future of American innovation. And we should talk about open models. I mean, he was the big champion, right? Dylan, you were talking earlier — I still don’t understand quite why someone didn’t just spend a few billion dollars and make something better than Kimi or DeepSeek and open source it. Dylan Patel: Not that easy. It’s not money, it’s talent, man. All of the most talented people primarily work at Anthropic, OpenAI, DeepMind, and Meta TBD, right? And then those who don’t are split across a hundred different startups. I mean, yes, Thinking Machines has a cracked team, but is Thinking Machines as good as Moonshot? No. Moonshot skill-wise is probably just as good as the US labs. They just have a big deficit in compute and deployment. So I think if we don’t have a scale advantage, then you don’t win. Yes, these smaller labs have spent a lot of money on models. But DeepMind, Grok, Meta have regularly fallen behind the frontier of Chinese labs, and they’re spending more. So it’s not just, oh, spend a few billion dollars and you can make a model that’s better. The best people for attracting talent are the ones at the front of movements. Jensen helped catalyze this, and on many metrics was still losing. Nemotron has had the right level of ambition and strong people, but it hasn’t delivered to the point of being called “mission accomplished.” The competition here in building leading-edge models is more fierce than most give credit to. Having an organization with billions of dollars, solid people, and good vibes may not get you there. You normally need something special. It could be the case that Thinking Machines has gotten to maturity in its commitment to open models, with its recent Inkling 2 Small being the best Western open-weight model in a while. Still, it’s far behind Kimi K3.1 Pro and expectations are high for Zhipu’s next GLM update. It’s a better sign that we’re at least having this debate, but the open ecosystem is riddled with questions and answers like this – maybe they can pull it off? On the other side of the equation, closed labs like Anthropic look like some of the greatest businesses ever assembled, which inspires confidence in the longevity of their approach. Who is Mira going to call when they need to close their next funding round? Supposedly the next round at a $40B valuation is a done deal, but that won’t be enough to keep pace with the closed frontier for long. The fundamental problem is that the open-weight ecosystem needs someone who will pick up the phone to abate a crisis. There are more challenges ahead. The most likely allies we could turn to are from the hyperscalers, the likes of Zuckerberg, Andy Jassy, or Satya. With such a coordinated campaign of pressure from the AI safety community that has open models as a negative target, I worry that being proactive is the only way to stay ahead. Jensen has carried that mantle for about two years, and times were messy before he stepped up clearly in 2025. We’re regressing in the operational capability of our movement, when the stakes and attacks are destined to rise. We open model believers are due some soul-searching and coalition building to construct a new platform. Shoes have been emptied that will never fully be refilled.

</details>