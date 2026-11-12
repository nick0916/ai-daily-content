---
id: inbox_44c01c80
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-lobsters-ai-writing-a-siggraph-paper-from-scratch-d59a]]"
title: "Writing a SIGGRAPH paper from scratch"
url: https://alexandergoslin.me/writing-a-siggraph-paper-from-scratch/
source: lobsters-ai
published_at: 2026-11-11T10:34:08-06:00
fetched_at: 2026-11-12T03:04:04.666964+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位軟體工程師以個人專案 Terrain Diffusion 寫成的論文獲 SIGGRAPH 2026 接受。 **Why** 作者想用擴散模型生成可無限延伸、能直接放進遊戲引擎的地形，並解決區塊相接時邊緣不吻合的問題。 **How** 作者先補足數學與機器學習基礎，再從領域 SOTA 論文的 related works 反向追溯參考文獻；專案中提出無限生成演算法 InfiniteDiffusion。 **What** 作者使用一張 RTX 3090 Ti 完成研究，2025 年 12 月發表 ArXiv preprint，2026 年 1 月投稿 SIGGRAPH 2026；論文經 Minecraft mod、Two Minute Papers 與 Hacker News 傳播。"
key_points:
  - "專案目標是可無縫接入幾乎任何遊戲引擎的學習式程序化地形生成器；核心為擴散模型的無限生成演算法 InfiniteDiffusion"
  - "學習路線：先花約 1.5 年讀完微積分與線性代數，再用約 1 年完成其餘書單；之後每天 1–2 小時、目標約 10 頁，從 SOTA 論文的 related works 反向追參考文獻"
  - "作者不建議以 AI 取代學習，只用來回答單一問題；偏好書籍，理由是不需等待他人、可自行決定閱讀速度，且 AI 會幻覺、在 ML 直覺上不可靠"
tags: [siggraph, diffusion-models, terrain-generation, self-learning, research-publishing]
topics: [research.training]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Writing a SIGGRAPH paper from scratch

一位軟體工程師以個人專案 Terrain Diffusion 寫成的論文獲 SIGGRAPH 2026 接受。

**Why** 作者想用擴散模型生成可無限延伸、能直接放進遊戲引擎的地形，並解決區塊相接時邊緣不吻合的問題。

**How** 作者先補足數學與機器學習基礎，再從領域 SOTA 論文的 related works 反向追溯參考文獻；專案中提出無限生成演算法 InfiniteDiffusion。

**What** 作者使用一張 RTX 3090 Ti 完成研究，2025 年 12 月發表 ArXiv preprint，2026 年 1 月投稿 SIGGRAPH 2026；論文經 Minecraft mod、Two Minute Papers 與 Hacker News 傳播。

### 重點
- 專案目標是可無縫接入幾乎任何遊戲引擎的學習式程序化地形生成器；核心為擴散模型的無限生成演算法 InfiniteDiffusion
- 學習路線：先花約 1.5 年讀完微積分與線性代數，再用約 1 年完成其餘書單；之後每天 1–2 小時、目標約 10 頁，從 SOTA 論文的 related works 反向追參考文獻
- 作者不建議以 AI 取代學習，只用來回答單一問題；偏好書籍，理由是不需等待他人、可自行決定閱讀速度，且 AI 會幻覺、在 ML 直覺上不可靠

**原文：** [lobsters-ai](https://alexandergoslin.me/writing-a-siggraph-paper-from-scratch/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Writing a SIGGRAPH paper from scratch.

Baby Steps

An Aside on Books

Technical Backgrounds

Forming A Thesis

Training the First Models

The Cheap Experiment

Anticipating Failure

The Expensive Experiments

Deciding to (Try to) Publish

Turning Code Into Research

Releasing the preprint & submitting to SIGGRAPH

The Rebuttal

Acceptance and Revision

Reception & The Future

References

Alexander Goslin

40 minute read

In September 2024, my final year of college, I began working on a side project called “Terrain Diffusion.” The goal was to create a learned procedural terrain generator that could drop into almost any game engine with minimal friction. I had nothing but one RTX 3090 Ti, which I bought with money from an internship at Walmart that prior summer. As I worked on the project, I developed InfiniteDiffusion, a new algorithm for infinite generation with diffusion models [5] . I continued this work throughout my final year of college, a move to California, and a full time SWE job at Walmart. In December 2025, I released the first preprint to ArXiv, and in January, I submitted it to SIGGRAPH 2026, where the paper was later accepted.

To my delight, the paper was very well received! I converted Terrain Diffusion to a Minecraft mod, which was showcased by AsianHalfSquat to over a million viewers. The paper’s launch on Twitter went about as viral as I could hope, also nearing a million views. And shortly after, the paper was showcased by Two Minute Papers . The preprint also reached the front page of HackerNews .

This paper was the result of about a decade of self-study in machine learning, though publishing did not become a goal of mine until much later. I don’t intend for this to be a tutorial for publishing at SIGGRAPH (or any venue for that matter), since I don’t consider myself to be an expert on that topic. Instead, I’ll share my own experiences so that you can have a better idea of what to expect if you decide to take the same route I did. I’ll also share how I learned everything I know, because for that I do have a process, and it’s proven to be quite effective.

I began programming when I was 13, and over the course of about a year developed a modest portfolio of mostly simple Java and C# applications. None of these were particularly impressive, but I found the entire process of learning and building to be quite fulfilling. As I became more skilled it became more appealing to specialize, and build things that I could be genuinely proud of not just for the process, but for the result. As someone who enjoys math, I was particularly interested in projects that would allow me to mix programming with mathematics, and use both skills at once. Graphics was one such area, and I spent much of the following year learning C++ and various graphics libraries.

In an alternate universe I might have gone all-in on rendering, but around this time StyleGAN came out [8] , generating photorealistic images from nothing, and it blew my mind. Skimming the paper, I found much of it surprisingly intuitive, though there were many terms I had never heard of, and so the full picture remained out of reach. Regardless, I had countless ideas for how this technology could be used (including as a terrain generator!), and so I decided to learn how to use it.

I initially tried following TensorFlow tutorials, but this quickly proved futile. I could get through them by following instructions, but as soon as it was time to go out on my own and start applying the knowledge, I had no idea what to do (in fairness, this may have just been the unreasonably confusing design of TensorFlow v1). I figured I was suffering from prerequisite debt – the tutorials taught me how to put layers together, but without knowing what those layers actually represented, that knowledge was mostly useless. So I put together a study plan, starting with all of the math I thought might be useful, and ending with “A Super Harsh Guide to Machine Learning” , which seemed pretty comprehensive. That led to this final list:

I dedicated about 1-2 hours a day to finishing this plan, aiming for about 10 pages a day. I was able to get through Calculus and Linear Algebra in ~1.5 years, and finished the remainder of the plan after another year. For the math textbooks, I mostly didn’t bother doing the exercises in full, and instead would read them and think through the solutions in my head. I found it was usually pretty obvious when I did or didn’t understand something this way, if I was being honest with myself.

After finishing the textbooks, I spent 1-2 years reading various papers from ArXiv, mainly focusing on computer vision. At this point, I found the most effective strategy was to find the state of the art for whatever topic I was interested in, and from there recursively go through the references to find work that was either a direct prerequisite or otherwise useful. I found the related works sections to be particularly helpful, since they typically cover the prior SOTA, often categorized by technique, giving you a convenient chain to follow. Any methods that were crucial to the implementation, or that I’d seen pop up frequently in other papers, I would also go read about in more detail. Simultaneously, I’d begun learning about the code side of things, and once I understood the textbooks, learning the libraries became almost trivial – the learning curve was mostly adapting to Python as someone most familiar with statically-typed languages like Java and C++.

I have nearly no regrets with the plan I followed, and for those interested in learning the fundamentals today, I don’t think much modification is required. Even as the field of ML has grown exponentially, the fundamentals have remained largely unchanged. That being said, you can largely skip Part III of the deep learning book, as that time is probably better spent learning about the things that the book was too early for, like transformers and diffusion models. Diffusion models in particular have had quite a complicated history, but thankfully there is a great (free) textbook [10] on the topic, which I would highly recommend if it is a topic that interests you. Transformers on the other hand, at their core, have remained largely the same since Attention Is All You Need [18] , except for a handful of advancements you could catch up on in a few days 1 .

In summary, if I were starting over, I’d follow the same plan except for these changes:

While the fundamentals haven’t changed much, each specialty has a substantial literature of its own. What to read next depends on what you want to work on, so beyond this foundation, I’d follow the same approach: start with surveys and recent papers, then work backward through their references.

I believe books are the best way to learn practically any technical topic. This is an opinion based on my experience, but there is reasoning for it that generalizes. I think if you are serious about learning fast, your first priority should be to avoid bottlenecks, or anything that prevents you from learning as fast as your brain will allow you to. This includes people. If you need to wait on someone else to teach you something, that person becomes a bottleneck. Of course, if you have access to a smart person and questions your materials don’t cover, then ask them. Just don’t wait for them.

Online courses and videos don’t suffer from this problem, but books still have many advantages. They tend to be both more detailed and comprehensive, which helps with understanding and generally learning more. With text, you can read at your own pace. With video, you must follow the pace of the lecturer, which I would argue is rarely in-sync with your own ability to process information. With video, you must watch contiguous sections of video, whereas with text you can dart between precisely the words you need to understand the topic at hand. Textbooks tend to carry far more exercises as well, and are typically easier to search through if you need to backtrack.

Also, do not dare use AI for anything more than individual questions you have while learning from another source. AI makes a lot of stupid decisions, hallucinates (yes, still), and generally doesn’t have great intuitions about many topics, especially ML in my experience. If everything you learn comes from an AI, you’ll never be able to detect when it’s being stupid. Anyways, onto the paper.

If you’ve ever played any game with procedural terrain, most famously Minecraft, you were looking at procedural noise . Procedural noise has been around for about 40 years now, and is used to algorithmically produce infinite textures. Infinite procedural worlds typically convert this into 3D by reading this texture as a heightmap, so white corresponds to high elevations, and black to low ones. An alternative, more complex method (not used here), is to generate 3D noise and read it as a volume, so white corresponds to filled space and black to empty space. The vast majority of terrain generators rely primarily on Perlin noise [13] (or Simplex, though they look very similar), which is stacked and scaled to produce multiple levels of detail, and then combined with hand-written post-processors to make the infinite worlds you are probably familiar with. This process of stacking noise is illustrated below.

Procedural noise is particularly useful because they typically possess many convenient properties. While not all procedural noises have the same properties, there are a handful that most terrain generators require:

The first property is obviously important for generating infinite, diverse worlds. The second means you can share worlds with friends, and you don’t need to store every output indefinitely. The third is important for parallelization, since it allows you to compute many points in parallel on the GPU, but it also enables teleportation and multiplayer, since two distant locations can be computed independently.

In the 2010s, GANs and diffusion models were invented. GANs generated realistic images [4] by training a generator model to create images, and a discriminator model to tell apart real images from fake ones. The generator would learn to fool the discriminator, and after a while would generate images that looked very similar to real ones. Diffusion models came a bit later [16] , demonstrating that it was possible to generate data by instead starting with a noisy image, and iteratively removing noise until there was no noise left, leaving you with a clean fake image. Diffusion models quickly became the standard for image generations, proving to be far easier to train and scale than GANs, which were notorious for being unstable, especially when scaled. The main tradeoff was that diffusion models were considerably slower, since they required dozens of steps (thousands when they were first released) to generate an image, as opposed to GANs which took only one. Later, distillation enabled diffusion models to generate images in as few as one step, though this required additional training stages and until recently required a considerable sacrifice to quality.

Both of these methods were quickly applied to terrain generation. By learning from real-world datasets, they were able to generate incredibly realistic terrain. However, they were typically too slow to use interactively, and due to factors I’ll discuss later, the quality of AI terrain generators was bottlenecked, so it didn’t improve at quite the same pace as general image generation. Additionally, learning to generate a single patch of terrain is a much simpler problem than generating an infinite world. Simply placing generated images next to each other would leave mismatched edges, and even overlapping patches could predict different elevations at the same location.

My goal was to create a terrain generator that could replicate all the important properties of procedural noise, but otherwise use the best technology available for image generation. 

[... truncated for safety ...]

</details>