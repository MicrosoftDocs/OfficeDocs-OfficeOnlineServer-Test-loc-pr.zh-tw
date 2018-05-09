---
title: Set-SPWOPIZone
TOCTitle: Set-SPWOPIZone
ms:assetid: bc751cc4-8ac8-45f7-b6ea-da6fcb5473ac
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219451(v=office.15)
ms:contentKeyID: 49565132
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIZone

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

設定目前的 SharePoint 伺服器陣列透過瀏覽器瀏覽至 WOPI 應用程式所使用的區域。

## 語法

    Set-SPWOPIZone [[-Zone] <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Set-SPWOPIZone** Cmdlet 可設定目前的 SharePoint 伺服器陣列透過瀏覽器瀏覽至 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器) 所使用的區域。瀏覽器中的 SharePoint Server 頁面會建立包含 WOPI 應用程式上頁面的框架。 WOPI 應用程式頁面 URL 的區域取決於此設定。

若未設定此區域，則預設值為 “internal-HTTPS”。若您選取 WOPI 應用程式不支援的區域，Office Web Apps 將無法正常運作。請只在使用 IPSEC 之完全安全的網路上 (完全加密)，或在不包含敏感性資料的測試環境中，才使用 HTTP。

SharePoint Management Shell

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
<td><p><strong>Zone</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定區域。如需 WOPI 應用程式支援的區域清單，請執行 <strong>Get-SPWOPIBinding</strong>。</p>
<p>若您同時擁有內部和外部 SharePoint 伺服器陣列，請指定外部。若您只有內部 SharePoint 伺服器陣列，請指定內部。請只在使用 IPSEC 之完全安全的網路上 (完全加密)，或在不包含敏感性資料的測試環境中，才使用 HTTP。選項如下：</p>
<p>- Internal-HTTP</p>
<p>- Internal-HTTPS</p>
<p>- External-HTTP</p>
<p>- External-HTTPS</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>選用</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>以適當處理方式來管理物件。例如使用 <strong>SPWeb</strong> 或 <strong>SPSite</strong> 物件時可能會使用大量記憶體，在 Windows PowerShell 指令碼中使用這些物件時需要適當的記憶體管理。透過使用 <strong>SPAssignment</strong> 物件，您可以在物件需要用來釋放記憶體時，將物件指派給變數及捨棄物件。使用 <strong>SPWeb</strong>、<strong>SPSite</strong> 或 <strong>SPSiteAdministration</strong> 物件時，如果不使用指派集合或 <strong>Global</strong> 參數，則物件會自動遭到捨棄。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>使用 <strong>Global</strong> 參數時，所有物件都會都包含在全域存放區。如果物件不會立即使用，或使用 <strong>Stop-SPAssignment</strong> 命令加以捨棄，則會發生記憶體不足的狀況。</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>顯示訊息會描述命令的功效而不執行命令。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\--------------範例-----------------

    Set-SPWOPIZone -Zone "external-https"

此範例會設定目前之 SharePoint 伺服器陣列透過 HTTPS 使用 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器) 的外部連線。

## 另請參閱


[Get-SPWOPIZone](get-spwopizone.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

