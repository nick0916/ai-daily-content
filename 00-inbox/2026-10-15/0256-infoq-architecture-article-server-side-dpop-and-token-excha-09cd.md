---
id: inbox_54b14f7e
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/articles/spring-security-7-server-side-dpop-token-exchange/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Dhruv Agnihotri"
published_at: 2026-10-15T09:00:00+00:00
fetched_at: 2026-10-18T02:56:45.377770+00:00
content_hash: "09cd851d79fa70b1212fd3daee2f47f844b866cb32753d80f7a941cf6fd50e85"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Server-Side DPoP and Token Exchange in Spring Security 7

Spring Authorization Server now lives inside Spring Security 7 under the same Maven coordinates, so the upgrade is a version bump. This server-side guide covers enabling DPoP and RFC 8693 Token Exchange, explains why 7.1 apps can silently stop enforcing DPoP until they call .dPoP(), and shows how to combine both into narrowed, sender-constrained tokens for service-to-service and agentic calls. By Dhruv Agnihotri