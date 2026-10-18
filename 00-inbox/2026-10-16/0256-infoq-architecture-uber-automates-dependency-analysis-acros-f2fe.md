---
id: inbox_ad18599b
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/10/uber-automated-dependency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Leela Kumili"
published_at: 2026-10-16T14:39:00+00:00
fetched_at: 2026-10-18T02:56:45.374489+00:00
content_hash: "f2fe4f780a7e25eb76bbae9b356ad250c628390b5243fd0821ba5d192793a4dc"
lang: en
caption_quality: None
raw: true
topics: []
---

# Uber Automates Dependency Analysis Across Its Service Mesh

Uber has developed an automated dependency analysis system that uses RPC middleware and production metrics to correlate caller and downstream failures. The approach classifies dependencies as fail-close, fail-open, or unknown and addresses limitations of sampled distributed tracing for rare failures across Uber’s large service mesh. By Leela Kumili