---
title: 防火牆設定
description: 
published: true
date: 2020-12-14T09:59:01.458Z
tags: 
editor: markdown
dateCreated: 2020-12-14T09:45:05.853Z
---

## 防火牆設定

- JSS = Jamf Pro Server
- On-Prem = 地端用戶請特別留意
- Cloud = 雲端用戶特別留意

| Env | Port | Protocol | Source | Destination | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| On-Prem | 2197,443 | HTTPS | JSS | 17.0.0.0/8 | NA |
| On-Prem | 80 | HTTP | JSS | 17.0.0.0/8 | iTunes Service |
| On-Prem | 443 | HTTPS | JSS | 17.0.0.0/8 | DEP |
| On-Prem | 443 | HTTPS | JSS | \*.jamfcloud.com | NA |
| On-Prem | 3306 | MySQL | JSS | MySQL DB IP | NA |
| On-Prem | 80,443 | HTTPS | JSS | app.pendo.io, cdn.pendo.io, pendo-io-static.storage.googleapis.com | Jamf Engage |
| On-Prem | 80,443 | HTTPS | JSS | login.microsoftonline.com, graph.windows.net, \*.manage.microsoft.com | MS Intune |
| On-Prem | 389,636 | LDAP/S | JSS | AD DC | NA |
| On-Prem | 25,465,587 | SMTP/S | JSS | SMTP Server | NA |
| On-Prem | 8443 | HTTPS | 蘋果裝置/IT人員工作站 | JSS | NA |
|  | 5223,443 | APNS | 蘋果裝置 | 17.0.0.0/8 | APNS |
|  | 548,445, 137-139 | SMB | 蘋果裝置/IT人員工作站 | Distribution Point | NA |
|  | 22 | SSH | IT 人員工作站 | 蘋果裝置 | 非必要 |
| Cloud | 25,465,587 | SMTP/S | 52.192.208.126 / 52.68.207.143 | SMTP Server | 東京 IP |
| Cloud | 389,636 | LDAP/S | 52.192.208.126 / 52.68.207.143 | LDAP Server | 東京 IP |


## Jamf Hosted Cloud S3 發起域名

Jamf Hosted Cloud 已配置無限大空間的 Jamf Cloud Distribution Point，座落於東京的伺服器發起連線的域名如下：

* apne1-jcdsdownloads.services.jamfcloud.com
* apne1-jcds.services.jamfcloud.com


## 參考資料
[https://support.apple.com/en-bn/HT210060](https://support.apple.com/en-bn/HT210060)

[https://developer.apple.com/news/?id=11042019a](https://developer.apple.com/news/?id=11042019a)

[https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro)

[https://www.jamf.com/jamf-nation/articles/409/permitting-inbound-outbound-traffic-with-jamf-cloud](https://www.jamf.com/jamf-nation/articles/409/permitting-inbound-outbound-traffic-with-jamf-cloud)