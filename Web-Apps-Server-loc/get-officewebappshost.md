---
title: Get-OfficeWebAppsHost
TOCTitle: Get-OfficeWebAppsHost
ms:assetid: a9b766a7-a15c-4bbf-9750-31719406d65f
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219446(v=office.15)
ms:contentKeyID: 49565122
ms.date: 05/27/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsHost

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2013-12-18_

傳回 Office Web Apps Server 伺服器陣列之「允許清單」中的主機網域清單。

## 語法

    Get-OfficeWebAppsHost

## 詳細描述

**Get-OfficeWebAppsHost** Cmdlet 會傳回主機網域的清單，而這些即是 Office Web Apps Server允許對其發出檔案操作要求 (例如檔案擷取、中繼資料擷取及檔案變更等等) 的主機網域。 此清單屬於安全性功能，稱為「允許清單」，可以避免不需要的主機連線到 Office Web Apps Server 伺服器陣列，在您不知情的情況下利用此伺服器陣列從事檔案操作。

「允許清單」中的所有網域皆會設以萬用字元 \* ，以一併允許所有的子網域。例如，若網域 contoso.com 列名於「允許清單」內，Office Web Apps Server也會允許對網域 domains corp.contoso.com 及 dev.contoso.com 的要求。除此之外對於其他網域 (如 fabrikam.com) 的要求將予禁止。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219446.Caution(Office.15).gif" title="注意" alt="注意" /><strong>注意：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>「允許清單」內若無任何網域，Office Web Apps Server將會允許對所有網域主機的檔案要求。您的 Office Web Apps Server伺服器陣列若可從網際網路存取，請勿將此清單留空，否則所有人皆可使用您的 Office Web Apps Server伺服器陣列檢視及編輯內容。</td>
</tr>
</tbody>
</table>


## 參數

## 輸入類型

## 傳回類型

## 範例

\------------------範例 1---------------------

    Get-OfficeWebAppsHost

此範例會傳回「允許清單」上所列的主機網域。

## 另請參閱


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

