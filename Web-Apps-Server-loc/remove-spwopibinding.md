---
title: Remove-SPWOPIBinding
TOCTitle: Remove-SPWOPIBinding
ms:assetid: 52855c21-ee2c-497a-b308-bf5eeabe4bbe
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219438(v=office.15)
ms:contentKeyID: 49565102
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPIBinding

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除應用程式、副檔名及其相關聯動作的繫結。

## 語法

    Remove-SPWOPIBinding [[-Identity] <SPWopiBindingPipeBind>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WhatIf [<SwitchParameter>]] [-WOPIZone <String>]

    Remove-SPWOPIBinding [-All <SwitchParameter>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Remove-SPWOPIBinding** Cmdlet 可從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除應用程式、副檔名及其相關聯動作的繫結。執行此 Cmdlet 之後，即可使用 **New-SPWOPIBinding** 視需要重新建立繫結。若您移除應用程式的所有繫結，使用者將無法針對該應用程式使用 Office Web Apps 或 SharePoint 的 \[共用連結\] 功能。若您從執行此 Cmdlet 的 SharePoint 伺服器陣列中移除所有繫結，使用者將無法針對 SharePoint 文件庫中的任何應用程式，使用 Office Web Apps 或 SharePoint 的 \[共用連結\] 功能。

若您想停止使用 Office Web Apps 做為預設按鍵動作，但是必須保留繫結的探索資訊，以及使用者可使用 SharePoint 的 \[共用連結\] 功能傳送連結至文件的能力，並允許收件者針對該文件類型使用 Office Web Apps，請改用 **New-SPWOPISuppression** Cmdlet。

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
<td><p><strong>Identity</strong></p></td>
<td><p>選用</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>指定繫結。</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結的動作。例如，“view&quot;、“edit&quot; 及 “embedview&quot;。如需動作清單，請執行 <strong>Get-SPWOPIBinding</strong>。一般而言，您不會使用此參數。若您指定部分動作 (但未包括其他動作)，則 SharePoint 的某些功能可能無法運作。</p></td>
</tr>
<tr class="odd">
<td><p><strong>All</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>移除所有繫結。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結的應用程式。可能的應用程式如下：“Word&quot;、“Excel&quot;、“PowerPoint&quot; 或 “OneNote&quot;。執行 <strong>Get-SPWOPIBinding</strong> 可取得應用程式清單。</p></td>
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
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結的副檔名。執行 <strong>Get-SPWOPIBinding</strong> 可取得副檔名清單。</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結之應用程式的程式設計識別碼 (ProgID)。執行 <strong>Get-SPWOPIBinding</strong> 可取得 ProgID 清單。您可能只想使用此參數移除 OneNote 的繫結。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結之 WOPI 應用程式 (例如 Office Web Apps Server) 的名稱。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>顯示訊息會描述命令的功效而不執行命令。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要移除繫結的區域。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\--------------範例 1-----------------

    Remove-SPWOPIBinding -Application "Excel"

此範例會從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除 Excel 的所有繫結。

\--------------範例 2-----------------

    Remove-SPWOPIBinding -All:$true

此範例會從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除所有繫結。

\--------------範例 3-----------------

    Get-SPWOPIBinding -Action "MobileView" | Remove-SPWOPIBinding

此範例會從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除 Office Mobile Web Apps 的所有繫結。

## 另請參閱


[New-SPWOPIBinding](new-spwopibinding.md)  
[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

