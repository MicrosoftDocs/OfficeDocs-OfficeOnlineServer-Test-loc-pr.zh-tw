---
title: New-OfficeWebAppsMachine
TOCTitle: New-OfficeWebAppsMachine
ms:assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219449(v=office.15)
ms:contentKeyID: 49565130
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsMachine

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

將目前的伺服器加入現有的 Office Web Apps Server伺服器陣列。

## 語法

    New-OfficeWebAppsMachine [-MachineToJoin] <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**New-OfficeWebAppsMachine** Cmdlet 會將目前的伺服器加入現有的 Office Web Apps Server伺服器陣列，並視情況為新伺服器設定一或多個角色。

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
<td><p><strong>MachineToJoin</strong></p></td>
<td><p>必要</p></td>
<td><p>System.String</p></td>
<td><p>指定 Office Web Apps Server伺服器陣列之成員伺服器的名稱。</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>假設所有使用者提示的回答皆為「是」。</p></td>
</tr>
<tr class="even">
<td><p><strong>Roles</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String[]</p></td>
<td><p>指定一或多個伺服器角色 (以逗號分隔)，將其指派給新的伺服器。若未指定任何角色，將會指派以全部的角色。</p>
<p>這些角色類型包括：</p>
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

\------------------範例 1---------------------

    New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com

此範例會將目前的伺服器加入名稱為 server1.contoso.com 之伺服器上所執行的 Office Web Apps Server伺服器陣列。

## 另請參閱


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

