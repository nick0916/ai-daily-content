---
id: inbox_bb633b10
date: 2026-10-01
source_ref: "[[00-inbox/2026-10-01/0101-tomsguide-chatgpt-security-researchers-discover-fake-chatg-3772]]"
title: "Security researchers discover fake ChatGPT ads that trick you into downloading malware"
url: https://www.tomsguide.com/computing/malware-adware/security-researchers-discover-fake-chatgpt-ads-that-trick-you-into-downloading-malware
source: tomsguide-chatgpt
published_at: 2026-10-01T18:23:33+00:00
fetched_at: 2026-10-25T01:20:50.493910+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "假 ChatGPT 贊助廣告以 ClickFix 手法誘騙 Windows 使用者執行惡意指令。 **Why** 使用者搜尋 ChatGPT 時，看到的贊助廣告可能導向仿冒網站，且外觀與正版相似。 **How** 假站在輸入提示後導向「備援網域」，接著出現偽造的 Cloudflare 驗證頁，要求使用者按 Win+R 執行指令，進而下載 NetSupport RAT 遠端控制工具。 **What** Island 研究人員指出，2026 年 5 至 8 月間約有 850 則付費廣告、26 個假連結與 71 個 Google Ads campaign ID；Google 表示已停用相關廣告主帳號。正版請直接輸入 chatgpt.com，任何網站要求按 Win+R 或執行 PowerShell 都不應照做。"
key_points:
  - "攻擊流程：Google 贊助廣告→假 ChatGPT 站→「備援網域」→偽造 Cloudflare 驗證頁要求執行指令→下載 NetSupport RAT"
  - "Island 研究人員指出，2026 年 5 至 8 月間約有 850 則付費廣告、26 個假連結、71 個 Google Ads campaign ID；惡意軟體透過 Telegram bot 回傳資料"
  - "防範方式：直接輸入 chatgpt.com；網站要求按 Win+R 或執行 PowerShell 時不要操作；確保防毒軟體與系統更新保持最新"
tags: [malvertising, clickfix, fake-chatgpt, malware, phishing]
topics: [security, foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Security researchers discover fake ChatGPT ads that trick you into downloading malware

假 ChatGPT 贊助廣告以 ClickFix 手法誘騙 Windows 使用者執行惡意指令。

**Why** 使用者搜尋 ChatGPT 時，看到的贊助廣告可能導向仿冒網站，且外觀與正版相似。

**How** 假站在輸入提示後導向「備援網域」，接著出現偽造的 Cloudflare 驗證頁，要求使用者按 Win+R 執行指令，進而下載 NetSupport RAT 遠端控制工具。

**What** Island 研究人員指出，2026 年 5 至 8 月間約有 850 則付費廣告、26 個假連結與 71 個 Google Ads campaign ID；Google 表示已停用相關廣告主帳號。正版請直接輸入 chatgpt.com，任何網站要求按 Win+R 或執行 PowerShell 都不應照做。

### 重點
- 攻擊流程：Google 贊助廣告→假 ChatGPT 站→「備援網域」→偽造 Cloudflare 驗證頁要求執行指令→下載 NetSupport RAT
- Island 研究人員指出，2026 年 5 至 8 月間約有 850 則付費廣告、26 個假連結、71 個 Google Ads campaign ID；惡意軟體透過 Telegram bot 回傳資料
- 防範方式：直接輸入 chatgpt.com；網站要求按 Win+R 或執行 PowerShell 時不要操作；確保防毒軟體與系統更新保持最新

**原文：** [tomsguide-chatgpt](https://www.tomsguide.com/computing/malware-adware/security-researchers-discover-fake-chatgpt-ads-that-trick-you-into-downloading-malware)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Update: Google responds to inquiries about this attack. Sponsored Google ads for fake ChatGPT are leading Windows users to download malware in "ClickFix" traps, according to security researchers from the AI company Island . The sponsored Google ads lead to Custom GPT sites that are built to look like normal ChatGPT websites. These ads pop up when people type terms like "chatgpt" into Google Search. Unfortunately, for trapped users, the ads do go to legitimate chatgpt.com sites. However, in these instances, entering a prompt makes the fake service direct people to a "backup domain" due to "high traffic." Clicking on that link then redirects unsuspecting users to another fake instance of ChatGPT with a fake Cloudflare verification page that contains ClickFix instructions. Island found nearly identical responses across two separate Custom GPTs over a 3-day period in August. According to the researchers, the malware advertising campaign appeared to involve around 850 paid ads, 26 fake ChatGPT links, and 71 Google Ads campaign IDs over a three-month period from May 2026 through August 2026. What is ClickFix? (Image credit: Sekoia/Tom's Guide) ClickFix traps are built to trick people into installing or executing malicious commands on their devices. In this instance, the instructions from the backup domain trick Windows into running a command that downloads malware onto your computer. Once installed, the malware infects the system. It can even survive PC restarts and uses a Telegram bot to send stolen info back to the hackers behind this camping The malware utilizes a tool called NetSupport RAT , which lets attackers remotely control an infected computer. Island found that the domains rotated and other Windows malware-delivery forms were identified too suggesting that the attack is not based on a single website. The company claims an AI tool highlighted the suspicious activity and human researchers confirmed it. However, it's not clear how many people may have been affected by this scam. A Google spokesperson told Tom's Guide that it has already suspended accounts associated with this attack. "Before this report was published, we suspended the advertiser accounts involved to block this scheme and updated our defenses to better detect these tactics," a spokesperson said. We were told that Google is monitoring new attempts to utilize fake ads. Google does have a policy that does not allow misleading ads about a business, product, service or destination. Per Google, the company blocked more than 400 million misleading ads for violating Google's "Misrepresentation" policies last year. How to avoid falling victim to online scams (Image credit: Rawpixel.com/Shutterstock) The combination of malware and advertising — also known as malvertising — has a long, storied history, which means you should always be careful when clicking on any advertisement online. To stay safe, you could try using one of the best ad blockers, since Google's "sponsored" links are still technically ads; most blockers will hide them. Beyond that, if you don't have or want an ad blocker, there are some red flags to note when using a search engine and especially if you get linked to a fake instance of ChatGPT. As for ChatGPT, if you are an existing user or just trying it out, go to chatgpt.com; no need to search for it. Likewise, I've covered ChatGPT outages quite frequently over the course of the last two years and even at its worst, the AI assistant never sends you to a "backup domain." Don't click that link. If ChatGPT is having issues, you can always check the OpenAI status page . At the same time, no website verification or CAPTCHA will ever ask you to open Windows Run and paste a command. If a website asks you to press Win + R or run PowerShell, don't do it. Finally, you should always have one of the best antivirus software solutions installed on your PC. From there, you want to ensure that your antivirus is current, updated and running on all your devices – both your computer and even your smartphone. More from Tom's Guide AI agents are going rogue and causing new security headaches — but Nvidia has a way to stop them Apple issues emergency update for millions of iPhones, iPads, and Macs — update your devices now Your personal information is everywhere online — 5 ways to start removing it from the internet

</details>