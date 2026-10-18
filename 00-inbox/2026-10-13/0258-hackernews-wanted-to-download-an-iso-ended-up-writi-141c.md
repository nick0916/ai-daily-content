---
id: inbox_7b9fdcb6
source: hackernews
source_type: hn
url: "https://blog.dfb.sh/blog/eap770-root-for-two-zeros/"
author: "0xdeafbeef"
published_at: 2026-10-13T12:30:08+00:00
fetched_at: 2026-10-18T02:58:33.569943+00:00
content_hash: "141cfb2278b741d4f520ab88d976d20f3cbdfe6e5a801b9ccebe30ca87af59cf"
lang: en
caption_quality: None
raw: true
topics: []
---

# Wanted to download an ISO, ended up writing a kernel exploit

Author here. Does anyone know what to do with the rest of the drivers? I found at least 13 in-tree drivers with the same bug class. The nasty part is they work fine on x86 and silently corrupt data on arm and other non-coherent archs, and I don&#x27;t have the hardware to test them. I&#x27;d guess that&#x27;s what the DMA API is for and drivers shouldn&#x27;t be doing cache maintenance by hand, but I&#x27;m not a kernel dev, so maybe I&#x27;m missing something.