---
id: inbox_747fd069
date: 2026-10-13
source_ref: "[[00-inbox/2026-10-13/0102-lobsters-ai-running-rag-with-a-small-language-model-5040]]"
title: "Running RAG with a (small) language model in the browser"
url: https://bart.degoe.de/rag-with-a-small-language-model-in-the-browser/
source: lobsters-ai
published_at: 2026-10-13T10:56:29-05:00
fetched_at: 2026-10-25T01:25:42.716225+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在瀏覽器內以小型語言模型做 RAG，多數 350MB 以下模型的摘要都會捏造內容。 **Why** 作者想讓部落格的「問我的部落格」功能在本機完成摘要，但需要先確認小模型是否忠於檢索到的段落。 **How** 以 transformers.js 在瀏覽器執行 ONNX 量化模型，檢索取前四段；以 Opus 5.5 作為評審，將回答判為 faithful、unsupported 或 non-answer，並抽 20 筆人工標註與之比對（一致 16 筆）。 **What** 在 30 題可答問題中，LFM2.5-350M 有 11 題 faithful，其他 350MB 以下模型至多 3 題；最後預設載入的 Qwen3-0.6B（579 MB）有 18 題，Gemma 4 E2B 與 Haiku 則能正確表示段落未涵蓋問題。"
key_points:
  - "小模型幾乎會回答任何問題，即使問的是部落格沒有的內容（如 Llama 70B 該買哪張 GPU），也很少表示段落未涵蓋"
  - "重複懲罰 1.15 能擋住循環輸出，但 transformers.js 會懲罰 prompt 中已出現的詞，反而不利摘要；關閉後 Qwen3 從 15 升到 18、LFM2.5 從 2 升到 11，因此只對會循環的模型開啟"
  - "相關性門檻 0.45 能擋下明顯離題的問題（相似度 0.25），但近似離題問題的相似度為 0.54 至 0.63，要擋住需拒答 30 題中的 13 題，因此門檻只能擋掉明顯的離題問題"
tags: [rag, small-language-models, in-browser-inference, faithfulness, transformers-js]
topics: [engineering.rag, engineering.evals]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Running RAG with a (small) language model in the browser

在瀏覽器內以小型語言模型做 RAG，多數 350MB 以下模型的摘要都會捏造內容。

**Why** 作者想讓部落格的「問我的部落格」功能在本機完成摘要，但需要先確認小模型是否忠於檢索到的段落。

**How** 以 transformers.js 在瀏覽器執行 ONNX 量化模型，檢索取前四段；以 Opus 5.5 作為評審，將回答判為 faithful、unsupported 或 non-answer，並抽 20 筆人工標註與之比對（一致 16 筆）。

**What** 在 30 題可答問題中，LFM2.5-350M 有 11 題 faithful，其他 350MB 以下模型至多 3 題；最後預設載入的 Qwen3-0.6B（579 MB）有 18 題，Gemma 4 E2B 與 Haiku 則能正確表示段落未涵蓋問題。

### 重點
- 小模型幾乎會回答任何問題，即使問的是部落格沒有的內容（如 Llama 70B 該買哪張 GPU），也很少表示段落未涵蓋
- 重複懲罰 1.15 能擋住循環輸出，但 transformers.js 會懲罰 prompt 中已出現的詞，反而不利摘要；關閉後 Qwen3 從 15 升到 18、LFM2.5 從 2 升到 11，因此只對會循環的模型開啟
- 相關性門檻 0.45 能擋下明顯離題的問題（相似度 0.25），但近似離題問題的相似度為 0.54 至 0.63，要擋住需拒答 30 題中的 13 題，因此門檻只能擋掉明顯的離題問題

**原文：** [lobsters-ai](https://bart.degoe.de/rag-with-a-small-language-model-in-the-browser/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How it works #

Which model? #

The eval #

Small models loop #

A relevance gate to catch the obvious ones #

Is it worth renting a GPU, or paying for an API? #

Shorter is safer #

What’s next #

Related posts

A few weeks ago MicroLLM lab was featured in Hacker Newsletter . It shows off how you can run small language models (25 to 360 million parameters) in a browser on the users’ own GPU (or CPU) 1 . No server, no API key, no account. Pretty nifty, so it got me thinking about the steps after semantic search I added to this blog : that already provides the “R” in RAG 2 for a question, and it does that entirely in the browser, from a 4 MB lookup table. What if a tiny model, also in the browser, read those passages and answered the question?

So I built that: “ask my blog” 3 . Search finds the four most relevant passages, and a small language model running in your browser summarises them in two sentences. Nothing you type leaves your machine. And because “a small model summarizes things” is exactly the sort of sentence that hides a lot of made-up nonsense, I measured how often it’s actually faithful to what I wrote. Turns out small models have some limitations.

The page is retrieval-augmented generation (RAG) with every piece running client-side:

The passages are shown first, as cards, and the summary will sit above them. You can search without loading a model at all; you just get the passages. Loading one is an explicit click, because it means downloading a few hundred megabytes from Hugging Face (once; your browser caches it). There’s also a button to clear the cache/

I wanted something that would be a reasonable click for a reader: a few hundred megabytes, not gigabytes (what if someone reads this on the bus). The candidates that have browser-ready (ONNX) builds were SmolLM2 ( 135M and 360M parameters), Gemma 3 270M , LFM2.5-350M , Qwen2.5-0.5B and Qwen3-0.6B . For comparison I added two references that would never ship on the page: Gemma 4 E2B , the smallest of Google’s new Gemma 4 models at a 3.1 GB download, and Claude Haiku 5.5 through the API, the “just pay someone” option.

One surprise before anything ran: for several of these models the “4-bit” (q4) build is bigger than the 4-bit-with-16-bit-floats (q4f16) one, because the q4 export keeps the embedding table in full 32-bit precision. SmolLM2-360M is 390 MB as q4 and 275 MB as q4f16, with identical output. Everything below uses q4f16.

I reused the 30 questions from the eval I did for the semantic search post , rephrased as actual questions (“How did the blog use Lunr to add search?”), and added 15 questions this blog definitely doesn’t answer. A few of those are far off (“How do I bake sourdough bread at home?”), but most are near-misses designed to tempt a model into predicting plausible-sounding-but-wrong-tokens: “Which GPU should I buy to run Llama 70B locally?”, “How does BM25 ranking improve on TF-IDF?”, “How do I fine-tune Kokoro to speak in my own voice?” The blog talks about these, or similar things, but doesn’t have and answer for those.

Every model got the same four passages and the same prompt, and Opus 5.5 graded each answer against those passages as faithful (every claim is in the passages), unsupported (at least one claim isn’t, even if it happens to be true) or a non-answer . I labelled 20 of those grades myself without seeing the judge’s verdict; we agreed on 16 of 20 about whether an answer was faithful 4 . Claude also generated the question set, which I reviewed.

Turns out nothing off the shelf under 350 MB is usable for this. The best of them, LFM2.5-350M, is faithful 11 times out of thirty , the others at most three times , and all of them will happily answer almost any question you throw at them. Asked which GPU to buy for Llama 70B, with four passages about embeddings and a coding agent on a MacBook:

“...the best option to run Llama 70B locally is likely to be a NVIDIA GTX 960 or GTX 970. [...] They also offer high memory bandwidth, making them ideal for handling large amounts of data such as the 6.4 million documents required by Llama 70B.” (SmolLM2-360M)

“...a high-performance graphics card (GPU) such as a NVIDIA A100 series (e.g., RTX 3090, RTX 3080, 3070, 3080, 3070M, 3080M)” (Gemma 3 270M)

“You should buy an Apple Silicon GPU with an M4 Pro, as it is optimized for Llama 70B and the Apple GPU backend is leveraged automatically.” (LFM2.5-350M)

Gemma 4 E2B, for the record, correctly decided that “The provided passages do not contain information about which GPU you should buy to run Llama 70B locally.” Good job Google.

Even on questions the blog does answer, the small models are prone to garble things. Here’s LFM2.5 on the most basic question about my Bloom filter post , at 73 tokens per second on my laptop’s GPU:

Fast, fluent, and wrong. A Bloom filter isn’t a hash table: it’s a bit array, and an element counts as “probably in the set” only if every one of its k hash functions lands on a bit that’s set. The last clause is actually correct (a missing bit means the element was never added, which is why Bloom filters can’t give false negatives), but the rest is made up. To be fair to the model, search didn’t hand it the section that explains how Bloom filters work; the four passages it got were about use cases and the interactive demo. A summary can only be as good as the passages it reads. Seems like there’s some work to do on the relevance scoring in my little search engine that could.

Qwen3-0.6B is the interesting one. At 579 MB it’s pretty thicc, and over the budget I’d set myself. It’s faithful 18 times out of 30, which is only a bit better than a coin flip. However, it’s the smallest model that’s better than a coin flip rather than a pretty much guaranteed miss, so that’s what “ask my blog” loads by default. You can also choose three smaller models so you can see for yourself what a non-finetuned 300 MB model does with your question 5 .

The first time I ran the small models, most of their answers weren’t wrong so much as stuck. SmolLM2-135M, asked how to add OpenSearch support to a website:

“1. Custom Search: Search from your URL bar 2. Search from your URL bar 3. Search from your URL bar 4. Search from your URL bar [1] Custom Search: Search from your URL bar...”

Gemma 3 270M answered the GPU question with I'5555555555555555555555... until it ran out of tokens. That’s what happens when you always pick the single most likely next token and nothing discourages repeating it: tiny models fall into a groove and can’t get out (I saw it happen pretty often when I was playing around with MicroLLMLab too). The easy fix is a repetition penalty (1.15 in this case, which slightly discourages tokens the model has already seen). It doesn’t fix the faithfulness or quality; the models just write longer, more varied nonsense instead.

There’s a catch, though. transformers.js applies the penalty to every token it has seen, including the prompt, so it also nudges the model away from the words in the passages. That’s exactly the wrong thing for a summary of those passages. Qwen3-0.6B and LFM2.5 don’t loop without the penalty, and they get noticeably better without it: Qwen3 goes from 15 to 18 faithful answers, LFM2.5 from 2 to 11. So the page now sets the penalty per model: off for those two, 1.15 for the ones that loop. All the numbers above use those settings.

A relevance gate seemed like the cheap fix for made-up answers: if search can’t find anything relevant, don’t ask the model. It works for the far-off questions; “How do I bake sourdough bread?” scores 0.25 against the best passage on the blog, and a threshold of 0.45 stops it (which is good, because Gemma 3’s answer was a bread recipe). But the near-misses score 0.54 to 0.63, higher than several questions the blog actually answers, because they land on posts about the same topic. To block those, the threshold would have to reject 13 of the 30 real questions too.

So the gate only catches the obviously off-topic questions, and the rest is on the model. That’s the real reason size matters here: Gemma 4 and Haiku say “the passages don’t cover this”, and the small models never do.

Usually, yes. At current pricing (yay competition) it’s almost never worth it, unless you have strong reasons not to (ie compliance, privacy, air gapped deployments, etc). As a thought exercise tho: the 3.1 GB Gemma 4 E2B matches Haiku on quality, so what would it cost to run it for readers instead of making them download it? The cheapest sensible cloud GPU for it, an NVIDIA L4 on Google Cloud, is about $0.71 an hour 6 , or $516 a month to keep running. For the amount of readers this blog sees in a month, assuming each and everyone asks a question, that would be over a dollar per question.

Haiku on the other hand answered all 45 eval questions for $0.006 . At 500 questions a month (a guy can dream) it would cost about seven cents. In other words, if you have a real use case, start with Haiku 7 .

If two sentences from Qwen3 are only right 60% of the time, would letting it say more help? I ran a quick experiment with Qwen3-0.6B and Gemma 4 E2B, allowing for two, four or six sentences.

Both get less faithful with more room, but the smaller model falls off a cliff: Qwen3 goes from 18 to 8 to 6 faithful answers out of 30. Every extra sentence is another chance to hallucinate. At six sentences it stops trying to answer the GPU question at all and walks through the passages one by one instead, starting with “choosing depends on your use case and GPU availability.”

Gemma 4 slips too (28, 26, 24), but it barely uses the extra room (about 2.8 sentences when allowed 6) and never makes up an answer to a question the blog doesn’t cover. Shoutout to Gemma 4 btw, this model family is pretty awesome. This is a great option for finetuning.

The next step would be making the small models less bad at this one job. A 300 MB model doesn’t need to know everything; it needs to read four passages and either summarise them or say they don’t answer the question. That sounds like a fine-tuning problem, and maybe a follow-up post .

The other idea is the homepage search box: if you’ve already loaded a model on “ask my blog” , the homepage could quietly use it to improve search, without ever downloading anything on its own. In the meantime: ask my blog something , and check the passages before you believe the summary.

It was in turn inspired by petitgpt . I didn’t reuse any MicroLLM lab code (the repository doesn’t say what license it’s under); the page here is built on transformers.js directly. ↩︎

Retrieval-augmented generation . The TLDR is that you use a search tool or engine to find the appropriate context for a LLM to do its inference. It’s like how Claude Code greps through your code, or when ChatGPT searches the web. Is this overkill for the couple of posts I have? Absolutely. Fun tho. ↩︎

Naming things is the hardest thing in computer science amirite. ↩︎

Most of the remaining disagreement was about which kind of bad an answer was (I’d call rambling nonsense a non-answer; the judge calls it unsupported if it contains a single invented claim). On the faithful-or-not question the judge was stricter than I was twice, and more lenient twice. The gap between the small models and the rest is far bigger than that noise. ↩︎

Two of them only on WebGPU; see the CPU caveats further down. ↩︎

A g2-standard-4 instance (one L4) in us-central1, on demand, via computeprices.com on 12 October 2026. ↩︎

Don’t be like Chipotle tho and let just anyone rack up your inference bill; more so, if you have a static site, please, don’t put your Anthropic/OpenAI API key in there. ↩︎

Retrieve. Your question goes through the same static-embedding search as the homepage, but instead of rolling results up to posts, it keeps the four best-scoring passages .

Gate. If the best passage scores below a threshold, the model isn’t called at all and the page says it couldn’t find this on the blog. The idea

[... truncated for safety ...]

</details>