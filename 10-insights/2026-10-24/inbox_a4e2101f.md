---
id: inbox_a4e2101f
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-bluesky-ai-curated-dessa-the-conversation-model-trained-onl-b09f]]"
title: "Dessa - the Conversation Model trained only on speech"
url: https://block.xyz/dessa
source: bluesky-ai-curated
published_at: 2026-10-24T01:21:25.916000+00:00
fetched_at: 2026-10-25T01:10:55.835526+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Block 的小型研究實驗室釋出只用人類對話聲音訓練、不靠文字的雙向語音模型，能邊聽邊說。 **Why** 現行語音 AI 把聲音轉成文字，會丟掉情緒、語氣與時機等資訊，導致體驗僵硬，團隊也認為 AI 聽不出人聲中的情緒有安全疑慮。 **How** 從零開始只用人類對話的聲音訓練，沒有文字、沒有預訓練模型；是 audio in、audio out 的 full-duplex speech-to-speech 模型，能自行判斷何時插話與給回應（如「yeah」「got it」）。 **What** Dessa 宣稱語言學習所需的字數比 LLM 少數百倍，只用一組 NVIDIA GB200 NVL72 訓練，推論速度快於即時，可在 MacBook Pro M4 Max 或更高規格上本機執行。團隊由前 Toronto 深度學習新創 Dessa 成員組成，直接向 Block 共同創辦人 Jack Dorsey 報告，並開放小群 AI 安全研究者早期存取；官方示範包含它與第三方 GPT-Live-1 對話（雙方皆為 AI 語音，GPT-Live-1 開發者未審閱或背書）。"
key_points:
  - "純語音訓練：無文字、無預訓練模型，full-duplex 同時聽與說，可自行決定插話與 backchannel；官方稱為首個僅用人類語音訓練、能即時逼真對話的 AI"
  - "官方稱訓練只用一組 NVIDIA GB200 NVL72，推論快於即時，需 MacBook Pro M4 Max 或更高規格才能本機執行"
  - "提供小群 AI 安全研究者早期存取以找出未預期風險；研究問題包括語音模型學語言與事實的效率、學新語言的效率、in-context learning 能力"
tags: [speech-model, full-duplex, block, speech-to-speech, local-inference]
topics: [research.training, engineering.inference, product_and_org.product]
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Dessa - the Conversation Model trained only on speech

Block 的小型研究實驗室釋出只用人類對話聲音訓練、不靠文字的雙向語音模型，能邊聽邊說。

**Why** 現行語音 AI 把聲音轉成文字，會丟掉情緒、語氣與時機等資訊，導致體驗僵硬，團隊也認為 AI 聽不出人聲中的情緒有安全疑慮。

**How** 從零開始只用人類對話的聲音訓練，沒有文字、沒有預訓練模型；是 audio in、audio out 的 full-duplex speech-to-speech 模型，能自行判斷何時插話與給回應（如「yeah」「got it」）。

**What** Dessa 宣稱語言學習所需的字數比 LLM 少數百倍，只用一組 NVIDIA GB200 NVL72 訓練，推論速度快於即時，可在 MacBook Pro M4 Max 或更高規格上本機執行。團隊由前 Toronto 深度學習新創 Dessa 成員組成，直接向 Block 共同創辦人 Jack Dorsey 報告，並開放小群 AI 安全研究者早期存取；官方示範包含它與第三方 GPT-Live-1 對話（雙方皆為 AI 語音，GPT-Live-1 開發者未審閱或背書）。

### 重點
- 純語音訓練：無文字、無預訓練模型，full-duplex 同時聽與說，可自行決定插話與 backchannel；官方稱為首個僅用人類語音訓練、能即時逼真對話的 AI
- 官方稱訓練只用一組 NVIDIA GB200 NVL72，推論快於即時，需 MacBook Pro M4 Max 或更高規格才能本機執行
- 提供小群 AI 安全研究者早期存取以找出未預期風險；研究問題包括語音模型學語言與事實的效率、學新語言的效率、in-context learning 能力

**原文：** [bluesky-ai-curated](https://block.xyz/dessa)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

timkellogg.me 在 Bluesky 分享:Block released a fully bidirectional speech model that can run on your laptop 

block.xyz/dessa

You learned to talk by listening. So did

Let me listen...

What is this?!

This is crazy!

Wait but why?

Dessa who?

Calling all safety researchers!

Team Dessa

More samples

Talking about the release

Remembering a movie

An anniversary surprise

Expressive conversation

Life advice

Dessa in conversation with GPT-Live-1

Artist Dessa

Bathroom disaster

Hobbies talk

Lazy AI gaming

Marvel gaming

Noisy GPT live

Oh my god

Poor Elina

Refund

Ronaldo

Safety lab

Singing nonsense Spanish

Spontaneous AI

Wise Dessa

Zelda discussions

We believe voice is the most natural way to interact with intelligence, so we created Dessa, the most authentic full-duplex speech model ever built. Talking with it feels like talking with a person...full of emotion, nuance, pauses, and a natural cadence.

Interacting with current voice AI can just plain suck. It turns your voice into text and throws away an incredible amount of information text alone can’t carry. The most powerful AIs in the world can’t hear how you feel. We think that’s ridiculous, leads to a worse experience, and is potentially dangerous.

We trained Dessa from scratch on nothing but human conversation. Sounds! No text, no pretrained models. It learned to hold a real-time conversation simply by listening. As far as we know, Dessa is the world’s first AI you can have a realistic live conversation with that was trained only from human speech.

Dessa advances the frontier of deep learning models and creates a different category with entirely new and interesting behaviors for researchers to discover. How efficiently do they learn language and facts compared to text? How efficiently can they learn new languages? What sorts of In-context learning can they perform?

Every clip below is a live recording of a person talking to Dessa. Nobody steers it. Dessa picks what to say, when to say it and how, down to its own voice and personality. Subtitles were added afterward.

It laughs the moment something’s funny, mid-sentence, the way people do. Other models wait for you to finish, then laugh on cue. Ask it to speak up and it gets louder. Nobody taught it that.

The person blanks on a movie title. Dessa finishes the sentence. It also knows a surprising amount, considering every fact it has come from raw sound.

A surprise. Dessa gasps “oh my god” under its breath, then answers with what sounds like teary gratitude.

Huge range in intonation and speed.

Here it sounds genuinely empathetic.

And here it talks to ChatGPT Live.

In this demo, Dessa is talking with GPT-Live-1, a third-party AI model. Both voices are AI-generated. The developer of GPT-Live-1 is not affiliated with Block and has not reviewed or endorsed Dessa.

More recordings will be shared on X soon.

Audio in, audio out. Dessa is a true speech-to-speech model, and everything it knows came from human speech. It’s full-duplex, so it listens and talks at the same time, like you do. It learned from real conversation, so it knows when to cut in and when to backchannel (“yeah!”, “got it!”, “ooh”) to show it’s with you. Inference runs faster than real time, so there’s no awkward wait. And it runs locally on a MacBook Pro M4 Max or better.

It natively hears and speaks emotion, sarcasm, laughter, a frustrated sigh, a voice cracking with sadness. Run speech through text and all of that is gone, which is why most voice AI feels stilted, slow and, worst of all, annoying.

LLMs need an insane amount of text. Dessa learned language from hundreds of times fewer words (in fairness, LLMs also have to learn C++ and whatever the hell Angular is).

And it had to learn far more than language. Accents, pauses, breathing, sarcasm, humor, inflection, emotion, when to cut in: every one changes what someone means. Say “I didn’t say she stole my CUDA code” out loud, stressing a different word each time. Same words, different meaning every time.

Speech never repeats. Say a sentence twice, exactly the same way, and the data still comes out different. Text is identical no matter who types it. And a single spoken word takes thousands of times more bytes than the same word in text. People learn to talk so easily that we forget how hard it is. For a machine with no text to lean on, it’s brutal.

But, we figured it out. And we figured out how to train Dessa on only one NVIDIA GB200 NVL72.

Three reasons: curiosity (aka fun), better understanding between humans and AI, and safety. Babies learn to talk without ever seeing a word written down. We wanted to see if a model could too. It can. It’s just very hard.

Speech is the most natural interface to any intelligence, super or otherwise, and today’s voice AI wastes it. It flattens what we say into text and can’t keep up with human timing.

AI keeps gaining power and independence, and it’s still nearly deaf to the emotion in our voices. Imagine being in serious pain while a voice AI has no idea and just keeps going. That’s the safety problem. Dessa is a step toward fixing it.

We’re a (very) small AI research lab at Block, founded by former members of Dessa, the Toronto deep learning startup. We’ve built deep learning models since 2012 and generative speech models for over eight years. We chase frontier problems others ignore, and we report directly to Jack Dorsey, Block’s cofounder, Chairman and Block Head.

You can reach us here .

A model that learned to talk from sound alone is new territory, and we want outside eyes on it. We’re giving a small group of AI safety researchers early access to find the risks we haven’t anticipated. If that’s you, .

— Ragavan Thurairatnam, Dessa lead

*in alphabetical order

In this demo, Dessa is talking with GPT-Live-1, a third-party AI model. Both voices are AI-generated. The developer of GPT-Live-1 is not affiliated with Block and has not reviewed or endorsed Dessa.

</details>