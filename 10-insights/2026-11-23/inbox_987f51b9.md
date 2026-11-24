---
id: inbox_987f51b9
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-infoq-main-jep-545-moves-zgc-memory-preparation-off-bedd]]"
title: "JEP 545 Moves ZGC Memory Preparation off the Startup Path in JDK 28"
url: https://www.infoq.com/news/2026/11/jep-545-jdk-28/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-23T15:30:00+00:00
fetched_at: 2026-11-24T02:15:52.712450+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Java 的 ZGC 垃圾回收器啟動更快、暖機更快，把準備記憶體的工作移到背景執行緒。 **Why** JVM 啟動與暖機階段需要準備堆積記憶體，這部分拖慢了啟動路徑。 **How** 由並行 worker threads 負責準備 heap 記憶體，ZGC 在擴張時預先 touch 記憶體，並在 Linux 6.1 以上將小頁升級為大頁。 **What** JEP 545（Faster Startup and Warmup with ZGC）已整合進 JDK 28。其 38% 啟動與 90% 暖機改善，需搭配 2 MB 初始堆積與 JEP 546 的 adaptive heap sizing 旗標，該旗標預設關閉。"
key_points:
  - "JEP 545 整合進 JDK 28，heap 記憶體準備移至並行 worker threads"
  - "Linux 6.1 以上會將小頁升級為大頁"
  - "38% 啟動與 90% 暖機提升需 2 MB 初始堆積，且要開啟預設關閉的 JEP 546 adaptive heap sizing 旗標"
tags: [java, jdk-28, zgc, jvm, startup-performance]
topics: [engineering.inference]
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## JEP 545 Moves ZGC Memory Preparation off the Startup Path in JDK 28

讓 Java 的 ZGC 垃圾回收器啟動更快、暖機更快，把準備記憶體的工作移到背景執行緒。

**Why** JVM 啟動與暖機階段需要準備堆積記憶體，這部分拖慢了啟動路徑。

**How** 由並行 worker threads 負責準備 heap 記憶體，ZGC 在擴張時預先 touch 記憶體，並在 Linux 6.1 以上將小頁升級為大頁。

**What** JEP 545（Faster Startup and Warmup with ZGC）已整合進 JDK 28。其 38% 啟動與 90% 暖機改善，需搭配 2 MB 初始堆積與 JEP 546 的 adaptive heap sizing 旗標，該旗標預設關閉。

### 重點
- JEP 545 整合進 JDK 28，heap 記憶體準備移至並行 worker threads
- Linux 6.1 以上會將小頁升級為大頁
- 38% 啟動與 90% 暖機提升需 2 MB 初始堆積，且要開啟預設關閉的 JEP 546 adaptive heap sizing 旗標

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/jep-545-jdk-28/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

JEP 545, Faster Startup and Warmup with ZGC, has been integrated into JDK 28, moving heap memory preparation onto concurrent worker threads. ZGC now pre-touches memory as it expands and upgrades small pages to large ones on Linux 6.1 and later, but the 2 MB initial heap behind the JEP's 38% startup and 90% warmup gains requires the adaptive heap sizing flag from JEP 546, which is off by default. By A N M Bazlur Rahman

</details>