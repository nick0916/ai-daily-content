---
id: inbox_8ed9ca05
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0102-lobsters-vibecoding-someone-on-torrent-sites-kept-fucking-wi-00e5]]"
title: "Someone on Torrent Sites Kept Fucking With My Sonarr"
url: https://thereallo.dev/blog/someone-on-torrent-sites-kept-fucking-with-my-sonarr-setup
source: lobsters-vibecoding
published_at: 2026-10-16T15:47:02-05:00
fetched_at: 2026-10-25T01:28:03.601234+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "偽裝成影集種子的 .exe 惡意程式，會竊取瀏覽器、錢包與開發者憑證。 **Why** 作者的 Sonarr 設定反覆受到此類假種子干擾。 **How** 程式讀取自身檔案尾端 64 bytes，從中找到並解密（文中示例為 ChaCha20）隱藏的 payload，再以手動映射 PE 的方式於記憶體中執行。 **What** 目標包括多款瀏覽器的密碼與 cookie、加密貨幣錢包、密碼管理器、Discord 與 Steam 帳號，以及 .ssh、.aws 等開發者憑證；作者建議在 qBittorrent 排除 .exe、.scr、.lnk、.bat、.cmd，並在 Sonarr/Radarr 將來源加入黑名單。"
key_points:
  - "假種子內含 PE 惡意程式，檔名類似 South Park S29E03 1080p ... .exe，載入流程為解密 payload 後在記憶體中執行"
  - "竊取範圍涵蓋瀏覽器、加密貨幣錢包、密碼管理器、通訊與遊戲帳號，以及 .ssh、.aws、.kube 等開發者憑證"
  - "防護：qBittorrent 的 Excluded file names 加入可執行檔副檔名；Sonarr 以 Remove from client 加入黑名單；Prowlarr 降級或移除反覆提供此類檔案的 tracker"
tags: [malware, torrent, infostealer, supply-chain, home-lab]
topics: [security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Someone on Torrent Sites Kept Fucking With My Sonarr

偽裝成影集種子的 .exe 惡意程式，會竊取瀏覽器、錢包與開發者憑證。 **Why** 作者的 Sonarr 設定反覆受到此類假種子干擾。 **How** 程式讀取自身檔案尾端 64 bytes，從中找到並解密（文中示例為 ChaCha20）隱藏的 payload，再以手動映射 PE 的方式於記憶體中執行。 **What** 目標包括多款瀏覽器的密碼與 cookie、加密貨幣錢包、密碼管理器、Discord 與 Steam 帳號，以及 .ssh、.aws 等開發者憑證；作者建議在 qBittorrent 排除 .exe、.scr、.lnk、.bat、.cmd，並在 Sonarr/Radarr 將來源加入黑名單。

### 重點
- 假種子內含 PE 惡意程式，檔名類似 South Park S29E03 1080p ... .exe，載入流程為解密 payload 後在記憶體中執行
- 竊取範圍涵蓋瀏覽器、加密貨幣錢包、密碼管理器、通訊與遊戲帳號，以及 .ssh、.aws、.kube 等開發者憑證
- 防護：qBittorrent 的 Excluded file names 加入可執行檔副檔名；Sonarr 以 Remove from client 加入黑名單；Prowlarr 降級或移除反覆提供此類檔案的 tracker

**原文：** [lobsters-vibecoding](https://thereallo.dev/blog/someone-on-torrent-sites-kept-fucking-with-my-sonarr-setup)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Open its own file.

Read the last 64 bytes.

Use those to find and decrypt a payload hidden in the junk.

Map it as a PE in memory by hand.

Point PEB->ImageBaseAddress at it.

Jump in.

Browsers : Chrome, Edge, Brave, Opera, Opera GX, Vivaldi, Firefox. Passwords, cookies, autofill, and it has code for Chrome's new app bound encryption too.

Crypto wallets : Exodus, Electrum, Atomic, Guarda, Coinomi, Ledger Live, Trezor Suite, Wasabi, Sparrow, Monero, Zcash, Armory, plus extension wallets.

Password managers : KeePass, KeePassXC, Bitwarden, 1Password, NordPass, RoboForm, Windows Credential Manager.

Accounts : Telegram, Discord tokens, Steam, Roblox cookies, Minecraft accounts, Authy.

Dev stuff : .ssh , .aws , .azure , gcloud, .kube , .docker .

Remote access : AnyDesk, TeamViewer, WinSCP, FileZilla, mRemoteNG, RDCMan.

The rest : Outlook, Thunderbird, VPN configs, OBS settings, Sticky Notes, and the documents on your desktop.

qBittorrent : add *.exe , *.scr , *.lnk , *.bat , *.cmd to "Excluded file names", tt'll just refuse to download them.

Sonarr / Radarr : blocklist with "Remove from client" when you see one of these.

Prowlarr : if a tracker keeps serving this crap, demote it or drop it.

Import failed, path does not exist or is not accessible by Sonarr: /data/downloads/torrents/South Park S29E03 1080p WEB H264-MeGusta.exe

pe end 0x1ce00 overlay 886653736 bytes

CompanyName Freeware Developers FileDescription prepares application data OriginalFilename SetupHelper.exe

dword_14000C020 ^= 0x F2C2EAC0 ; v34 = 0 ; dword_14000C020 ^= 0x F2C2EAC0 ;

mask = bytes . fromhex ( " 56951de331cd7f254bf1931533dd82bc3c8bf542f0d1ed5736a40f394c51d0a1 " ) h = fnv1a ( mask ) size = u64 ( footer , 0x 34 ) ^ ( h | h > 8 key = xor ( mask , footer [: 32 ]) nonce = footer [ 32 : 44 ] payload = chacha20 ( key , nonce , data [ - 64 - pad - size : - 64 - pad ])

osinfo browsers telegram wallets discord steam clipboard remoteaccess credentialmanager authy notes obs ssh email games filegrabber

v5 = _mm_xor_ps ( v6 , v5 ); v7 = { 1924987977 , 1270327144 , 877876327 , 271431577 }; v8 = { 641333755 , - 1942364857 , ... }; sub_140080F40 ( & v5 , v7 , v8 , 0x 20 );

cbc b'w\x1c\xe9\xc6\xa0y\x96\xa4...' ctr b'guid=\x00\x00\x00...'

www.youtube.com/channel/UC18vFC1xgebddr_7NsvgBYA gist.githubusercontent.com/jasonterra69/48d9e264c05843f0cdc302143b4400c8/raw [[ ]] ZhxchsdfhSGdfgsgdfAJsakdaksdk2364236AH

b = base64 . b64decode ( " OA0dDQ0HFBQHJyIHEkkQCAlJLS0JTgwAAB8S " ) k = b " ZhxchsdfhSGdfgsgdfAJsakdaksdk2364236AH " bytes ( x ^ k [ i % len ( k )] for i , x in enumerate ( b ))

beenetprotect[dot]com/lgz/gdata

Domain Name: BEENETPROTECT.COM Creation Date: 2026-09-14T06:21:54Z Registrar: Cloudflare, Inc. Name Server: DONALD.NS.CLOUDFLARE.COM Name Server: JULISSA.NS.CLOUDFLARE.COM

</details>