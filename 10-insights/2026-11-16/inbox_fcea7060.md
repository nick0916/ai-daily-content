---
id: inbox_fcea7060
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2316-latent-space-building-visual-intelligence-andreas-bla-7cc2]]"
title: "Building Visual Intelligence — Andreas Blattmann & Dustin Podell, Black Forest Labs"
url: https://latent.space/p/bfl/
source: latent-space
published_at: 2026-11-16T21:38:03+00:00
fetched_at: 2026-11-17T23:22:50.111161+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Black Forest Labs 主張讓模型同時用靜態圖、影片與聲音三種訊號學習，來取得對真實世界的視覺理解。 **Why** 靜態圖只能呈現物體位置，影片才能呈現動態過程，聲音則能補足畫面沒拍到的資訊（如撞擊時間），因此 BFL 認為要走向「視覺智慧」需整合這些訊號。 **How** 以 FLUX 3 同時訓練圖像、影片與音訊；影片升頻器沿用同一個 FLUX 3 backbone，以保持時間一致性，避免逐幀處理造成閃爍。 **What** Latent Space 訪談 BFL 的 Andreas Blattmann（Latent Diffusion 共同發明人）與 Dustin Podell（FLUX Kontext 負責人、SDXL 第一作者）。內容涵蓋 FLUX 3、運動學習、flow matching、自迴歸 vs. diffusion 的取捨、世界動作模型與 2027 機器人。Kontext 早期實驗只用一小組帶關係標註的照片、數小時訓練就能讓模型把 logo 放上襯衫，之後才投入數月做資料與模型。"
key_points:
  - "FLUX 3 同時用圖像、影片與聲音三種訊號訓練，影片升頻器沿用同一 backbone 以維持時間一致性"
  - "自迴歸可一次從訓練樣本的所有 token 學習，diffusion 可把長取樣過程蒸餾成少數步驟，取捨取決於付費在訓練還是等待生成"
  - "Kontext 早期實驗：小組帶關係標註的照片、數小時訓練即可讓模型把 logo 放上襯衫，驗證後才投入數月做資料與模型"
tags: [black-forest-labs, flux-3, video-generation, world-models, latent-space-podcast]
topics: [foundation_models.open_weights, research.training, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Building Visual Intelligence — Andreas Blattmann & Dustin Podell, Black Forest Labs

Black Forest Labs 主張讓模型同時用靜態圖、影片與聲音三種訊號學習，來取得對真實世界的視覺理解。

**Why** 靜態圖只能呈現物體位置，影片才能呈現動態過程，聲音則能補足畫面沒拍到的資訊（如撞擊時間），因此 BFL 認為要走向「視覺智慧」需整合這些訊號。

**How** 以 FLUX 3 同時訓練圖像、影片與音訊；影片升頻器沿用同一個 FLUX 3 backbone，以保持時間一致性，避免逐幀處理造成閃爍。

**What** Latent Space 訪談 BFL 的 Andreas Blattmann（Latent Diffusion 共同發明人）與 Dustin Podell（FLUX Kontext 負責人、SDXL 第一作者）。內容涵蓋 FLUX 3、運動學習、flow matching、自迴歸 vs. diffusion 的取捨、世界動作模型與 2027 機器人。Kontext 早期實驗只用一小組帶關係標註的照片、數小時訓練就能讓模型把 logo 放上襯衫，之後才投入數月做資料與模型。

### 重點
- FLUX 3 同時用圖像、影片與聲音三種訊號訓練，影片升頻器沿用同一 backbone 以維持時間一致性
- 自迴歸可一次從訓練樣本的所有 token 學習，diffusion 可把長取樣過程蒸餾成少數步驟，取捨取決於付費在訓練還是等待生成
- Kontext 早期實驗：小組帶關係標註的照片、數小時訓練即可讓模型把 logo 放上襯衫，驗證後才投入數月做資料與模型

**原文：** [latent-space](https://latent.space/p/bfl/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This episode is sponsored by Deepgram. Try Deepgram for voice agents that truly understand your context! #contextiseverything Not many people know that Stable Diffusion is why I went fulltime into AI (I aptly titled Multiverse, not Metaverse to call out Zuck’s mistaken investment). It turns out that Dustin Podell also had the same aha moment - quitting his day job when the model came out. But we took very different paths... I stuck to what I knew in human content creation, and Dustin immersed deep into AI content creation with Andreas Blattmann , co-inventor of Latent Diffusion and the rest of the world-leading imagegen crew at Stability AI. Stability fell apart, but Anj Midha helped the core group spin out to BFL, which immediately built an incredible new imagegen model in the Flux series. But why are they now going into video and world models? Andreas gives an example you can try with one hand. If somebody tosses you a ball, your hand starts moving before the ball reaches you. You can do that without being able to write down the trajectory. When he talks about building visual intelligence , that’s the kind of knowledge he means. A still can show you where the ball is. A video shows you how it got there. The sound of impact can tell you when it hit something, even if the camera missed the contact. That’s BFL’s argument for training FLUX 3 on the three signals together. BFL’s FLUX 3 release The horse in motion is one of the FLUX 3 examples we show in the intro. The audio examples are worth playing with the sound on. FLUX 3 Video What a moving camera teaches you Suppose the camera starts in front of a person and pans around them. At some point the model owes you the back of their head. Andreas thinks ordinary two-dimensional video contains a great deal of evidence about what objects look like from other angles. That doesn’t settle whether a model “understands physics,” a point we go back and forth on. It does give you a much better test than asking whether one frame looks convincing. There’s a good engineering example late in the episode. Sharpen each frame of a clip independently and each frame might look terrific. Hit play and the extra detail can shimmer, because the upscaler made a slightly different decision every time. BFL derives its video upscaler from the same FLUX 3 backbone. Temporal consistency matters even when all the user asked for was a higher-resolution file. What’s worth spending training compute on? One of the questions I had for them was whether autoregression was taking over image generation. Andreas gives the other side its due. An autoregressive model can learn from all the tokens in a training example at once. On the diffusion side, the team can distill a long sampling process down to a handful of steps. Which advantage matters depends on whether you’re paying to train the model or waiting for an image to finish. Dustin’s early Kontext experiment is a nice example of how they decide where to invest. He suspected an image model that could draw a dog wearing a hat already knew something about where hats go. He and a colleague collected a small set of photos labeled with relationships. A training run of a few hours got the model to put a logo on a shirt. It was rough, but it was enough to take to the next offsite. The team then spent months on the data and the model. FLUX Kontext examples My favorite user story comes near the end. People were feeding FLUX old, degraded family photos, restoring them, then showing the pictures to their families. Dustin says he hadn’t predicted that use. After talking about preserving somebody’s identity across edits and across frames, it’s a lovely example of who actually notices if you get it right. Show notes BFL explains what a still image, a moving camera and a soundtrack each contribute during training. FLUX 3 launch and research overview Watch and listen to the results of generating video and sound together. FLUX 3 Video demos See how the lab teaches a model to make a requested change while preserving the rest of an image. FLUX Kontext examples Andreas Blattmann co-created Stable Diffusion and co-invented the latent diffusion method behind it. Guest bio · Original research Dustin Podell led FLUX Kontext and was the lead author of SDXL. Dustin’s project credits · FLUX Kontext · SDXL The first Latent Space essay grew out of the Stable Diffusion release. Multiverse, not Metaverse Chapters 0:00 Host introduction 3:39 Cold open 4:23 Black Forest roots 9:23 Dustin’s path 17:04 Visual intelligence 27:38 Inside SDXL 33:59 Learning motion 39:57 Flow matching 46:57 Starting BFL 50:36 Deepgram sponsor break 51:43 Early use cases for FLUX 54:58 Editing with Kontext 1:03:15 Training data 1:07:32 Testing an edit 1:13:12 Autoregression 1:20:50 World action models 1:30:08 Robotics in 2027 1:32:16 Who uses FLUX?

</details>