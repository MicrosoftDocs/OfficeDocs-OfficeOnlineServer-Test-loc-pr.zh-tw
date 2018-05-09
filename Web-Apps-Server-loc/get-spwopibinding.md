---
title: Get-SPWOPIBinding
TOCTitle: Get-SPWOPIBinding
ms:assetid: b757301b-f6c5-43a5-a8ca-2ef33ede0ae8
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219450(v=office.15)
ms:contentKeyID: 49565131
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-SPWOPIBinding

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

傳回在目前執行此 Cmdlet 之 SharePoint 伺服器陣列上使用 **New-SPWOPIBinding** 建立的繫結清單。

## 語法

    Get-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WOPIZone <String>]

## 詳細描述

**Get-SPWOPIBinding** 可傳回在目前執行此 Cmdlet 之 SharePoint 伺服器陣列上使用 **New-SPWOPIBinding** 建立的繫結清單。結果包括為 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器) 設定的動作、應用程式、檔案類型及區域。

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
<th>說明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Action</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結的動作。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結的應用程式。</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結的副檔名。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結之應用程式的程式設計識別碼 (ProgID)。</p></td>
</tr>
<tr class="even">
<td><p><strong>Server</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結之 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器) 的名稱。</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要傳回繫結的區域。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\--------------範例 1-----------------

    Get-SPWOPIBinding -Server "Server.corp.Contoso.com"

此範例會傳回繫結清單，而這些繫結的建立對象，是此 Cmdlet 針對 WOPI 應用程式 "Server.corp.Contoso.com" 執行所在的 SharePoint 伺服器陣列。WOPI 應用程式可以是執行 Office Web Apps Server 的伺服器。

\--------------範例 2-----------------

    Get-SPWOPIZone | Get-SPWOPIBinding

此範例會傳回繫結清單，而這些繫結的建立對象，是此 Cmdlet 針對 WOPI 應用程式的設定區域執行所在的 SharePoint 伺服器陣列。

## 另請參閱


[New-SPWOPIBinding](new-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

