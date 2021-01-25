---
title: 零接觸部署
description: 
published: true
date: 2020-12-24T04:15:04.755Z
tags: 
editor: markdown
dateCreated: 2020-12-13T10:07:40.594Z
---


# 哪些機器適用於零接觸部署
要思考哪些機器適用於零接觸部署，只要思考兩個因素就好，分別是：
- 作業系統
下方連結有一篇 Jamf Pro System Requirements > Computer and Mobile Device Management 裡面有提到至少需要的作業系統版號。
https://www.jamf.com/resources/product-documentation/jamf-pro-release-notes/
- 機器取得來源
來源通常可以是以下二個地方，如果不是這二個地方取得的機器，是無法使用零接觸部署的。不過，不能使用零接觸部署不等於無法管理。
1. 跟企業經銷商/教育經銷商採購的 iPad、iPhone、Apple TV 與 macOS 設備。
2. 跟 Apple Store 直營店商務團隊所購買的 iPad、iPhone、Apple TV 與 macOS 設備。

# 零接觸部署通路聯絡方式
- 企業經銷商
https://www.apple.com/tw/education/how-to-buy/aaer.html
- 教育經銷商
https://www.apple.com/tw/buy/reseller/enterprise.html
- Apple Store
https://www.apple.com/tw/retail/

# 零接觸部署的概念
請觀看以下的影片:
https://docs.jamf.com/education-services/jamf-100-course/4.0/Lesson_21__Automated_Device_Enrollment_and_PreStage_Enrollments.html

在影片中，你會看到 Apple Business Manager / Apple School Manager 等服務，這些都是給用戶免費申請的。每一個公司或學校都可以免費申請這個帳號。此外，一所企業或學校只能申請一個帳號，如果單位裡面需要有很多人都能使用 Apple Business Manager / Apple School Manager 的話，在這兩個平台裡面都能開子帳號給其它人。

<!-- # 實作零接觸部署影片

以下影片將介紹 SSO 的整合部分。（請額外參考 Jamf Connect）

## 零接觸部署整合 Azure AD
## 零接觸部署整合 Google Suite
## 零接觸部署整合 Active Directory -->

# 零接觸部署的實施注意事項
任何需要 IT 人員介入設定設備的情況，都會被視為破壞體驗。為了最終用戶可以自己開箱，很多原本由 IT 預先配置的事項，都會需要改由雲端自動配置，這其中就包含：

1. 網路設定（VPN、憑證、MAC Address）
2. 軟體安裝
3. 身份機制


| Mac 需考慮事項 | 在家領設備 | 辦公室領設備 |
|--------|---------|----------|
|Jamf Pro 伺服器的位置|如果 Jamf 伺服器在地端上，確認用戶在家的網路可以與地端的 Jamf Pro 進行通訊；如果是使用 Jamf Cloud 的話就不需要擔心|如果 Jamf 伺服器在地端的話，請確認用戶所使用的網路能否與 Jamf Pro 伺服器溝通。如果使用 Jamf Cloud，需確認公司防火牆已做對應設置|
|用戶電腦需不需要接微軟 AD 伺服器|電腦在一開機的設定階段時，無法用 VPN 回到公司的 AD 伺服器，會造成帳號零接觸部暑失敗。有可能需要考慮使用 ADFS 或其它雲端 IdP 服務|確認該設備使用的網路可以碰到 AD|
|是否需要接802.1x網路| N/A |需要先有憑證才能接802.1x網路，會需要準備另外一種網路能接到 Apple 與 Jamf Pro，啟用完電腦後再自動接回公司的 802.1x 網路|
|資安軟體部署|資安軟體會要求存取磁碟上的所有文件。基於蘋果隱私政策，如果用戶未同意該資安軟體存取磁碟，則該軟體也無法正常作用。需從Jamf Pro 部署 PPPC 設置，將該軟體設定為隱私允許名單|同左|
|核心軟體部署|如驅動程式、網路相關或其它接觸到系統核心的軟體。如果使用者不同意載入核心套件，則該程式仍不會啟動。需從 Jamf Pro 部署允許名單載入核心套件。|同左|
|CIS合規事項|舉凡磁碟加密、密鑰回收、資安設定等，確保設備在開機時就能由 Jamf Pro 正確部署|同左|