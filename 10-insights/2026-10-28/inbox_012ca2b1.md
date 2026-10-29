---
id: inbox_012ca2b1
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/youtube/0020-youtube-i'm-阿湯-ai-windows-macos-7bdb]]"
title: "用 AI 打造的工具,怎麼編譯成 Windows 及 macOS 的軟體?"
url: https://www.youtube.com/watch?v=zZOJITqREak
source: youtube-i'm-阿湯
published_at: 2026-10-28T12:00:00+00:00
fetched_at: 2026-10-29T00:23:47.378790+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "不用兩台電腦，請 AI 把程式推到 GitHub，讓 GitHub Actions 幫你編出 Windows exe 與 macOS dmg。 **Why** 在 Mac 上很難編出 Windows 的 exe，反過來在 Windows 上編 macOS App 也麻煩，多數開發者得備兩套系統。 **How** 先用 Claude Code 做出程式，再到 GitHub 建立 Classic Personal Access Token（只給 repo 與 workflow 權限，期限設短），交給 AI 推送並設定 GitHub Actions 去建置 exe 與 dmg，最後在 Release 頁下載。 **What** 阿湯示範用 Claude Code（Python）做工程數學計算機，推上 GitHub 後版本從 1.0.0 自動更新到 1.2.0 並建置完成。他提醒 Mac 要分 Intel 與 M 系列晶片，若沒要求，輸出只有 M 系列版本；建議先讓 AI 規劃再執行，且 Token 用完要刪除。"
key_points:
  - "流程：Claude Code 寫程式 → 建立 GitHub Classic PAT（僅勾 repo 與 workflow，期限設短）→ 交給 AI 推送並設定 GitHub Actions → 在 Release 下載 Windows exe 與 macOS dmg"
  - "macOS 要分 Intel 與 M 系列晶片，需明確要求 AI 兩種都編，否則只輸出 M 系列版本"
  - "安全做法：PAT 給 AI 後要刪除或設短期限；也建議先請 AI 規劃再執行"
tags: [github-actions, claude-code, cross-platform-build, tutorial, pat]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 用 AI 打造的工具,怎麼編譯成 Windows 及 macOS 的軟體?

不用兩台電腦，請 AI 把程式推到 GitHub，讓 GitHub Actions 幫你編出 Windows exe 與 macOS dmg。

**Why** 在 Mac 上很難編出 Windows 的 exe，反過來在 Windows 上編 macOS App 也麻煩，多數開發者得備兩套系統。

**How** 先用 Claude Code 做出程式，再到 GitHub 建立 Classic Personal Access Token（只給 repo 與 workflow 權限，期限設短），交給 AI 推送並設定 GitHub Actions 去建置 exe 與 dmg，最後在 Release 頁下載。

**What** 阿湯示範用 Claude Code（Python）做工程數學計算機，推上 GitHub 後版本從 1.0.0 自動更新到 1.2.0 並建置完成。他提醒 Mac 要分 Intel 與 M 系列晶片，若沒要求，輸出只有 M 系列版本；建議先讓 AI 規劃再執行，且 Token 用完要刪除。

### 重點
- 流程：Claude Code 寫程式 → 建立 GitHub Classic PAT（僅勾 repo 與 workflow，期限設短）→ 交給 AI 推送並設定 GitHub Actions → 在 Release 下載 Windows exe 與 macOS dmg
- macOS 要分 Intel 與 M 系列晶片，需明確要求 AI 兩種都編，否則只輸出 M 系列版本
- 安全做法：PAT 給 AI 後要刪除或設短期限；也建議先請 AI 規劃再執行

**原文：** [youtube-i'm-阿湯](https://www.youtube.com/watch?v=zZOJITqREak)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

今年教了大家很多有關於 AI打造網頁工具的一些相關教學 有人就問到說如果 今天想要打造成macOS軟體或者是Windows軟體的話 那又要怎麼去做呢 這些AI打造出來的程式 我完全不知道怎麼把它變成Windows的exe檔 或是變成macOS的dmg檔案 今天我們就來教大家這個打造軟體的基礎中的基礎 究竟要怎麼去編譯成Windows可以執行的檔案 以及macOS可以執行的APP 好 先來看吧 GO 嗨 我是阿湯 看了那麼多AI相關教學之後 你是不是用來打造一些程式或是工具越來越上癮了啊 有種停不下來的感覺 感覺隨時想到什麼就想要來做一個工具看看 但是呢做多了之後你就會發現一件事情 其實也不是所有的工具我都要把它做成網頁工具嘛 畢竟呢所有東西你都要架設到網頁上去也是蠻麻煩的 有些小工具如果它本來就是離線就要可以使用的話 那不如我們就是把它打造成軟體來使用就好了 所以我們今天就要來教大家究竟呢 到底要怎麼在AI打造完程式之後 把它編譯成Windows軟體以及macOS可以執行的APP 畢竟這兩個系統它是不一樣的東西 如果你想要在macOS上面編譯成Windows可以執行的exe檔 其實蠻麻煩的 相對的你要在Windows上面編譯出macOS可以執行的APP 一樣很麻煩 所以我們今天就會教大家一個方式解決這個共通的困擾哦 好首先我們要先來說明一下 如果你今天呢想要在mac電腦上面打造一個工具 是可以同時用在Windows以及macOS的這個軟體的話 那你必須要分成Windows可以run的這個exe檔案 以及macOS可以執行的APP檔案 那在這樣的情況下呢會有一個小問題就是 當我在mac上面開發的時候 我只能用Xcode來編輯我mac可以run的這個APP 但是呢 你想要把它編譯成Windows可以執行的這個exe檔的話呢 是沒有辦法的 你必須要透過其他工具 或者是呢你只能在Windows上面去做編譯 那相反過來呢 如果你今天在Windows上開發的話 你想要把它編輯成exe檔的話 是完全沒有問題的 但是如果你要把它編譯成macOS檔案的話 也是比較麻煩的 所以呢大部分開發者呢 他們都會有兩個系統可以去執行使用 那另外一種方式呢 我們就是今天要來介紹 就是當我們開發完之後 其實我們是可以透過GitHub 來幫我們把它編譯成mac可以跑的這個APP檔案 以及Windows可以執行的exe檔案 那這個部分要怎麼去做呢 往下來跟大家做分享 在開始編譯之前呢 我們先來簡單做一個小工具 就是用AI來製作一個小工具 然後我們可以讓AI清楚的知道 我們等一下呢是要把它編譯成 Windows的執行檔以及macOS的APP檔案 好比如說我們今天要做一個工程數學計算機 那我今天是用claude Code來做 那一樣我在macOS上面來做示範給大家看 claude Code的這個執行的方式 以及一些使用方式呢 我就不特別的詳細介紹了 但大家可以大概看一下 我是怎麼去用它來寫出這個程式 可以在mac上面跑 以及在Windows上面跑 那就給大家做一個基礎開發的這個參考 那首先呢 像我今天是用中文機的方式 我先開了一個資料夾 在mac上面呢 你就可以直接右鍵這個資料夾 然後新增位於檔案夾位置的終端機視窗 這邊呢你就可以有終端機的介面 可以去做開發 然後我們就可以去執行claude 那我像我這樣執行呢 意思就是等一下他任何需要要求權限的 就不會再問我 他會一次按照我的需求 然後執行到完成再告訴我 好那我們來執行一下claude 好比如說呢 我告訴claude Code呢 說幫我做一個工程數學計算機軟體 那跟大家講好 我就是我最後要分別編譯成 Windows可以用的exe檔案 跟macOS K的DMG檔案 然後我會告訴他 我是要透過GitHub來製作 叫他先去做程式就好 我們把他送出 如果你跟我一樣呢 是略過所有權限的這個方式 去執行claude的話呢 那我會建議呢 你給他指令之後 可以告訴他呢 你先規劃給我看 確認後再開始執行 這樣呢他就會先把規劃列出來 他要怎麼做 你就會比較清楚他規劃出來 有沒有理解你想要這些功能 好像我剛剛簡短的這些指令完之後 他就有先問我一下 要技術框架是什麼 功能需求UI風格 好我們來選一下 那我們就選最快速的這個 開發最快速 再來功能需求呢 我們就來先看一下核心功能就好 最後有一個UI風格 那我們就說都可以 把他送出 然後開始去進行開發 因為我們今天重點是要教大家 怎麼透過GitHub 來把他編譯成 macOS的DMG檔案 以及Windows要執行的exe檔案 好給他看一下 我就算沒有告訴他先規劃 他一樣先規劃給我看 然後呢等我確定之後 然後才會開始 好我們就讓他開始製作吧 好這邊AI呢 已經用Python這個程式呢 把我要的工程數學計算機做完了 接下來我們下一個步驟呢 就是要把他推送到GitHub上面 然後把他編譯成 Windows可以執行的exe檔案 還有macOS可以執行的DMG檔案 接下來我們要怎麼去製作呢 我們可以先到我們的GitHub上面的帳號 然後把他登錄之後 我們直接在右上角 點擊Settings進去 然後往下拉 拉到底會有一個開發者的設定 Developer Settings 進去之後呢 這邊會有一個Personal Access Token 我們把他點擊進去 再點擊Token 這邊我們就可以去建立一個新的Token 那選擇Classic這個 好名稱呢你可以輸入一個你記得住的 因為呢這個Token我們給AI用完之後 記得要回頭來把他刪掉 或者是這個期限可以設短一點 一週甚至你可以Custom 然後再把他設定短一點 到哪一天就會過期 畢竟呢我們把這種隱私的金鑰呢 丟給AI他並不是一個安全的事情嘛 所以我們可以把期限設短一點 避免你後續呢忘記回來刪除 那我們今天做的是工程計算機 我就打個工程計算機標記一下 好權限我們要給哪些呢 第一個是Repo 第二個是Workflow 這樣就好了給兩個權限 好我們就往下Generate Token 好這邊產生出來之後 我們就把他複製起來 然後等一下我們要丟給AI 告訴他可以推送到這邊來產生 接下來你就可以很簡單的告訴他呢 就是你提供給他 GitHub的Personal Access Token 然後呢這給他之後推送 並且編譯成Windows exe 還有macOS的DMG檔案 然後叫他幫你編輯一下 Readme的說明 也就是GitHub上面的這個說明頁面 全部交給AI去編輯說明就好 好我們把他送出 等他整個完成之後 我們再去看GitHub頁面 來下載使用就可以了 好那因為我們沒有先在GitHub上面 建立專案 所以他就給我們一個 他準備推送的這個名稱 那如果你沒有要修改的話 就直接照他去推送就好 然後跟他說繼續推送就好 那這個過程他就先把檔案 推送到GitHub上面去 推送完之後他會利用GitHub上面 有一個功能叫GitHub Actions 他就用來建立Windows的檔案 跟macOS的檔案有沒有 這邊其實都有說明 接下來我們就繼續等 等他全部建置完之後 我們再來看下載檔案 能不能使用就好 好剛剛在這個編譯過程中 我剛好自己忽略一件事情 順便提醒一下大家 如果你在開發Mac的軟體的時候 記得Mac的App 現在因為Mac電腦 他有分為以前舊版的 Intel晶片系列的電腦 跟新版的M系列的晶片的電腦 這兩款的電腦的這個App 是要分開開發的 在編譯上有點不太一樣 那我剛忘記做這件事情 所以他最後輸出給我的是 M系列晶片的這個App 那如果你想要也加入 Intel的電腦也可以使用的話 就記得要在AI這邊也要告訴他 那他最後在Github這邊生成了 就會有兩種晶片的這個檔案 可以去做使用 他最後從1.0.0一直更新 自己更新到變成1.2.0 終於完成編譯然後上線了 好那我們編譯完之後 我們就可以到我們的Github上面來看 你看這個文字說明 然後下載檔案這邊都已經告訴你 那我們可以到Release這邊 去查看所有的版本 我們來看一下 你看這邊我們就可以直接去下載 我們這個Mac的版本 好把它下載來做使用 我們這邊測試就完成了 App是可以打開的 那這個功能我就不去驗證了 主要是教大家 就是要怎麼透過Github Actions的功能 去幫你直接編譯出 Windows可以用的檔案 以及Mac可以用的檔案 所以大家如果之後在製作軟體的時候 可以直接透過Github上傳來控制版本 順便可以讓Github Actions 幫你去做編譯就好了 你就不用去煩惱 你的Mac電腦如果要編譯成 Windows電腦可以用的工具要怎麼用 如果你是Windows 又要怎麼可以把它編譯成 macOS可以用的這個工具 那你就可以透過這個方式 讓大家去試看看囉 看完上面的教學之後 你沒想到Github居然這麼好用吧 除了用來控制你製作的 這些程式的版本之外 它也可以直接透過Github 來編譯成Windows的ex檔案 以及macOS的DNG檔案 甚至我們還可以直接把檔案 就存放在Github上面 給別人去下載喔 是不是真的很方便呢 今天影片我們就分享到這邊了 如果喜歡今天影片 別忘了按贊訂閱分享 還有開啟小鈴鐺 如果想要知道更多AI相關教學的話 別忘了在底下留言告訴我喔 我是阿湯下次見掰掰

</details>