---
id: inbox_34a1db78
date: 2026-09-29
source_ref: "[[00-inbox/2026-09-29/0102-lobsters-ai-text-to-meowdio-models-93bc]]"
title: "Text-to-meowdio models"
url: https://www.kmjn.org/notes/text_to_meowdio_models.html
source: lobsters-ai
published_at: 2026-09-29T11:51:35-05:00
fetched_at: 2026-10-25T01:26:32.361887+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用「表現範圍圖」檢視文字轉音訊模型能生成多大的變化，並以貓叫聲為例比較三個開放模型。 **Why** 常見指標如 FAD、CLAP 分數無法取代實際聆聽，需要另一種方式看清生成空間的分布。 **How** 生成 2,100 段音訊（3 模型 × 7 提示 × 100 樣本），計算 timbre、pitch、loudness 的特徵與一、二階差分後，以 PCA 降到二維。 **What** EzAudio 在「cat」類提示下常只生成靜音或背景噪音，加入動作描述後才會出現貓叫；「plaintively」在三個模型上的位移方向並不一致，且作者指出聲學特徵分布無法衡量品質。"
key_points:
  - "三模型各 100 個樣本 × 7 種提示，共 2,100 段音訊；特徵為 timbre/pitch/loudness 及其一、二階差分，PCA 降到二維"
  - "EzAudio 在無動作描述的提示下常產生靜音或背景噪音，加入「meowing」後大多會出現貓叫"
  - "「plaintively」在三模型上的質心位移方向不平行；timbre 空間中模型更分散，pitch 空間則趨於一致"
tags: [text-to-audio, evaluation, expressive-range, pca]
topics: [engineering.evals]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Text-to-meowdio models

用「表現範圍圖」檢視文字轉音訊模型能生成多大的變化，並以貓叫聲為例比較三個開放模型。

**Why** 常見指標如 FAD、CLAP 分數無法取代實際聆聽，需要另一種方式看清生成空間的分布。

**How** 生成 2,100 段音訊（3 模型 × 7 提示 × 100 樣本），計算 timbre、pitch、loudness 的特徵與一、二階差分後，以 PCA 降到二維。

**What** EzAudio 在「cat」類提示下常只生成靜音或背景噪音，加入動作描述後才會出現貓叫；「plaintively」在三個模型上的位移方向並不一致，且作者指出聲學特徵分布無法衡量品質。

### 重點
- 三模型各 100 個樣本 × 7 種提示，共 2,100 段音訊；特徵為 timbre/pitch/loudness 及其一、二階差分，PCA 降到二維
- EzAudio 在無動作描述的提示下常產生靜音或背景噪音，加入「meowing」後大多會出現貓叫
- 「plaintively」在三模型上的質心位移方向不平行；timbre 空間中模型更分散，pitch 空間則趨於一致

**原文：** [lobsters-ai](https://www.kmjn.org/notes/text_to_meowdio_models.html)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Text-to-meowdio models

Generative range analysis

Prompt: "sound of cat"

Object and action in the prompt

Descriptive modifiers

Cross-model agreement: What does "plaintive" mean?

Full Meowdio Explorer

Baseline Comparison

Prompt Specificity: Object vs. Action

Descriptive Modifiers: Distribution Shifts

Cross-Model Agreement: "Plaintive"

Meowdio Explorer

Unimpressed by AI

Text-to-audio models take a text prompt as input, and generate audio as output.
In principle they take any kind of prompt and generate any type of audio.
If you re-prompt them with the same prompt but a different random seed, you
should get a new example of audio for that prompt. But as you might imagine,
any given text-to-audio model is not equally good at all kinds of audio: nature
sounds, animal vocalizations, human vocalizations, music, etc. Furthermore,
the range of output is wider in some cases than others: a given model
may be able to produce a wide range of thunderclaps but have a relatively
narrow range of bird chirps, or vice versa.

Some collaborators and I proposed a methodology for exploratory data analysis
of the generative range of text-to-audio models, which is an aspect we don't
think has been studied in much detail:

The main visualization tool we use, an expressive-range plot , comes from
the procedural content generation (PCG) community, which uses it to analyze the
range of level generators and similar kinds of PCG systems that may be either
AI-driven or handcrafted generators (examples here and here ).
This post applies the methodology to the rather expressive special case of cat
vocalizations. Unlike in the PDF paper, you can also click on the dots in the
plots and listen to the generated audio. Advice: Use headphones if you
live with a cat!

For this post, I generated 2,100 clips of cats vocalizing, with seven different
prompts, three text-to-audio models, and 100 samples per prompt+model
combination. The models are intended to illustrate some of the range of current
model architectures and training sets:

In typical expressive range analysis, you choose domain-specific metrics for
the axes. To compare outputs more generally without hand-crafted metrics for
each prompt, in the paper we used three standard audio attributes: timbre,
pitch, and loudness. For each clip, we computed a feature vector of
timbre/pitch/loudness through the clip, as well as the 1st- and 2nd-order
differences (to capture variation over time). Then we reduced each to two
dimensions with principal components analysis (PCA) to plot it. This means the
axes are not directly interpretable as acoustic properties, but distance and
point clustering is meaningful (nearby points share similar acoustic profiles).
For this post, I ran one PCA reduction for all 2,100 clips, so points are
comparable between plots.

In the paper, we started with the prompt "sound of [x]" for
various objects [x] , to see what each model would produce without
being given an explicit verb. So in this post I'll also start with "sound
of cat" .

Toggle between Timbre, Pitch, and Loudness to see the point-cloud spreads on
each acoustic property. Click a point to listen.

Generative range for "sound of cat"

 Observations: Stable Audio Open and TangoFlux both generally produce
meowing, as one might expect. TangoFlux's meows are a bit more tightly
clustered in the expressive-range diagrams (and to my ears also sound like they
vary less). EzAudio surprisingly often just has silence or living-room
background noise, or a single faint meow in the whole 10 seconds; I believe
this is probably due to being trained on uncurated video captions, where cats
often appear silently. The fact that EzAudio is an outlier is particularly
visible on the Loudness plot.

We can try a few prompts to see how models respond to being more or less
specific about the desired object and action.

That produces 900 total samples (3 prompts x 3 models x 100 samples each). In
the visualization below you can check or uncheck each of the three prompts and
three models to see subsets.

Comparing bare noun ( "cat" ), baseline template, and explicit action ( "sound of a cat meowing" )

 Observations: As in the previous plot, EzAudio often doesn't produce a
meow with the "cat" or "sound of cat" prompts, but does start doing so (most of the time) when we explicitly say we want
the cat to be meowing. TangoFlux and Stable Audio Open tend to produce meows
for all three prompts, but it's interesting that the timbre range significantly
narrows when we specify meowing. (To see that, try selecting just one model and
the 1st and 3rd prompts.)

Something the paper left for future work was investigating how descriptive
modifiers impact expressive ranges. For this post I'll try four different
prompts that try to elicit qualitatively different types of cat vocalizations
(some of them not meows):

In addition to the dots for individual clips (as above), the plot below draws
an arrow from the centroid for the baseline "sound of cat" clips
to each of the other four prompts' centroids, showing how each prompt shifts
the model's output distribution. Select a model to compare how it responds
here, and click any centroid badge to listen to the clip nearest to the centroid.

Centroids and directional shifts from "sound of cat"

 Observations: Well, there is a lot going on here. Toggling between
models shows they respond differently to the modifiers. On timbre, TangoFlux
has particularly large centroid shifts (especially for "tiny kitten
meowing" ). On loudness, we can see again that EzAudio needs actions
specified to produce noticeable audio, so essentially any modifier
pushes in a similar direction. The Pitch view shows fairly strong directional
agreement in the effect of each modifier between TangoFlux and Stable Audio.

Listening to a few examples is also a good reminder that looking at the
distribution of purely acoustic features like these doesn't measure quality ,
which would need different metrics. Some of the hisses in particular seem to
blow out into something more like tape hiss, either due to semantic
mix-up or some kind of audio artifact. A lot of the purrs are also pretty
weird sounding.

To plot that differently, let's look at just one of the modified prompts,
but with all the models. The plot below shows "sound of cat" and "cat meowing plaintively" along with the shift in centroids from
the former to the latter prompt for all three models. I picked "cat meowing
plaintively" to look at in more detail because, subjectively, all three
models actually do fairly good interpretations of it, unlike some of the
artifacts in the hissing and purring prompts, so we can look for more subtle
distinctions.

Centroid shifts from baseline to "cat meowing plaintively"

 Observations: There are a few things we might look for here. If there
were some kind of consistent, direct acoustic meaning of "plaintive" as a
modifier, we might expect to see the arrows be parallel to each other, as in
some of the classic word2vec examples (although admittedly those examples are in embedding space, while we're in
a projected acoustic space). That clearly does not seem to be the case. We can
also look at the actual centroid locations and spreads of points, where there
does seem to be something interesting going on. In timbre space, asking for a
plaintive meow vs. a generic sound of cat seems to actually push the models
further apart; but in pitch space they converge to more similar generative
output.

Below are all 2,100 clips generated for this post. Select any combination of
models and prompts, switch between Timbre, Pitch, and Loudness plots, and
toggle whether points are colored by model or by prompt.

There are all kinds of metrics for text-to-audio generators: Fréchet audio
distance (FAD), CLAP score, etc. But there's no substitute for just listening to
the output. We think slicing and dicing the generative space with these kinds
of expressive-range plots is one way to get an ear on what's going on. 

Jonathan Morse, Azadeh Naderi, Swen Gaudl, Mark Cartwright, Amy K. Hoover, Mark J. Nelson (2025). Expressive range characterization of open text-to-audio models . In Proceedings of the AAAI Conference on Artificial Intelligence and Interactive Digital Entertainment , pp. 91-98.

Stable
Audio Open 1.0 : Continuous latent diffusion trained on ~486k open-license
clips from Freesound and the Free Music Archive (FMA), conditioned via
T5-base.

EzAudio : 1D
waveform VAE + DiT trained on AudioSet and VGGSound with synthetic captions,
followed by supervised fine-tuning on AudioCaps.

TangoFlux :
Flow-matching transformer pre-trained on WavCaps (~400k clips), fine-tuned on
AudioCaps, and aligned using direct preference optimization (DPO) on synthetic
CLAP-ranked preference pairs.

Bare noun: "cat"

Paper baseline: "sound of cat"

Explicit action: "sound of a cat meowing"

"tiny kitten meowing"

"angry cat hissing and growling"

"cat meowing plaintively"

"happy cat purring"

</details>