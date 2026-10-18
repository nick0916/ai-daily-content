---
id: inbox_affb832b
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Oct/17/document-currentscript/"
author: ""
published_at: 2026-10-17T21:11:12+00:00
fetched_at: 2026-10-18T02:56:33.587054+00:00
content_hash: "5e6c985de66c904423e837e4de8a06e0eed768c7769cadd6ae110793c6804583"
lang: en
caption_quality: None
raw: true
topics: []
---

# Inline rendering with document.currentScript

Inline rendering with document.currentScript 
Lean Rada describes a neat trick that takes advantage of the document.currentScript property. You can use that to drop in a tiny inline &lt;script&gt; element that replaces itself when the page loads: 
 The year is &lt;script&gt;
document.currentScript.replaceWith(
 new Date().getFullYear())&lt;/script&gt;
 
 If you define a shortcut function like this: 
 $=(...n)=&gt;document.currentScript.replaceWith(...n)
 
 You get a tiny template language: 
 The year is &lt;script&gt;$(new Date().getFullYear())&lt;/script&gt;
 

 Tags: javascript