---
id: inbox_b08a7741
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0018-creator-economy-the-internet-is-being-hacked-6-steps-to-a7f0]]"
title: "The Internet Is Being Hacked. 6 Steps to Secure Your Accounts Now"
url: https://creatoreconomy.so/p/the-internet-is-being-hacked-6-steps-to-secure-your-accounts
source: creator-economy
published_at: 2026-10-28T13:03:52+00:00
fetched_at: 2026-10-29T00:26:41.637161+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 已能比人更快找到軟體漏洞，因此個人應立即盤點並加固帳號安全，文中提供六個步驟。 **Why** 作者列出近一週的資安事件：PHP 關鍵漏洞（NSA 要求修補或離線）、WordPress 遭竊用金鑰植入後門、Quest Diagnostics 病患紀錄遭存取、銀行中出現未授權的 AI agent。 **How** 六步驟為：移除不用的應用程式授權、使用密碼管理器建立獨立密碼、以驗證器 App 取代簡訊驗證、輪替或停用 API key、請 AI 掃描並更新軟體、不信任 breach 相關的緊急郵件或電話。 **What** 作者在 myaccount.google.com/connections 找出 47 個已連結應用，並讓 AI 協助審查與撤銷；AI 也找出 Anthropic Console 中兩個仍有效的舊 key。"
key_points:
  - "Google 帳號連結頁可審查第三方應用授權；作者交由 ChatGPT 與 Claude 建議撤銷清單後再執行"
  - "簡訊 2FA 不夠安全，原因是攻擊者可能說服電信業者轉移號碼；建議改用 Google Authenticator 等驗證器 App"
  - "在 breach 郵件中，以右鍵「複製連結位址」檢查實際網址，不點擊緊急連結"
tags: [account-security, api-keys, two-factor-auth, phishing]
topics: [security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## The Internet Is Being Hacked. 6 Steps to Secure Your Accounts Now

AI 已能比人更快找到軟體漏洞，因此個人應立即盤點並加固帳號安全，文中提供六個步驟。

**Why** 作者列出近一週的資安事件：PHP 關鍵漏洞（NSA 要求修補或離線）、WordPress 遭竊用金鑰植入後門、Quest Diagnostics 病患紀錄遭存取、銀行中出現未授權的 AI agent。

**How** 六步驟為：移除不用的應用程式授權、使用密碼管理器建立獨立密碼、以驗證器 App 取代簡訊驗證、輪替或停用 API key、請 AI 掃描並更新軟體、不信任 breach 相關的緊急郵件或電話。

**What** 作者在 myaccount.google.com/connections 找出 47 個已連結應用，並讓 AI 協助審查與撤銷；AI 也找出 Anthropic Console 中兩個仍有效的舊 key。

### 重點
- Google 帳號連結頁可審查第三方應用授權；作者交由 ChatGPT 與 Claude 建議撤銷清單後再執行
- 簡訊 2FA 不夠安全，原因是攻擊者可能說服電信業者轉移號碼；建議改用 Google Authenticator 等驗證器 App
- 在 breach 郵件中，以右鍵「複製連結位址」檢查實際網址，不點擊緊急連結

**原文：** [creator-economy](https://creatoreconomy.so/p/the-internet-is-being-hacked-6-steps-to-secure-your-accounts)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Upgrade to paid to unlock $600+ in AI tool credits (e.g., Grok Bot), my Personal AI course with 25+ lessons, 17+ AI skills, and an invite to my private Slack community with monthly live workshops. Get instant access Dear subscribers, The internet is being hacked right now, and I want to help you protect yourself. People’s bank accounts, health records, and API keys were all targets last week because AI is finding security holes faster than anyone can patch them. Watch my tutorial to learn how to work with AI to secure your accounts in 6 steps. Timestamps: (00:00) 12 security fires in one week and 6 steps to take now (03:16) One AI prompt that audits all 6 for you (05:11) Step 1: Disconnect apps you don't use (06:55) Step 2: Use a password manager and check Watchtower (09:57) Step 3: Turn on two-factor with an authenticator app (10:48) Step 4: Rotate or retire your API keys (11:50) Step 5: Ask AI to scan and update your software (12:51) Step 6: Don't trust breach emails or calls I’m proud to partner with Granola The world’s best teams, including Ramp, Linear, Replit, Brex, and more, use Granola to take notes and focus more in meetings. I’ve tried many meeting apps myself but keep coming back to Granola. Get 1 month free via my link below. Try Granola for Free Why the internet is being hacked Just this past week, we’ve seen critical security issues in: PHP: The NSA told organizations to patch critical bugs or take systems offline. PHP is used by millions of websites on the internet. WordPress: Attackers used stolen keys to plant backdoors on websites. Quest Diagnostics: Hackers accessed patient records. Banks: Unauthorized AI agents were found inside customer accounts, and JPMorgan, Bank of America, and Wells Fargo are now restricting them. Jason Clinton, Anthropic’s deputy chief security officer, tweeted: This is all happening because AI can now find security vulnerabilities in legacy software that human audits missed for years. So it’s an arms race between attackers looking to exploit these issues and defenders trying to patch them. Personally, what prompted me to act was receiving this critical security alert from Google that said a Linux machine had deleted some emails. The problem is, every agent — from Grok Bot to Muse to ChatGPT Dots — uses Linux machines! Enough is enough 🫠 6 steps to secure your accounts right now I spent two hours securing all of my accounts after receiving the alert above. Here’s my simple 6-step security checklist that you can follow to do the same: Disconnect apps you don't use. Go to myaccount.google.com/connections and remove any apps that shouldn’t have access to your Gmail and Google data. I had 47 apps connected (!) so it would have taken forever to manually remove each one. Instead, I asked ChatGPT and Claude, “On myaccount.google.com/connections , review my connected apps and give me a list of apps you think I should disconnect.” Then I reviewed the list and had AI disconnect them for me. Use a password manager with unique passwords. I was using just a few passwords for all my accounts, which is crazy in hindsight. So I finally decided to stop being cheap and pay ~$48/year for 1Password to set up unique passwords for each website. It has a handy Watchtower page (below) that told me which websites had reused or weak passwords: Turn on two-factor with an authenticator app. Text message codes aren't safe because attackers can trick your phone carrier into moving your number to their SIM card. Instead, use an app like Google Authenticator and turn on two-factor authentication for your accounts. Rotate or retire your API keys. If you've vibe coded a bunch of apps like me, ask ChatGPT or Claude: “Audit all my projects for any leaked keys and help me rotate my active keys and archive ones that I no longer use.” AI found two keys in Anthropic Console that were still active for apps I stopped using. Ask AI to scan and update your software. Ask ChatGPT or Claude: “Check my computer and apps for any updates. Run a dependency audit on all my projects. Don't install anything, just list everything that you found.” Vendors are shipping security fixes fast right now, so it's worth running this every few days. Don't trust “breach” emails or calls. You should expect a wave of phishing emails that claim a service got hacked and ask you to act now. Check the sender's address and right-click the button and choose “Copy link address” to see where it actually goes. I basically try to avoid clicking any links in supposedly “urgent” emails. Get your personal security audit with my AI prompt I turned all 6 steps above into one prompt that you can paste into ChatGPT , Claude , or your favorite AI agent to walk you through everything and even build a personal security audit report like this: My prompt gets AI to generate a personal security report that you can then review It's read-only by default, so it won't change anything without your approval. Upgrade now to get the full prompt below, plus access on behindthecraft.com along with 16+ other AI skills, my Personal AI course, and more. Upgrade to get instant access Here's the full prompt for you to copy and paste into your favorite AI agent: 
 
 
 Read more

</details>