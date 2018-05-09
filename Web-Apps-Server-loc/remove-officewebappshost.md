---
title: Remove-OfficeWebAppsHost
TOCTitle: Remove-OfficeWebAppsHost
ms:assetid: d0f7b5c2-da0f-421a-8478-c39b247c3ac5
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219453(v=office.15)
ms:contentKeyID: 49565145
ms.date: 05/27/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsHost

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

從 Office Web Apps Server 伺服器陣列的「允許清單」中移除主機網域。

## 語法

    Remove-OfficeWebAppsHost -Domain <String>

## 詳細描述

**Remove-OfficeWebAppsHost** Cmdlet 會從「允許清單」中移除指定的主機網域。「允許清單」包含 Office Web Apps Server允許對其傳送檔案操作要求的主機網域。

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
<td><p>Specifies the host domain to remove from the Allow List.</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\------------------範例 1---------------------

    Remove-OfficeWebAppsHost -domain "contoso.com"

此範例會從「允許清單」中移除網域 contoso.com。

## 另請參閱


[New-OfficeWebAppsHost](new-officewebappshost.md)  
[Get-OfficeWebAppsHost](get-officewebappshost.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

