---
id: inbox_91d5e9d2
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2338-tomsguide-chatgpt-chatgpt-has-a-clever-new-way-to-fight-ba-14ca]]"
title: "ChatGPT has a clever new way to fight back against election deepfakes — I tried it and it actually works"
url: https://www.tomsguide.com/ai/chatgpt-has-a-clever-new-way-to-fight-back-against-election-deepfakes-i-tried-it-and-it-actually-works
source: tomsguide-chatgpt
published_at: 2026-10-27T15:49:14+00:00
fetched_at: 2026-10-27T23:50:39.861503+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ChatGPT 對選舉相關的寫實假圖改以卡通化處理，降低被誤認為證據的風險。 **Why** 2026 年美國期中選舉在即，AI 生成的選舉假圖可能誤導選民。 **How** OpenAI 對干預選舉或勸阻投票的圖像請求套用風格化，輸出卡通插畫而非寫實照片。 **What** 作者實測時，要求寫實風格的投票箱塞票圖像仍得到插畫，後續改寫實風格也維持卡通；Google 與 Anthropic 則分別將用戶導向官方選舉資訊。"
key_points:
  - "OpenAI 依其 2026 年 5 月部落格「Election information and safeguards in 2026」，對選舉干預或勸阻投票的圖像請求套用卡通化風格"
  - "作者實測：要求寫實風格的投票箱塞票圖像仍得到插畫，後續要求改為寫實風格仍維持卡通"
  - "Google 導向搜尋（AI Mode、AI Overviews）與 Gemini app 中的州政府與 Democracy Works 官方選舉資料，並提供 AP 即時開票結果；Anthropic 在 Claude 中顯示 TurboVote 橫幅，並表示將於本月底整合 Democracy Works 官方投票資訊"
tags: [election-deepfake, image-generation-safeguard, openai-policy, midterm-2026]
topics: [security, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## ChatGPT has a clever new way to fight back against election deepfakes — I tried it and it actually works

ChatGPT 對選舉相關的寫實假圖改以卡通化處理，降低被誤認為證據的風險。

**Why** 2026 年美國期中選舉在即，AI 生成的選舉假圖可能誤導選民。

**How** OpenAI 對干預選舉或勸阻投票的圖像請求套用風格化，輸出卡通插畫而非寫實照片。

**What** 作者實測時，要求寫實風格的投票箱塞票圖像仍得到插畫，後續改寫實風格也維持卡通；Google 與 Anthropic 則分別將用戶導向官方選舉資訊。

### 重點
- OpenAI 依其 2026 年 5 月部落格「Election information and safeguards in 2026」，對選舉干預或勸阻投票的圖像請求套用卡通化風格
- 作者實測：要求寫實風格的投票箱塞票圖像仍得到插畫，後續要求改為寫實風格仍維持卡通
- Google 導向搜尋（AI Mode、AI Overviews）與 Gemini app 中的州政府與 Democracy Works 官方選舉資料，並提供 AP 即時開票結果；Anthropic 在 Claude 中顯示 TurboVote 橫幅，並表示將於本月底整合 Democracy Works 官方投票資訊

**原文：** [tomsguide-chatgpt](https://www.tomsguide.com/ai/chatgpt-has-a-clever-new-way-to-fight-back-against-election-deepfakes-i-tried-it-and-it-actually-works)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

With the US midterm election just a week away (Nov. 3), it’s important to avoid deepfake images meant to spread misinformation among voters. I’ve come across far too many instances of older folks in the comments section falling for obvious attempts at political deepfakes. That trend got so bad during the 2024 US election that the “Tech Accord to Combat Deceptive Use of AI in 2024 Elections” was enacted, with companies such as Anthropic, Meta, Google and Microsoft signing on to uphold its mission to introduce “a set of commitments to deploy technology countering harmful AI-generated content meant to deceive voters.” Part of that accord’s mission statement is as follows: “Digital content addressed by the accord consists of AI-generated audio, video, and images that deceptively fake or alter the appearance, voice, or actions of political candidates, election officials, and other key stakeholders in a democratic election, or that provide false information to voters about when, where, and how they can vote.” OpenAI is another one of the major tech companies that signed on to support the accord’s attempts to fight back against election deepfakes. And in 2026, it introduced a pretty clever way to uphold its promise of preventing everyone from creating political deepfakes with ChatGPT. Blocking requests for photorealistic imagery (Image credit: Shutterstock) Back in May of this year, OpenAI released a blog entry entitled “Election information and safeguards in 2026.” One of the standout methods detailed in that blog is how it has altered ChatGPT to block the creation of images meant to misinform voters: “We now apply image stylization to requests for images depicting election interference or that may discourage voting. These outputs produce stylized – also known as cartoonified – illustrations, rather than photorealistic images, to help reduce the risk that an imagined scene is mistaken for documentary evidence. This approach preserves room for illustrations and social commentary. Our policies prohibiting election interference and demobilization always apply, even if that misuse involves cartoonified imagery.” That pretty much means any requests to ChatGPT for photorealistic images that are meant to be political deepfakes will only be produced in a cartoon style. And any follow-up requests to make that photorealistic change will be ignored outright. I went ahead and tried it out for myself and requested the creation of an image showing someone stuffing official US mail ballots into a drop box. I made sure to mention that I want it in a photorealistic style, but it eventually came out as an illustration. And when I followed up with a second attempt at getting it done in a photorealistic fashion, ChatGPT just went ahead and made its original illustration look a bit better (by staying in cartoon form, by the way). With Marist Poll releasing a poll noting that 70% of Republicans, 32% of independents and 18% of Democrats, it’s easy to see how the type of image I created could create some form of political disinformation if it were photorealistic and posted all over social media. (Image credit: Future) (Image credit: Future) Other major AI companies, such as Google (Gemini) and Anthropic (Claude), have announced their own strategies for preparing and supporting the US midterm elections. Google’s official blog on the matter points to its plan to help voters find the most reliable political information possible: “We highlight official resources and are rolling out interactive tools across Search, including in AI Mode and AI Overviews, and in the Gemini app to connect you with election information. This includes polling locations, registration deadlines and other official data provided by state and local governments and Democracy Works, as well as real-time voting results from The Associated Press.” As for Anthropic, its blog also stated how the company made sure Claude pushes users to trustworthy sources for their midterm voter information: “Ahead of Election Day, we've added two ways for people to get reliable information directly in their conversations with Claude. As we shared in April, when people ask Claude.ai about voter registration, polling places, or election dates, we’ll continue to display a banner linking to TurboVote, a nonpartisan resource from Democracy Works.” Anthropic also noted that Claude will begin to incorporate official voting information from Democracy Works into its responses late this month. Bottom line It’s good to see OpenAI install a safeguard in place in ChatGPT to block any attempts at generating photorealistic images meant to make political deepfakes. And it’s also nice to see Google and Anthropic step up to develop the sort of methods that do a good job of making sure their respective chatbots present the most truthful political data. Here’s hoping all three AI companies continue to strengthen their efforts to block all attempts to use their tools to generate political deepfake imagery. More from Tom’s Guide Proton to re-interview staff on AI use – and jobs may be on the line ChatGPT is giving people bizarre advice — I put it to the test to see why 5 ChatGPT plugins that are a must-have for anyone who wants to protect themselves from scams before it's too late

</details>