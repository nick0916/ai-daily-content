---
id: inbox_dffcf286
date: 2026-11-21
source_ref: "[[00-inbox/2026-11-21/0239-lobsters-ai-researcher-plants-2m-canaries-into-the-a-9001]]"
title: "Researcher plants 2m canaries into the AI supply chain. A privacy disaster surfaced"
url: https://arstechnica.com/security/2026/11/a-leaky-ai-supply-chain-is-exposing-secret-user-data-at-an-alarming-rate/
source: lobsters-ai
published_at: 2026-11-21T20:03:46-06:00
fetched_at: 2026-11-22T02:46:23.421261+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "研究者在 AI 服務鏈中埋下約兩百萬組追蹤用誘餌憑證，發現敏感資料大量外洩。 **Why** AI 路由器與轉售商會在每一跳解密 prompt 並可能記錄，使敏感資訊暴露在多方之下。 **How** HD Moore 把獨特的 AWS 金鑰、SSH 密碼與 URL 各只放進一個 prompt 送往單一供應商，再追蹤它們在何處出現。 **What** 三家託管供應商遭入侵，被盜金鑰在 AWS API 中被使用「數萬次」；某中國 AI 實驗室的爬蟲抓取超過一半 prompt 中的秘密 URL，其中約三分之二標註 ZDR 或「不收集資料」。OpenRouter 回應後已移除 MiniMax 端點的 ZDR 標籤。"
key_points:
  - "三家託管供應商遭入侵，攻擊者重用約「數百」組被盜的 AWS 金鑰，在 AWS API 中共被使用「數萬次」"
  - "某中國 AI 實驗室的爬蟲抓取超過一半 prompt 中的秘密 URL，含約三分之二標註 ZDR 或「不收集資料」的請求"
  - "研究者建議選第一線供應商、避免使用預設的 reseller pool；ZDR 旗標在攻擊者已進入系統時無法防護"
tags: [ai-security, data-privacy, ai-gateway, prompt-leakage, supply-chain]
topics: [security, engineering.inference]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Researcher plants 2m canaries into the AI supply chain. A privacy disaster surfaced

研究者在 AI 服務鏈中埋下約兩百萬組追蹤用誘餌憑證，發現敏感資料大量外洩。

**Why** AI 路由器與轉售商會在每一跳解密 prompt 並可能記錄，使敏感資訊暴露在多方之下。

**How** HD Moore 把獨特的 AWS 金鑰、SSH 密碼與 URL 各只放進一個 prompt 送往單一供應商，再追蹤它們在何處出現。

**What** 三家託管供應商遭入侵，被盜金鑰在 AWS API 中被使用「數萬次」；某中國 AI 實驗室的爬蟲抓取超過一半 prompt 中的秘密 URL，其中約三分之二標註 ZDR 或「不收集資料」。OpenRouter 回應後已移除 MiniMax 端點的 ZDR 標籤。

### 重點
- 三家託管供應商遭入侵，攻擊者重用約「數百」組被盜的 AWS 金鑰，在 AWS API 中共被使用「數萬次」
- 某中國 AI 實驗室的爬蟲抓取超過一半 prompt 中的秘密 URL，含約三分之二標註 ZDR 或「不收集資料」的請求
- 研究者建議選第一線供應商、避免使用預設的 reseller pool；ZDR 旗標在攻擊者已進入系統時無法防護

**原文：** [lobsters-ai](https://arstechnica.com/security/2026/11/a-leaky-ai-supply-chain-is-exposing-secret-user-data-at-an-alarming-rate/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Security breaches, prompt theft, and privacy violations

The Wild West in the age of AI

Researchers planted 2 million digital tripwires in requests sent through a sprawling network of AI services to find out what happened to sensitive information entrusted to them. What they discovered was an ecosystem that leaked highly sensitive data like a sieve.

The exposure was found through an ingenious experiment designed to test if sensitive information can leak through the vast chain of widely used AI services and how that information is exploited when it does. Many of today’s AI apps use services such as OpenRouter or Vercel that act as brokers. These “AI routers,” sometimes also known as “AI gateways,” receive large numbers of prompts sent from AI app end users and route them to an available inference engine based on criteria such as the one charging the lowest price or being best suited for the given task. Instead of using Anthropic, OpenAI, or another big provider, the developer hires an AI router to find the most suitable model.

Update, Nov 21: Posts on both Hacker News and X report that OpenRouter has sent customers an email notifying them that some of their prompts may have been read. OpenRouter cited the research and said that it received a report that the potential exposure involved prompts sent to MiniMax, a China-based model provider. OpenRouter said the researchers’ planted URLs were accessed whether the prompts were sent to MiniMax directly or through three other resellers: AtlasCloud, Novita, and StreamLake. OpenRouter has removed a “Zero Data Retention” label from MiniMax-model endpoints. Hat tip: Sulat.com .

To test for potential leakage, researcher HD Moore assembled a collection of Amazon Web Services access keys, functioning credentials tied to empty AWS accounts, passwords for services such as SSH, and unique URLs, DNS names, and private git repository references. None of the secrets had ever been used before, and he controlled the infrastructure that received any requests using the credentials. He then seeded each secret into exactly one prompt sent to a single provider. In the event any of the secrets were leaked, these “canaries”—so called because they resemble the role of that bird when taken into coal mines—would allow Moore to identify each link in the chain that was responsible.

The findings are striking. They included:

“We sent nearly two million AI prompts containing unique, trackable secrets to AI providers, then watched where those secrets surfaced,” Moore, the chief research officer of security firm Dragos, wrote Thursday . “What we found revealed security breaches, prompt theft, and widespread failures to protect customer data.”

Although prompts are encrypted in transit, they are decrypted at each hop inside the large inference reseller network. The prompt is first sent to an AI router, which reads the plaintext in it to determine the most suitable inference providers to handle the request. Often, the prompt is then sent to a pool of available models, which sometimes run inside different hosting providers. Prompts can also pass from one AI router (such as Vercel) to another one (e.g., OpenRouter). Each one of these players is likely to log the prompt and store it for as long as its policies call for (if not indefinitely).

The most concerning finding was the breach of three separate hosting providers. The attackers who compromised one of the providers reused “a couple hundred” of the AWS keys. Moore wrote:

Each key was sent in exactly one request to one provider, all within a few short windows in late October, and every request we sent during those windows was stolen. Some of the stolen keys came from requests that the provider rejected before a model ever ran—this tells us that the attacker was copying requests at the provider’s front door, and not somewhere deeper in the inference stack. In the other two breaches, some of the stolen requests were marked as ZDR. A privacy flag doesn’t help when the attacker is already inside.

Parties tied to the hack of these three providers then tested each key, in some cases within hours of being seeded, to see what kind of resources it gave access to. The parties looked through S3 buckets, secrets managers, and parameter stores in search of still more credentials. They also tried to enable hosted models in AWS Bedrock and added their own IAM users to maintain access. In all, the stolen bait keys were used “tens of thousands” of times in AWS API calls.

Secrets sent to two of the hacked providers were quickly used together, almost immediately, from the same rented server. That means the providers were almost certainly compromised by the same adversary.

As noted earlier, some of the secrets were stolen by the resellers themselves. To lure prompts to their servers, they offered low prices. Then they turned on request logging and waited. Moore identified them by sending requests to the same model through different sellers. When credentials were later reused when sent through one seller and not another, the researcher knew it was the reseller, not the model provider, that was responsible.

Last, the canary experiment revealed that some providers are scraping secret URLs put into the prompts, in violation of privacy terms. Moore wrote:

The clearest example involves a Chinese AI lab. This lab’s systems fetched the secret URLs from more than half of the prompts that we sent to its models between July and October, including roughly two-thirds of the requests marked as “no data collection” or Zero Data Retention. The scraper typically showed up two or three days after the request.

This wasn’t limited to requests sent to the lab directly. Several US hosting providers resell this lab’s models, and prompts sent to those providers triggered the exact same scraper—the prompts were flowing back to the lab. A customer who picked a US provider specifically to keep their data in the U.S. didn’t get what they paid for. Later on, a git client on a different cloud started trying to clone the private repositories referenced in our prompts, but only for prompts that used this lab’s models.

The researcher said he found one US hosting provider crawling a secret URL more than two months after it was used in a single inference call to its search endpoint. Another ran a scraper that came back for URLs days after each request, regardless of the AI router used to reach it.

Moore said that the most effective means for preventing leakage is to host models using on-premises servers. That option is expensive, though. For those who can’t afford a self-hosted system, the next best option, Moore said, is to receive service directly from a first-tier provider that provides “one contract and a privacy policy to read.” Moore said that even then, there’s no guarantee no data will leak, but that the measure minimizes the chances. AI users should also avoid accepting default provider or reseller pools and instead pick upstream providers themselves.

The blockbuster research is the latest indictment exposing the lax privacy and security that’s endemic in much of the AI ecosystem. The findings mean that people who want to ensure secrets they put into prompts stay private face a daunting task that isn’t likely to become easier any time soon.

Evidence that at least three AI providers were compromised by attackers who used their access to siphon prompts they received

Multiple resellers in the inference marketplace that logged the prompts and somehow passed them along to people who used the credentials

Multiple cases of AI providers not following end-user privacy settings embedded into flags specifying terms such as Zero Data Retention (ZDR) or “no data collection”

</details>