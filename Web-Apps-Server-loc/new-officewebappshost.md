---
title: New-OfficeWebAppsHost
TOCTitle: New-OfficeWebAppsHost
ms:assetid: f1d523ab-45c6-4e3c-b274-22c0d229a6a0
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219459(v=office.15)
ms:contentKeyID: 49565161
ms.date: 05/27/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsHost

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

將主機網域新增至 Office Web Apps Server 伺服器陣列的「允許清單」。

## 語法

    New-OfficeWebAppsHost -Domain <String>

## 詳細描述

**New-OfficeWebAppsHostt** Cmdlet 會將主機網域加入主機網域的清單，而這些即是 Office Web Apps Server允許對其發出檔案操作要求 (例如檔案擷取、中繼資料擷取及檔案變更等等) 的主機網域。 此清單屬於安全性功能，稱為「允許清單」，可以避免不需要的主機連線到 Office Web Apps Server 伺服器陣列，在您不知情的情況下利用此伺服器陣列從事檔案操作。

<table>
<thead>
<tr class="header">
<th><img src="images/Ee890080.tip(Office.15).gif" title="提示" alt="提示" /><strong>提示：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>You may any domain type including: Public, Pool, Farm, and Active Directory domain names. Just make sure that the domain you're granting access to meets your security requirements.</td>
</tr>
</tbody>
</table>


加入「允許清單」中的所有網域皆會設以萬用字元 \* ，以一併允許對所有子網域發出的要求。例如，若將網域 contoso.com 加入「允許清單」，Office Web Apps Server也會允許對網域 domains corp.contoso.com 及 dev.contoso.com 的要求。除此之外對於其他網域 (如 fabrikam.com) 的要求將予禁止。

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


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>參數</th>
<th>必要</th>
<th>類型</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Domain</strong></p></td>
<td><p>必要</p></td>
<td><p>System.String</p></td>
<td><p>指定要加入「允許清單」的網域。請勿指定星或以句號為開頭。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\------------------範例 1---------------------

    New-OfficeWebAppsHost -domain "contoso.com"

此範例會將網域 contoso.com 加入「允許清單」。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>您無法同時將多個主機網域新增至「允許清單」。您必須對每個要新增至「允許清單」的主機網域執行 New-OfficeWebAppsHost Cmdlet。</td>
</tr>
</tbody>
</table>


## 另請參閱


[Get-OfficeWebAppsHost](get-officewebappshost.md)  
[Remove-OfficeWebAppsHost](remove-officewebappshost.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

