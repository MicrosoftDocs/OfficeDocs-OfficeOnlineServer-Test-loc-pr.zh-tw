---
title: New-SPWOPISuppressionSetting
TOCTitle: New-SPWOPISuppressionSetting
ms:assetid: 7e6bb8f5-3124-4568-80c6-02cae46b803b
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219443(v=office.15)
ms:contentKeyID: 49565112
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPISuppressionSetting

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

**New-SPWOPISuppressionSetting** Cmdlet 可針對您在目前 SharePoint 伺服器陣列上指定的動作、副檔名或程式設計識別碼，關閉 Office Web Apps。

## 語法

    New-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**New-SPWOPISuppressionSetting** Cmdlet 可針對您在目前 SharePoint 伺服器陣列上指定的動作、副檔名或程式設計識別碼 (ProgId)，關閉 Office Web Apps。此 Cmdlet 執行這項操作時，不需要移除探索資訊，或使用者使用 SharePoint 的 \[共用連結\] 功能傳送連結至文件的能力，並允許收件者針對該文件類型使用 Office Web Apps。若您想使用 Excel Services 檢視 Excel 活頁簿，而不是 WOPI 應用程式 (例如 Office Web Apps Server)，則可能必須使用此 Cmdlet。

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
<td><p><strong>Action</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定隱藏給定副檔名或程式設計識別碼 (ProgId) 的動作。例如，“view”、“edit” 及 “embedview”。如需完整的動作清單，請執行 <strong>Get-SPWOPIBinding</strong>。</p></td>
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
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要隱藏的副檔名。執行 Get-SPWOPIBinding 可取得 WOPI 應用程式支援的副檔名清單。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要隱藏之應用程式的程式設計識別碼 (ProgId)。執行 Get-SPWOPIBinding 可取得 WOPI 應用程式支援的 ProgId 清單。</p></td>
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

\--------------範例 1-----------------

    New-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

    New-SPWOPISuppressionSetting -Extension "XLS" -Action "view"

此範例會關閉使用者使用 Office Web Apps 檢視副檔名為 “.xlsx” 或 “.xls” 之 Excel 活頁簿的功能。

## 另請參閱


[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

