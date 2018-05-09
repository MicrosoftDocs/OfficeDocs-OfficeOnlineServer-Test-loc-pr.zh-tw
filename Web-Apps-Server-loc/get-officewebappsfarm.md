---
title: Get-OfficeWebAppsFarm
TOCTitle: Get-OfficeWebAppsFarm
ms:assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219434(v=office.15)
ms:contentKeyID: 49565093
ms.date: 05/27/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsFarm

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2013-12-18_

傳回目前伺服器所屬的 OfficeWebAppsFarm 物件。

## 語法

    Get-OfficeWebAppsFarm

## 詳細描述

**Get-OfficeWebAppsFarm** Cmdlet 會傳回目前伺服器所屬之 OfficeWebAppsFarm 物件的詳細資料。此物件代表一群聯合運作並以單一裝置形態提供 Office 文件之網路編輯與檢視功能的伺服器。**Get-OfficeWebAppsFarm** Cmdlet 不使用任何參數。

## 參數

## 輸入類型

## 傳回類型

## 範例

\------------------範例 1---------------------

    Get-OfficeWebAppsFarm

此範例會傳回 OfficeWebAppsFarm 物件的詳細資料。

\------------------範例 2---------------------

    (Get-OfficeWebAppsFarm).Machines

此範例會傳回隸屬於 Office Web Apps Server伺服器陣列之伺服器的詳細資料，包括每部伺服器的健康狀態及其所具有的角色。

## 另請參閱


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

