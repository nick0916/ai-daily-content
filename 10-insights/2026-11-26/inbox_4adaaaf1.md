---
id: inbox_4adaaaf1
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0146-hackernews-show-hn-i-wrote-an-entire-vim-manual-ove-f7d5]]"
title: "Show HN: I wrote an entire Vim manual over 4 years"
url: http://themouseless.dev/vim/
source: hackernews
published_at: 2026-11-26T14:44:22+00:00
fetched_at: 2026-11-28T01:51:16.550268+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位作者花四年寫完一本循序漸進的 Vim 教學書，並聲明未使用 LLM。 **Why** 作者覺得 vimtutor 太濃縮難記，官方 `:help manual` 在部分章節過細、其他功能又著墨不足。 **How** 作者自己從基礎到進階逐步編寫，多數設定同時提供 Vimscript 與 Lua（Neovim）寫法，只涵蓋 Vim 與 Neovim 共通功能。 **What** 《Learning to Play Vim》耗時超過 4 年、2987 個番茄鐘（1244 小時），共 21 章、170 題附解答的練習，並有實例與相關 Vim help 頁面；官網提供含目錄與前三章的試讀。"
key_points:
  - "21 章、170 個附解答的練習，耗時 4 年以上、2987 個番茄鐘（1244 小時）"
  - "多數設定同時提供 Vimscript 與 Lua 版本，僅涵蓋 Vim 與 Neovim 共通功能（不含 treesitter、LSP）"
  - "作者聲明全程未使用 LLM 撰寫"
tags: [vim, show-hn, book, neovim, learning-resource]
topics: [product_and_org.product]
importance: 1
novelty: 1
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: I wrote an entire Vim manual over 4 years

一位作者花四年寫完一本循序漸進的 Vim 教學書，並聲明未使用 LLM。

**Why** 作者覺得 vimtutor 太濃縮難記，官方 `:help manual` 在部分章節過細、其他功能又著墨不足。

**How** 作者自己從基礎到進階逐步編寫，多數設定同時提供 Vimscript 與 Lua（Neovim）寫法，只涵蓋 Vim 與 Neovim 共通功能。

**What** 《Learning to Play Vim》耗時超過 4 年、2987 個番茄鐘（1244 小時），共 21 章、170 題附解答的練習，並有實例與相關 Vim help 頁面；官網提供含目錄與前三章的試讀。

### 重點
- 21 章、170 個附解答的練習，耗時 4 年以上、2987 個番茄鐘（1244 小時）
- 多數設定同時提供 Vimscript 與 Lua 版本，僅涵蓋 Vim 與 Neovim 共通功能（不含 treesitter、LSP）
- 作者聲明全程未使用 LLM 撰寫

**原文：** [hackernews](http://themouseless.dev/vim/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I'm glad to announce that I'm releasing my new book, Learning to Play Vim. When I started using Vim more than a decade ago, I wished there was a manual out there teaching how to use this fantastic editor step by step, beginning with the foundations up to more advanced features. Of course at the time I did the vimtutor, but it was too dense for me to remember much from it. I also read the entire Vim manual (`:help manual`), but I didn't like it: it was too detailed in places (for example `02.8 Finding help` completely lost me for a while), and other features didn't get the treatment they deserved. So I decided to write my own Vim manual. It took me more than 4 years and 2987 focused pomodoros (1244 hours) of work to finally get it done! The result: - 21 chapters showing the most important Vim features step by step. - 170 exercises with solutions. - Many real-life examples to show how Vim can be used and configured for your own needs. - The related Vim's help pages to dig further into each feature. Most configs are both written in Vimscript and Lua for Neovim users. This book explores the common features between Vim and Neovim, so don't expect anything about Neovim-specific features (like treesitter or LSP for example). - The landing page: https://themouseless.dev/vim/ - A sample of the book with the entire table of contents and the first three chapters covering most of the basics: https://themouseless.dev/content/learning_to_play_vim_sample... . I wrote this with my bare hands, no LLM involved to spoil the fun.

</details>