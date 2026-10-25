---
id: inbox_b4257d70
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0102-lobsters-vibecoding-introducing-portal-a86e]]"
title: "Introducing Portal"
url: https://unclex.net/writing/portal
source: lobsters-vibecoding
published_at: 2026-10-15T07:21:11-05:00
fetched_at: 2026-10-25T01:29:34.900929+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Emacs 直接嵌入 macOS 原生網頁與 Ghostty 終端機，不必在多個 app 間切換。 **Why** Emacs 內建的 xwidget-webkit 在 macOS 上效果不佳，而作者在 Emacs 內畫草圖、看 Markdown 與 HTML、跑 coding agent。 **How** 以動態模組把 WKWebView 放進 Emacs pane，view 跟隨所屬 buffer；另附 Bun 後端服務網頁應用，並把 Ghostty renderer 作為原生 view 嵌入。 **What** Excalidraw 可離線使用，Markdown 以渲染頁面顯示（含目錄與 Open in Emacs 按鈕），HTML mockup 可直接在 Emacs 內預覽。作者表示已數週未開獨立 Ghostty。已知問題是外接螢幕插拔會觸發 Ghostty renderer deadlock（ghostty#14427），並連帶讓 Emacs 凍結，上游近期有修正。專案僅支援 macOS 並已開源。"
key_points:
  - "以 macOS WKWebView 作為 Emacs buffer 內的原生 view，附 Bun 後端服務 Excalidraw 離線運作"
  - "Agent 產出的 Markdown 表格與 HTML mockup 在 Emacs 內直接渲染，作者稱 Markdown 表格在 Emacs 中不好看"
  - "Ghostty renderer 嵌入 Emacs 後，外接螢幕插拔會觸發 deadlock（ghostty#14427），作者以 tmux 或 herdr 保護 session"
tags: [emacs, macos, webkit, ghostty, agentic-coding]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Introducing Portal

讓 Emacs 直接嵌入 macOS 原生網頁與 Ghostty 終端機，不必在多個 app 間切換。 **Why** Emacs 內建的 xwidget-webkit 在 macOS 上效果不佳，而作者在 Emacs 內畫草圖、看 Markdown 與 HTML、跑 coding agent。 **How** 以動態模組把 WKWebView 放進 Emacs pane，view 跟隨所屬 buffer；另附 Bun 後端服務網頁應用，並把 Ghostty renderer 作為原生 view 嵌入。 **What** Excalidraw 可離線使用，Markdown 以渲染頁面顯示（含目錄與 Open in Emacs 按鈕），HTML mockup 可直接在 Emacs 內預覽。作者表示已數週未開獨立 Ghostty。已知問題是外接螢幕插拔會觸發 Ghostty renderer deadlock（ghostty#14427），並連帶讓 Emacs 凍結，上游近期有修正。專案僅支援 macOS 並已開源。

### 重點
- 以 macOS WKWebView 作為 Emacs buffer 內的原生 view，附 Bun 後端服務 Excalidraw 離線運作
- Agent 產出的 Markdown 表格與 HTML mockup 在 Emacs 內直接渲染，作者稱 Markdown 表格在 Emacs 中不好看
- Ghostty renderer 嵌入 Emacs 後，外接螢幕插拔會觸發 deadlock（ghostty#14427），作者以 tmux 或 herdr 保護 session

**原文：** [lobsters-vibecoding](https://unclex.net/writing/portal)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A web view first

Previews

Then the terminal

Daily driving it

The catch

It started with a drawing. I wanted to sketch something quickly in Excalidraw , and I didn't want to switch to the browser every time I do that. I want to stay inside Emacs. That's the whole point of everything I've been doing lately. 

Emacs does have an answer for this: xwidget-webkit, a web view embedded in a buffer. On macOS, it doesn't work very well. So, same as last time : screw it, I will make it myself. 

The first piece was a dynamic module that puts the native macOS web view (WKWebView) inside an Emacs pane. It's fast, it's the same engine Safari uses. The view belongs to a buffer and follows it around: splits, resizes, other frames. Hide the buffer and the page keeps running in the background. 

A web view alone only shows URLs, though. So I bundled a small Bun server as a backend that serves web apps to those views. Excalidraw runs offline now, and once that was in place it was clear any web UI could live inside Emacs. That was the moment it stopped being an Excalidraw hack. 

Once there's a web view in Emacs, previews come almost for free. Two of them turned out to be really useful: Markdown and HTML. Both are because of agentic coding. 

Agents write a lot of Markdown files, and they love tables. Tables look ugly in Emacs. I tried all kinds of Markdown modes, and none of them beats a plain web view. So now a Markdown file opens as a rendered page, served by the Bun backend, with a table of contents and an Open in Emacs button when I want the source. 

HTML is the other one. When I ask an agent for a mockup, I get a single HTML file with everything inlined. Before, that meant opening it in the browser. Now I preview it right in Emacs, next to the code, and most of the time the mockup is even interactive. Very nice. 

My day looks like this: Ghostty is where I run coding agents, Emacs is where I do version control, code review and some light editing. Two apps, and I switch between them constantly. It's annoying. 

The obvious fix is a terminal inside Emacs, and I've tried them. They are all a bit sluggish, even the fast one I was using before Portal, which is built on Ghostty's terminal engine. The parsing is fast, but every frame still gets drawn through the Emacs UI, and you can feel it. 

So I thought, maybe I should just render Ghostty in Emacs directly, as a native view, the same way as the web view. So I did. It's the real Ghostty renderer, sitting in an Emacs pane, and the buffer around it is still a normal Emacs buffer. I can split it, switch to it with consult-buffer , give each project its own terminals, and pull up a quick scratch terminal at the bottom of the frame. I was very happy. 

I've been using the Portal terminal as my daily driver since. It works perfectly, and I haven't opened Ghostty as a separate app for weeks. 

There was one rough patch. My MacBook is connected to a dock with two 4K monitors, and every now and then, after I unplugged it from the dock, the terminal would freeze, which takes down emacs as well. It turned out to be a bug in Ghostty itself, not in Portal: the renderer deadlocks when an external display is disconnected or reconnected ( ghostty#14427 , a follow-up to the sleep/wake variant in ghostty#14150 ). The standalone Ghostty app hits the same freeze. A fix landed upstream recently, and since the last update I haven't seen it. 

Still, the terminal runs inside the Emacs process, so a frozen terminal can take Emacs down with it. To be cautious, I run a multiplexer like tmux or herdr inside the terminal. If anything goes wrong, the sessions survive and nothing is lost. 

It's macOS only, by design. It needs a graphical Emacs with dynamic modules, and the module runs inside the Emacs process, so a bug in it can take Emacs down with it. 

It's open source now. How to install it, and what you can build on it, is on the project page . 

A portal from Emacs to the rest of the computer: native macOS views inside Emacs panes.

← All writing

</details>