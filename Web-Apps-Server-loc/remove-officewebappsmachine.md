---
title: Remove-OfficeWebAppsMachine
TOCTitle: Remove-OfficeWebAppsMachine
ms:assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219440(v=office.15)
ms:contentKeyID: 49565107
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsMachine

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

從 Office Web Apps Server伺服器陣列中移除目前的伺服器。

## 語法

    Remove-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Remove-OfficeWebAppsMachine** Cmdlet 會從 Office Web Apps Server伺服器陣列中移除目前的伺服器。除此之外還會一併移 Web 應用程式並關閉所有和 Office Web Apps Server相關的服務。若無法從所要移除的伺服器上執行 **Remove-OfficeWebAppsMachine** Cmdlet，可改從 Office Web Apps 伺服器陣列中的其他任意伺服器上執行 **Repair-OfficeWebAppsFarm** Cmdlet。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>若本機伺服器被指定為 Office Web Apps Server伺服器陣列的主要伺服器，除非先使用 <strong>Set-OfficeWebAppsMachine</strong> Cmdlet 指定其他伺服器，或先移除伺服器陣列中的其他所有伺服器，否則將無法從伺服器陣列中移除本機伺服器。</td>
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
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
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

\------------------範例 1---------------------

    Remove-OfficeWebAppsMachine

此範例會從 Office Web Apps Server伺服器陣列中移除目前的伺服器。

## 另請參閱


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

