---
title: Remove-SPWOPISuppressionSetting
TOCTitle: Remove-SPWOPISuppressionSetting
ms:assetid: cbaef5a8-e682-4166-be44-15ab1c79acca
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219452(v=office.15)
ms:contentKeyID: 49565142
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPISuppressionSetting

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除副檔名或程式設計識別碼以及動作的隱藏設定。

## 語法

    Remove-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPISuppressionSetting [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Identity <String>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Remove-SPWOPISuppressionSetting** Cmdlet 可從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除副檔名或程式設計識別碼 (ProgID) 以及動作的隱藏設定。

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
<td><p>指定給定副檔名或程式設計識別碼 (ProgId) 的動作。例如，“view”、“edit” 及 “embedview”。</p></td>
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

</div>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。。</p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定副檔名。執行 Get-SPWOPIBinding 可取得 WOPI 應用程式支援的副檔名清單。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Identity</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定代表 SPWOPISuppressionSetting 的字串。執行 Get-SPWOPISuppressionSetting 可查看此類字串的範例。</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要隱藏之應用程式的程式設計識別碼 (ProgID)。執行 Get-SPWOPIBinding 可取得 WOPI 應用程式支援的 ProgID 清單。</p></td>
</tr>
<tr class="odd">
<td><p><strong>WhatIf</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>顯示訊息會描述命令的功效而不執行命令。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\--------------範例 1-----------------

    Remove-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

此範例會移除隱藏設定，以檢視副檔名為 “.xlsx” 的 Excel 活頁簿。

\--------------範例 2-----------------

    Get-SPWOPISuppressionSetting | Remove-SPWOPISuppressionSetting

此範例會從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除所有隱藏設定。

## 另請參閱


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

