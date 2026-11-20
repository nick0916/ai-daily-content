---
id: inbox_4f68b306
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0106-lobsters-ai-rebuilding-my-local-voice-assistant-pipe-ac19]]"
title: "Rebuilding my local voice assistant pipeline"
url: https://blog.platypush.tech/article/Rewriting-my-voice-assistant-pipeline
source: lobsters-ai
published_at: 2026-11-19T13:50:25-06:00
fetched_at: 2026-11-20T01:15:02.250059+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "改用更抗噪的喚醒詞與語音端點偵測，讓本地語音助理結束對話更即時。 **Why** 作者自架語音助理誤喚醒與漏喚醒率高，且在噪音環境與廉價麥克風下，語音起訖判斷不穩。 **How** 以基於 microWakeWord 的新 plugin 取代 openWakeWord，並在共用音訊前處理層加入滯後門檻、0.5 秒多數決平滑與自適應噪音底線。 **What** 在作者的合成測試集（Piper 語音混合雜訊）中，對話結束時間從語音結束後 6–10 秒縮短至 1.0–1.6 秒；在 Raspberry Pi 5 上，tts.piper 比 tts.openai 多約 3–4 秒延遲。"
key_points:
  - "新 assistant.microwakeword 基於 pymicro-wakeword，內建 okay_nabu、hey_jarvis、hey_mycroft、alexa，API 與 openwakeword 相同，可直接切換"
  - "音訊前處理加入 VAD 門檻滯後與 0.5 秒多數決；噪音底線以 noise_floor_factor（預設 2.0，約 6 dB）過濾，單一噪音突發不再延長對話"
  - "Silero VAD 為主要後端（透過 onnxruntime，不需 PyTorch），WebRTC VAD 與能量偵測為備援；原文稱預設值是在合成音訊與作者少量錄音上調整的"
tags: [voice-assistant, wake-word, voice-activity-detection, raspberry-pi, local-first]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Rebuilding my local voice assistant pipeline

改用更抗噪的喚醒詞與語音端點偵測，讓本地語音助理結束對話更即時。

**Why** 作者自架語音助理誤喚醒與漏喚醒率高，且在噪音環境與廉價麥克風下，語音起訖判斷不穩。

**How** 以基於 microWakeWord 的新 plugin 取代 openWakeWord，並在共用音訊前處理層加入滯後門檻、0.5 秒多數決平滑與自適應噪音底線。

**What** 在作者的合成測試集（Piper 語音混合雜訊）中，對話結束時間從語音結束後 6–10 秒縮短至 1.0–1.6 秒；在 Raspberry Pi 5 上，tts.piper 比 tts.openai 多約 3–4 秒延遲。

### 重點
- 新 assistant.microwakeword 基於 pymicro-wakeword，內建 okay_nabu、hey_jarvis、hey_mycroft、alexa，API 與 openwakeword 相同，可直接切換
- 音訊前處理加入 VAD 門檻滯後與 0.5 秒多數決；噪音底線以 noise_floor_factor（預設 2.0，約 6 dB）過濾，單一噪音突發不再延長對話
- Silero VAD 為主要後端（透過 onnxruntime，不需 PyTorch），WebRTC VAD 與能量偵測為備援；原文稱預設值是在合成音訊與作者少量錄音上調整的

**原文：** [lobsters-ai](https://blog.platypush.tech/article/Rewriting-my-voice-assistant-pipeline)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Rebuilding my voice assistant pipeline https://blog.platypush.tech/article/Rewriting-my-voice-assistant-pipeline 

Rebuilding my local voice assistant pipeline

Wake word detection: a new assistant.microwakeword plugin

Speech-to-text: assistant.openai , with a much better ear

Responses and context: the openai plugin

Text-to-speech: tts.openai

The full configuration

What changed on the code side

Caveats

Reactions

Swapping openwakeword for microwakeword and making voice detection smarter

I wrote an article a couple of months ago describing how I rebuilt my old voice assistant pipeline in Platypush .

And I wrote earlier articles describing my journey through self-hosted voice assistants - in 2024 (with Picovoice ), in 2020 (diving into the legacy assistant.google integration, the now defunct assistant.alexa integration, the now defunct Snowboy integration, the now defunct DeepSpeech integration and Picovoice) and the original article in 2019 describing the Google Assistant integration.

For a couple of months I used the voice pipeline described in my latest article as my main driver, but after getting used to the robustness of commercial voice assistants I was unhappy with the high rates of false positives/negatives of my self-hosted pipeline, as well as its lack of robustness in detecting start/end of speech, especially in noisy environments and using cheap microphones.

After a bit of experimentation, I decided to swap and fine tune a few parts, and after a couple of days of trying the results are satisfying enough for me to write a short article about it.

The resulting pipeline is:

Until recently I used assistant.openwakeword , which wraps openWakeWord .

It works, but the project has been quiet for a while and all of its pre-trained models are v0.1 files from 2023, mostly trained on synthetic speech.

In practice I was getting both false positives (the hotword triggering on background noise) and false negatives (the hotword not detected unless I was close to the microphone).

I added a new plugin, assistant.microwakeword , on top of microWakeWord through the pymicro-wakeword Python bindings.

microWakeWord is the engine used by ESPHome and Home Assistant Voice, its models are actively maintained, and the built-in models ( okay_nabu , hey_jarvis , hey_mycroft , alexa ) ship with the package — no download required.

The current official models are provided under the ESPHome micro-wake-word-models repository .

Custom models are supported too: drop a microWakeWord JSON manifest (with its .tflite model) in the plugin's models directory and reference it by name.

The plugin exposes the same API as assistant.openwakeword (same models , detection_threshold , frame_duration , patience_frames , input_device , input_volume parameters, same list_models action, same HotwordDetectedEvent ), so switching is a matter of just changing the configuration to point to the new plugin:

A few design notes:

assistant.openai records audio when a conversation starts and transcribes it through Whisper.

The tricky part has always been end-of-speech detection : knowing when the user has finished talking. The previous implementation used a per-frame boolean from WebRTC VAD, and any single frame classified as speech would reset the silence timer. With even a bit of background noise, phrases would only end when the maximum conversation duration was hit.

The audio preprocessing layer ( AudioPreprocessor , shared by the STT integrations) has been reworked:

Hysteresis + sliding window : a frame becomes speech above the VAD threshold and stays speech until its score drops by a margin, and the per-frame decisions are smoothed by majority vote over a 0.5s window. A single noise burst can no longer keep a conversation alive.

Adaptive noise floor : the background noise level is tracked over time, and frames that aren't louder than noise_floor_factor (default 2.0, ~6 dB) times the floor are never considered as speech.

On a synthetic benchmark (Piper-generated phrases mixed with babble and burst noise), the old settings kept conversations open for 6–10 seconds after the speech had ended; the new pipeline ends them 1.0–1.6 seconds after the last word, which is the configured conversation_end_timeout plus the smoothing lag.

Since the changes on Platypush have been performed directly in the AudioPreprocessor also used by other native speech-to-text engines, other speech-to-text plugins also benefit from them - e.g. if you use assistant.vosk for full on-device detection.

The transcribed phrase is processed by the openai plugin, which handles both the API key and the conversation context. By default the assistant renders the response through the configured tts_plugin ; if the response ends with a question mark, the conversation continues with a follow-up.

Custom hooks can intercept phrases before the default response kicks in — for example, to handle home automation commands locally without an LLM round-trip:

And the hotword event is wired to the conversation start with a similar hook:

Responses are rendered by tts.openai , with volume and voice configurable. In my tests however tts.piper also yielded good results, and it runs entirely locally. In my tests on a RaspberryPi 5 however it added ~3-4s of latency to process the response to audio compared to tts.openai .

Since the TTS output goes to the speakers and the wake word detector listens on the microphone, the assistant plugins pause hotword detection while a conversation is active — otherwise the assistant would hear itself.

The microphone on my RPi doesn't support 16 kHz natively, so audio is captured at 44.1 kHz and software-resampled — it works, but if detection feels sluggish software resampling is usually the first suspect.

The VAD and threshold defaults were tuned on synthetic audio plus a couple of my audio recordings.

Different rooms, microphones and acoustics may yield different results. You may want to adjust detection_threshold on the wake word plugin and noise_floor_factor on the STT plugins if you don't feel satisfied with your mileage.

To interact via Webmentions ,
 send an activity that references this URL from a platform that supports Webmentions,
 such as Lemmy , WordPress with Webmention plugins ,
 or any IndieWeb-compatible site .

https://blog.platypush.tech/article/Rewriting-my-voice-assistant-pipeline

It's 2026. You deserve a good local-first or local-only voice assistant on your #RaspberryPi

#platypush

blog.platypush.tech/article/Rewriting-my-voice-assistant-pipeline

Wake word detection: a new assistant.microwakeword plugin

Speech-to-text: assistant.openai, with a much better ear

Responses and context: the openai plugin

Text-to-speech: tts.openai

The full configuration

What changed on the code side

Caveats

Without an explicit detection_threshold , each model uses the probability_cutoff from its own manifest (0.9 for alexa ), which is the value the model was validated against.

Models already smooth their output over a sliding window, so unlike openwakeword, patience_frames defaults to 0 here.

The audio thread never touches the TFLite models directly: it queues frames (and a reset marker) to the main thread, because MicroWakeWord.reset() reloads the interpreter and isn't safe to call concurrently.

Like assistant.openwakeword , the plugin releases the audio device when another assistant plugin starts a conversation, and re-acquires it when the conversation ends.

Silero VAD as the primary backend (through onnxruntime , no PyTorch required), with WebRTC VAD and a plain RMS-based detector as fallbacks. To get an idea of Silero VAD's performance compared against other solutions for speech activity detection, take a look at the insightful article One voice detector to rule them all . The Silero model is downloaded on first use into the Platypush workdir and checksum-verified:

 Hysteresis + sliding window : a frame becomes speech above the VAD threshold and stays speech until its score drops by a margin, and the per-frame decisions are smoothed by majority vote over a 0.5s window. A single noise burst can no longer keep a conversation alive. 

 Adaptive noise floor : the background noise level is tracked over time, and frames that aren't louder than noise_floor_factor (default 2.0, ~6 dB) times the floor are never considered as speech. 

New assistant.microwakeword plugin : microWakeWord hotword detection through pymicro-wakeword , same API as assistant.openwakeword , built-in models bundled with the package, custom models via JSON manifests.

assistant.openwakeword fixes : frames are now 80ms (1280 samples, the size openWakeWord recommends) instead of 500ms — longer chunks only return the highest score over their sub-frames and can miss hotwords — plus a patience_frames parameter (consecutive frames above threshold) and an explicit detection_threshold parameter (default 0.5).

Shared AudioPreprocessor rework : Silero/WebRTC/energy VAD backends with vad_backend: auto selection, threshold hysteresis, sliding-window majority vote, and an adaptive noise floor. Used by both assistant.openai and assistant.vosk .

New Silero VAD wrapper : ONNX inference through onnxruntime , recurrent state carried across frames, checksum-verified model download into the workdir.

Follow @blog@platypush.tech on your ActivityPub platform (e.g. Mastodon, Misskey, Pleroma, Lemmy).

Mention @blog@platypush.tech in a post to feature on the Guestbook .

Search for this URL on your instance to find and interact with the post.

Like, boost, quote, or reply to the post to feature your activity here.

assistant.microwakeword : models : - alexa 

assistant.openai : # auto = silero -> webrtc -> energy, depending on what's installed vad_backend : auto 

from platypush import run , when from platypush.message.event.assistant import SpeechRecognizedEvent @when ( SpeechRecognizedEvent , phrase = 'play (the)? music' ) def play_music (): run ( 'music.mpd.play' ) 

from platypush import run , when from platypush.message.event.assistant import HotwordDetectedEvent @when ( HotwordDetectedEvent ) def on_hotword ( ** _ ): run ( 'assistant.openai.start_conversation' ) 

openai : api_key : YOUR_API_KEY # Or, for a custom setup using a model provider compatible with the OpenAI API, # e.g. a local Ollama instance: # base_url: http://localhost:8000/v1 # model: gpt-5 # Optional context that can be passed to initialize the assistant # context: # role: system # content: You are a useful assistant. assistant.microwakeword : models : - alexa assistant.openai : tts_plugin : tts.openai conversation_start_sound : ~/sounds/wake_word_detected.wav input_volume : 100 # assistant.vosk: # model: /path/to/vosk/model # conversation_start_sound: ~/sounds/wake_word_detected.wav # input_volume: 100 tts.openai : output_volume : 80.0 # Or, for a fully local setup that uses tts.piper: # tts.piper: # output_volume: 80.0

</details>