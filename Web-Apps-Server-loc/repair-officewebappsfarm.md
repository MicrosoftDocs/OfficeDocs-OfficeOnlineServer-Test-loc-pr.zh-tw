---
title: Repair-OfficeWebAppsFarm
TOCTitle: Repair-OfficeWebAppsFarm
ms:assetid: 083d8e25-ce82-4884-9bbc-06375185011c
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219433(v=office.15)
ms:contentKeyID: 49565092
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Repair-OfficeWebAppsFarm

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-09_

移除 Office Web Apps Server 伺服器陣列中所有標示為不健康的伺服器。

## 語法

    Repair-OfficeWebAppsFarm [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**Repair-OfficeWebAppsFarm** Cmdlet 會移除 Office Web Apps Server 伺服器陣列中所有標示為不健康的伺服器。此 Cmdlet 只會更新伺服器陣列拓撲，而不會清理所移除之伺服器上的服務或 Web 應用程式。因此建議您從不健康的伺服器上執行 **Remove-OfficeWebAppsMachine** Cmdlet，以從伺服器陣列徹底移除這些伺服器。請只在不健康的伺服器失敗，導致無法直接由其上執行 **Remove-OfficeWebAppsMachine** Cmdlet 時，才使用 **Repair-OfficeWebAppsFarm** Cmdlet。

如有多部不健康的伺服器，將會在移除每部伺服器前提示您。若無不健康的伺服器，此 Cmdlet 將不會採取任何動作。

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
<td><p><strong>Force</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>假設所有使用者提示的回答皆為「是」。</p></td>
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

    (Get-OfficeWebAppsFarm).Machines

此範例會顯示 Office Web Apps Server伺服器陣列中所有伺服器的健康狀態。

\------------------範例 2---------------------

    Repair-OfficeWebAppsFarm

此範例會移除 Office Web Apps Server伺服器陣列中所有不健康的伺服器。

## 另請參閱


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

