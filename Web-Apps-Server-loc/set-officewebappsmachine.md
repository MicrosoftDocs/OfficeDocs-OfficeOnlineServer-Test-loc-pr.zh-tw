---
title: Set-OfficeWebAppsMachine
TOCTitle: Set-OfficeWebAppsMachine
ms:assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219448(v=office.15)
ms:contentKeyID: 49565129
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsMachine

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

變更 Office Web Apps Server 伺服器陣列中之目前伺服器的設定。

## 語法

    Set-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-Master <String>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Set-OfficeWebAppsMachine** Cmdlet 會變更 Office Web Apps Server伺服器陣列中之目前伺服器的設定，包括目前伺服器所具有的角色，以及伺服器陣列中所指定的主要伺服器。

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
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>Master</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p></p>
<p>指定儲存主要伺服器陣列設定檔的伺服器。</p>
<p>若將本機伺服器設為主要伺服器，必須在 Office Web Apps Server伺服器陣列中的所有其他伺服器上執行 <strong>Set-OfficeWebAppsMachine -Master</strong>，以將其指向新的主要伺服器。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Roles</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String[]</p></td>
<td><p>指定要指派給本機伺服器之伺服器角色的清單 (以逗號分隔)。</p>
<p>這些角色類型包括：</p>
<p><strong>All</strong></p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>建議的最佳作法是讓 Office Web Apps Server伺服器陣列中的每部伺服器皆執行所有的角色。當 Office Web Apps Server伺服器中的伺服器數量不及 50 部時，指派角色並無太大用場。</td>
</tr>
</tbody>
</table>

</div></td>
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

    (Get-OfficeWebAppsFarm).Machines

此範例會顯示 Office Web Apps Server伺服器陣列中之每部伺服器所具有的角色。

\------------------範例 2---------------------

    Set-OfficeWebAppsMachine -Roles FrontEnd

此範例會將目前的伺服器設為前端伺服器。

\------------------範例 3---------------------

    Set-OfficeWebAppsMachine -Roles All

此範例會將目前的伺服器設定為執行所有角色。

## 另請參閱


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

