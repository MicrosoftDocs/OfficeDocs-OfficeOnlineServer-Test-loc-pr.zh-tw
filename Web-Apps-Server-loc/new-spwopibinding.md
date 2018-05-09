---
title: New-SPWOPIBinding
TOCTitle: New-SPWOPIBinding
ms:assetid: 696f01b4-a144-431b-9bae-1c3ede78609d
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219441(v=office.15)
ms:contentKeyID: 49565108
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPIBinding

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

在目前執行此 Cmdlet 的 SharePoint 伺服器陣列上，建立新繫結以將副檔名或應用程式關聯至動作。

## 語法

    New-SPWOPIBinding -ServerName <String> [-Action <String>] [-AllowHTTP <SwitchParameter>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-FileName <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**New-SPWOPIBinding** Cmdlet 可在目前執行此 Cmdlet 的 SharePoint 伺服器陣列上，建立新繫結以將副檔名或應用程式關聯至動作。每個繫結都可讓您使用 WOPI 應用程式檢視或編輯 SharePoint 文件庫中的檔案。例如，當使用者使用 SharePoint 文件清單中的 Word 文件時，SharePoint 清單會根據該 SharePoint 伺服器陣列上之 Word 所繫結的動作，顯示可檢視或編輯文件的選項。

若要針對 Office Web Apps 使用 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器)，必須對 SharePoint 伺服器陣列執行此 Cmdlet，才可以使用 Office Web Apps。

若您針對已經存在繫結 (或關聯) 的應用程式或副檔名執行 **New-SPWOPIBinding**，此 Cmdlet 會失敗。

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
<td><p><strong>ServerName</strong></p></td>
<td><p>必要</p></td>
<td><p>System.String</p></td>
<td><p>指定 WOPI 應用程式 (例如執行 Office Web Apps Server 的伺服器) 的名稱或完整網域名稱 (FQDN)。</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要繫結的動作。例如，“view”、“edit” 及 “embedview”。如需 WOPI 應用程式支援的動作清單，請執行 <strong>Get-SPWOPIBinding</strong>。一般而言，您不會使用此參數。若您指定部分動作 (但未包括其他動作)，則 SharePoint 的某些功能可能無法運作。</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHTTP</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>指定此 Cmdlet 可以使用 HTTP 探索 WOPI 應用程式支援的項目。若其指定為 True，則會透過不安全的連線從 WOPI 應用程式傳送探索資訊。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要繫結的應用程式。可能的應用程式如下：“Word&quot;、“Excel&quot;、“PowerPoint&quot; 或 “OneNote&quot;。執行 <strong>Get-SPWOPIBinding</strong> 可取得 WOPI 應用程式支援的完整應用程式清單。</p></td>
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
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要繫結的副檔名。執行 <strong>Get-SPWOPIBinding</strong> 可取得 WOPI 應用程式支援的副檔名清單。</p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定包含 WOPI 應用程式之探索資訊的 xml 檔案路徑。您可以從 xml 檔案載入探索資訊，而不需直接向 WOPI 應用程式要求。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要繫結之應用程式的程式設計識別碼 (ProgID)。執行 <strong>Get-SPWOPIBinding</strong> 可取得 WOPI 應用程式支援的 ProgID 清單。您可能只想使用此參數將動作關聯至 OneNote 資料夾。</p></td>
</tr>
<tr class="even">
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

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com"

此範例會在目前執行此 Cmdlet 的 SharePoint 伺服器陣列上，建立 WOPI 應用程式支援之所有應用程式與副檔名的繫結。

\--------------範例 2-----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com" -Application "Excel"

此範例會在目前執行此 Cmdlet 的 SharePoint 伺服器陣列上，將 Excel 關聯至 WOPI 應用程式支援 Excel 的所有動作。

## 另請參閱


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

