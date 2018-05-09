---
title: Update-SPWOPIProofKey
TOCTitle: Update-SPWOPIProofKey
ms:assetid: fe7f3a87-082e-4a43-a5f3-7be41d8e91a3
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219460(v=office.15)
ms:contentKeyID: 49565166
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Update-SPWOPIProofKey

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2015-03-09_

更新用於連線到此 Cmdlet 目前執行所在之 SharePoint 伺服器陣列的 WOPI 應用程式的公開金鑰。

## 語法

    Update-SPWOPIProofKey [-AssignmentCollection <SPAssignmentCollection>] [-ServerName <String>]

## 詳細描述

**Update-SPWOPIProofKey** Cmdlet 會更新用於連線到此 Cmdlet 目前執行所在之 SharePoint 伺服器陣列的 WOPI 應用程式 (可能是執行 Office Web Apps Server的伺服器) 的公開金鑰。當 SharePoint 伺服器陣列與 WOPI 應用程式之間的金鑰不同步時，即可使用此 Cmdlet。當金鑰處於不同步的狀況時，不僅無法在瀏覽器中開啟文件，統一登入系統 (ULS) 記錄中還會出現「檔案的證明簽章無效...」或「資料夾的證明簽章無效...」等訊息。

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
<td><p><strong>ServerName</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定 WOPI 應用程式取得金鑰來源。此來源或許是執行 Office Web Apps Server的伺服器。若缺少此參數，所有 WOPI 應用程式用於連線至目前之 SharePoint 伺服器陣列的公用金鑰皆會更新。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\--------------範例-----------------

    Update-SPWOPIProofKey -ServerName "Server.corp.Contoso.com"

此範例會從 WOPI 應用程式 (例如執行 Office Web Apps Server的伺服器) 取得目前的公開金鑰，並更新要儲存在 SharePoint 伺服器陣列上的金鑰。

## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[搭配並用 Office Web Apps 與 SharePoint 2013](use-office-web-apps-with-sharepoint-2013.md)

