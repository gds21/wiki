---
title: Jamf Pro 安裝條件
description: 
published: true
date: 2021-01-19T05:56:08.878Z
tags: 
editor: markdown
dateCreated: 2021-01-19T05:56:08.878Z
---

# Jamf Pro 安裝條件

## 前置準備表單
你可以使用此表單，確認客戶的環境準備現況：
[Glee Evernote 客戶前置準備作業（英文版）](!https://www.evernote.com/shard/s2/client/snv?noteGuid=1adfd991-8c57-45b7-aa2a-372e2e85edf1&noteKey=2b4a76acbf953ad9&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs2%2Fsh%2F1adfd991-8c57-45b7-aa2a-372e2e85edf1%2F2b4a76acbf953ad9&title=JumpStart%2BPreCall%2BTemplate)

## 準備帳號
1. 請準備 Apple Business Manager 帳號，並確保帳號持有人當日不會請假。
2. 請準備一組公司的 Apple ID 做為 APNS 憑證申請使用。最好別用 ABM 的帳號、也別用 Apple Developer Program 的 Apple ID。建議申請一個 IT 群組的電子郵件，用他來申請 Apple ID。
3. 請用公司個人信箱申請 Jamf Nation 帳號，並提供給經銷商，以接受 Jamf Pro 產品啟動序號。

> 一個公司可以有多組的 Jamf Nation 帳號。通常是 IT 人員各自擁有。擁有 Jamf Nation 帳號才可以收到 Jamf Pro 的產品啟動序號、在 Jamf 論壇上發表文章、送出 Support Ticket 給 Jamf 客服團隊、下載 Jamf Pro 相關管理套件，以及存取 Jamf Pro 線上教學課程。
{.is-info}

4. 在進行 JumpStart 前，客戶有責任準備以下要務，請參考 [Jamf Customer Resposibility](https://www.jamf.com/services/services-policies/)

## 雲端安裝環境
Jamf Pro 有雲端版本可以使用，強烈建議使用雲端，因為：
1. 不用自己管伺服器
2. Jamf 雲端版與地端版功能一樣，價格也一樣
3. Jamf 雲端版會自動備份、升級並且有自動負載平衡設定
4. 使用 Jamf 雲端版可以少開很多公司的防火牆，降低企業風險
5. Jamf 雲端版通過 SOC2 與 ISO27001 的資安認證

<!-- [Jamf Cloud 常見問答](/jamf-pro/jamf-cloud.md) -->


## 地端安裝環境
如果客戶不使用雲端版本，Jamf Pro 亦可以安裝於地端環境，但有以下責任：
1. 客戶未來需自行負責 Jamf Pro 版本升級
2. 客戶需要自行準備域名與憑證
3. 客戶需要在裝機當天自行確保所有環境已經就緒。若未就緒，後續將由 Jamf Support 團隊以遠端的方式提供文件，客戶需參考文件並自行完成架設。
4. 需確保 Jamf Pro 安裝包、MySQL 安裝包、Java 安裝包已下載完畢，或 JumpStart 當天能存取 Jamf Nation 下載安裝包及其它服務位置下載安裝包，並能將安裝包放置於目標伺服器主機。
5. 若是客戶需要用地端環境，請特別繪製 Jamf Pro 架構圖。
6. Jamf Pro 地端僅適用於安裝 Windows Server、RedHat、Ubuntu 與 macOS。版本請參考：[Jamf 產品說明文件裡](https://www.jamf.com/resources/product-documentation/jamf-pro-release-notes/) 的 Jamf Pro System Requirements。

> 如果客戶使用的作業系統為 Linux，再加上網路環境非常封閉的話，在安裝 Jamf Pro 過程中，有可能會需要下載外部相依套件，請確保所有相依套件的外連點都能接上，或事先下載所有相依套件（非常多、而且龐大）
{.is-info}

## 地端安裝架構
JumpStart 會教客戶如何建置單台伺服器。如果客戶的環境需要建置到兩台以上的伺服器，不在 JumpStart 的教學範圍之內，客戶可以：
- 購買 Jamf Professional Service 服務，由 Jamf 工程師施作安裝。
- 自行學習 Jamf Cluster 伺服器安裝技術並自行施作。

Jamf Cluster 的技術可在客戶成為 Jamf 用戶後，在 Jamf Training Catalog 免費習得。

### 單台 Jamf Pro 伺服器
Jamf JumpStart 教育訓練過程中，會教導客戶架設單台 Jamf Pro 伺服器。如有需要架設第二台（含）以上的必要，請考慮 Jamf Professional Service。

單台 Jamf Pro 參考示意圖

![單台 Jamf Pro 參考示意圖](/jamf_pro_single_server.jpg)

### 兩台（含）以上 Jamf Pro 伺服器
通常會需要兩台以上 Jamf Pro 伺服器的，不外乎是以下原因，如果以下的原因不符合你目前正在施作的項目，請與 Jamf 原廠技術顧問聯絡 。如果你正在研究的施作目標同時符合下列多個，代表你每個都必須考慮疊加上去。

#### 目的：不讓 Internet 的人訪問 Jamf 後台
通常是金融業、遊戲業比較需要這樣的架構。這個架構的目標是讓 IT 人員不能在 Internet 上進入 Jamf Pro 後台管理裝置，只能在公司內網完成這個操作。所以如果遇到遠端辦公，沒有人能進到辦公室時，這會是一個問題。

如果客戶可以使用雲端，也可以考慮 Jamf 的 Premium Cloud 雲端版。這種特別定制的 Cloud 可僅允許特定的 IP 才能訪問該公司的 Jamf 後台，一樣可以達到類似的目的，而且不用自架伺服器。

客戶可以自己到 [Installing a Jamf Pro Web Application in the DMZ](https://www.jamf.com/jamf-nation/articles/174/installing-a-jamf-pro-web-application-in-the-dmz) 學會如何在 DMZ 區裡架設一台 Jamf Pro 伺服器，並安置一台 Jamf Pro 伺服器於內部。

#### 目的：為了不讓某一台伺服器掛點後，導致 IT 人員無法更新 Policy

> 請先確定客戶了解： Jamf Pro 伺服器中斷服務，也不會造成設備脫管或是 Policy 消失的前提。在這個前提下，如果 Jamf Pro 伺服器掛掉，只是代表 IT 人員無法更新裝置上的 Policy，原有已經上的管理都會留著。另外會影響到的，如果 Jamf Pro 伺服器在停止服務期間，有新的設備要向 Jamf Pro 進行零接觸部署報到時，會無法正常下放 Policy。
{.is-info}


根據上文，所以如果客戶只是怕 Jamf Pro 中斷服務導致設備脫管或是 Policy 消失的話，是完全不必擔心的。但是，如果今天公司三不五時就會有人不定時的採購新設備並進行零接觸部署，那麼 Jamf Pro 伺服器停止服務就會是一件麻煩事，將會建議部署負載平衡技術。

#### 目的：需要管理的設備數量超過 1000 台，需要負載平衡

## 防火牆設定
[請參考防火牆設定篇](/jamf-pro/jamf-pro-installation/firewall)