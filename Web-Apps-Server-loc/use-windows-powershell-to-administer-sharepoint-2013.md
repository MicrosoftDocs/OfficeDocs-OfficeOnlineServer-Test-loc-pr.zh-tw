---
title: 使用 Windows Powershell 管理 SharePoint 2013
TOCTitle: 使用 Windows Powershell 管理 SharePoint 2013
ms:assetid: ae4901b4-505a-42a9-b8d4-fca778abc12e
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Ee806878(v=office.15)
ms:contentKeyID: 49565127
ms.date: 03/01/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# 使用 Windows Powershell 管理 SharePoint 2013

 

_**適用版本：**SharePoint Foundation 2013, SharePoint Server 2013 Enterprise, SharePoint Server 2013 Standard_

_**上次修改主題的時間：**2016-12-16_

**摘要：**了解基本的 Windows PowerShell Cmdlet 與概念，並了解如何將 Windows PowerShell 與 SharePoint 2013 搭配使用。

本文內容：

  - 概觀

  - 存取 Windows PowerShell 來管理 SharePoint 2013 產品

  - 權限

  - 指令碼和執行原則

  - 瞭解 Windows PowerShell

## 概觀

Windows PowerShell 為命令列命令介面和指令碼語言，可對管理員提供適當之應用程式開發介面 (API) 的完整存取權。管理員可以直接與 SharePoint 2013 互動，操作 Web 應用程式、網站集合、網站、清單等。此外，管理員還可以撰寫 Cmdlet (發音為 "command-lets") 指令碼。

Windows PowerShell 3.0 是安裝 SharePoint 2013 的先決條件。如果尚未安裝此程式，將會在您執行 Microsoft SharePoint 產品準備工具 時安裝。Windows PowerShell 預設位於下列路徑：\<%SystemRoot%\>\\System32\\WindowsPowerShell\\v1.0\\PowerShell.exe。

如需 Windows PowerShell 3.0 新功能的清單，請參閱＜[Windows Management Framework 3.0](http://go.microsoft.com/fwlink/p/?linkid=272782)＞

如需協助您了解 Windows PowerShell 語法的互動式工具和指南，請參閱＜[Windows PowerShell 命令建立工具](http://go.microsoft.com/fwlink/p/?linkid=229854)＞和＜[快速入門指南](http://www.microsoft.com/download/en/details.aspx?id=27588)＞。

我們建議您在執行命令列管理工作時使用 Windows PowerShell。Stsadm 命令列工具雖已被取代，但依然涵蓋在內，這是為了與先前的產品版本相容。

## 存取 SharePoint 2013 的 Windows PowerShell

安裝 SharePoint 2013 之後，SharePoint 2013 管理命令介面 中會提供可用的 Windows PowerShell Cmdlet。您可以管理 SharePoint Management Shell 中 SharePoint 2013 的各個層面。您可以建立新的網站集合、Web 應用程式、使用者帳戶、服務應用程式、Proxy 等等。您在 SharePoint Management Shell 中輸入的命令會傳回以 Microsoft .NET Framework 為基礎的 SharePoint 物件。您可以將這些物件視為後續命令的輸入，或將物件儲存於本機變數內以供稍後使用。

使用 SharePoint Management Shell，您就不必登錄包含 Cmdlet 的嵌入式管理單元。位於 *%CommonProgramFiles%*\\Microsoft Shared\\Web Server Extensions\\15\\Config\\PowerShell\\Registration 中的 SharePoint.ps1 檔案，其中的 `Add-PSSnapin Microsoft.SharePoint.PowerShell` 一行會自動登錄 SharePoint 2013 的 Microsoft.SharePoint.PowerShell.dll 模組。若要使用 Windows PowerShell 主控台，您必須手動登錄此嵌入式管理單元。

無論您使用 SharePoint Management Shell 或 Windows PowerShell 主控台，您都可以載入其他嵌入式管理單元。如需詳細資訊，請參閱＜[Windows PowerShell：設定檔的威力](http://go.microsoft.com/fwlink/p/?linkid=183166)＞。

存取 SharePoint Management Shell

1.  啟動 SharePoint Management Shell。
    
      - 若為 Windows Server 2008 R2：
        
          - 依序按一下 \[開始\]、\[Microsoft SharePoint 2013 產品\] 和 \[SharePoint Management Shell\]。
    
      - 若為 Windows Server 2012：
        
          - 在 \[開始\] 畫面上，按一下 \[SharePoint Management Shell\]。
            
            若 \[SharePoint Management Shell\] 不在 \[開始\] 畫面上：
        
        <!-- end list -->
        
          - 在 \[電腦\] 上按一下滑鼠右鍵，按一下 \[所有應用程式\]，然後按一下 \[SharePoint Management Shell\]。
    
    如需如何與Windows Server 2012互動的詳細資訊，請參閱 ＜[常見管理工作及 Windows Server 2012 中的導覽](http://technet.microsoft.com/en-us/library/hh831491.aspx)。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SharePoint 2013 管理命令介面與 Windows PowerShell 主控台使用 <code>ReuseThread</code> 選項的方式也不相同，此選項可定義使用執行緒模式的方式。SharePoint.ps1 檔案中的 <code>{Host.Runspace.ThreadOptions = &quot;ReuseThread&quot;}</code> 一行定義了 SharePoint 2013 管理命令介面的用法。如需詳細資訊，請參閱＜<a href="http://go.microsoft.com/fwlink/p/?linkid=183145">PSThreadOptions 列舉</a>＞。</td>
</tr>
</tbody>
</table>


## 權限

## 內部部署

在您可以使用 **Add-SPShellAdmin** Cmdlet 以授權使用者執行 SharePoint 2013 Cmdlet 之前，請先確認您符合以下所有最低需求：

  - 您必須具有 SQL Server 執行個體上 **securityadmin** 固定伺服器角色中的成員資格

  - 您必須具備所有待更新資料庫之 **db\_owner** 固定資料庫角色中的成員資格。

  - 您必須是正在執行 Windows PowerShell Cmdlet 之伺服器上的管理員群組成員。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果未符合這些權限，請連絡設定管理員或 SQL Server 管理員以要求這些權限。</td>
</tr>
</tbody>
</table>


如需 Windows PowerShell 權限的其他資訊，請參閱＜權限＞和＜[Add-SPShellAdmin](https://technet.microsoft.com/zh-tw/library/ff607596\(v=office.15\))＞

如果您不具備 **SharePoint\_Shell\_Access** 角色或 **WSS\_Admin\_WPG** 本機群組中的成員資格，請使用 **Add-SPShellAdmin** Cmdlet 以在 SharePoint 伺服器陣列中的所有前端網頁伺服器中新增 **WSS\_Admin\_WPG** 群組和 **SharePoint\_Shell\_Access** 角色。如果 SQL Server 資料庫不具備 **SharePoint\_Shell\_Access** 角色，則會在執行 **Add-SPShellAdmin** Cmdlet 時，自動建立角色。執行 **Add-SPShellAdmin** Cmdlet 之後，使用者可以在多部伺服器陣列環境中執行 SharePoint Windows PowerShell Cmdlet。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>安裝 SharePoint 2013 時，執行安裝所使用的使用者帳戶會授與適當權限以執行 Windows PowerShell Cmdlet。如果未新增任何使用者執行 Windows PowerShell Cmdlet，您可以使用 <strong>Add-SPShellAdmin</strong> Cmdlet 以新增使用者。</td>
</tr>
</tbody>
</table>


您必須對所有要授與存取權的資料庫執行 **Add-SPShellAdmin** Cmdlet。 如果未指定資料庫，就會使用伺服器陣列設定資料庫。如果有指定資料庫，除了您指定的伺服器陣列設定資料庫之外，還會包括伺服器陣列內容資料庫。

若要查看所有 **SPShellAdmin** Cmdlet 的清單，請從 Windows PowerShell 命令提示字元輸入 `Get-Command -Noun SPShellAdmin`。

## SharePoint Online

確認您具備下列管理權限：

  - 在您執行 Windows PowerShell Cmdlet 的 SharePoint Online 網站上，您必須獲指派為全域管理員角色。如需詳細資訊，請參閱＜[預設系統管理角色和使用者群組](http://go.microsoft.com/fwlink/p/?linkid=242451)＞。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /> <strong>重要事項：</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>您可以使用含 SharePoint Online 之 Windows PowerShell 的特定群組。如需詳細資訊，請參閱＜<a href="https://technet.microsoft.com/zh-tw/library/fp161362(v=office.15)">適用於 SharePoint Online 的 office 365 PowerShell</a>＞。</td>
    </tr>
    </tbody>
    </table>


## 指令碼和執行原則

雖然您可以使用 Windows PowerShell 執行單一管理工作，但是您也可以使用指令碼來自動化一系列的工作。指令碼是含有一個或多個 Windows PowerShell 命令的純文字檔。Windows PowerShell 指令碼的副檔名是 .ps1。

若要執行指令碼，SharePoint 2013 的最小必要執行原則為 RemoteSigned，但 Windows PowerShell 的預設原則為 Restricted。如果將原則保留在 Restricted，則 SharePoint 2013 管理命令介面會將 Windows PowerShell 的原則變更為 RemoteSigned。這表示您必須選取 \[以系統管理員身分執行\]，以提高的管理權限來啟動 SharePoint 2013 管理命令介面。這項變更會套用至所有 Windows PowerShell 工作階段。如需詳細資訊，請參閱＜[ExecutionPolicy 列舉](http://go.microsoft.com/fwlink/p/?linkid=242452)＞。

如需指令碼和執行原則的詳細資訊，請分別參閱＜[about\_scripts](http://go.microsoft.com/fwlink/p/?linkid=144310)＞和＜[about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)＞。

## 了解 Windows PowerShell

SharePoint IT 人員有數種 Windows PowerShell 學習資源可以使用。

**TechNet 指令碼中心**

TechNet 指令碼中心內含許多可協助您學習關於 Windows PowerShell 基本技巧的資源。其中包含的指令碼存放庫提供可搭配各種不同 Microsoft 產品的常用指令碼範例。下表顯示主要的學習資源。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>頁面</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187813">TechNet 上的 Windows PowerShell 文件</a></p></td>
<td><p>此部分的 TechNet Library 包含核心 Windows PowerShell Get-Help 主題的網頁。此部分也內含 Windows PowerShell 快速入門文件、PowerShell.exe 說明以及 Windows PowerShell 入門的網頁。</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187815">使用 Windows PowerShell 撰寫指令碼</a></p></td>
<td><p>Windows PowerShell 指令碼撰寫學習資源的首頁。</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187817">Windows PowerShell 擁有人的手冊</a></p></td>
<td><p>Windows PowerShell 快速入門的網頁指南。</p></td>
</tr>
<tr class="even">
<td><p><a href="http://go.microsoft.com/fwlink/p/?linkid=187819">Windows PowerShell 快速參考</a></p></td>
<td><p>可下載的快速參考文件，可隨 Windows PowerShell 一起安裝。</p></td>
</tr>
</tbody>
</table>


閱讀這些資源時請注意，下列概念與 Cmdlet 是對 SharePoint 2013 使用 Windows PowerShell 前可暸解的實用資訊：

  - [Get-Command](http://go.microsoft.com/fwlink/p/?linkid=171069)

  - [Get-Member](http://go.microsoft.com/fwlink/p/?linkid=171070)

  - [Get-Help](http://go.microsoft.com/fwlink/p/?linkid=171068)

  - [別名](http://go.microsoft.com/fwlink/p/?linkid=113207)

  - [Windows PowerShell 中的管線與管道](http://go.microsoft.com/fwlink/p/?linkid=187808)

  - [Cmdlet 參數集](http://go.microsoft.com/fwlink/p/?linkid=187810)

  - [Foreach-Object](http://go.microsoft.com/fwlink/p/?linkid=187812)

  - [Where-Object](http://go.microsoft.com/fwlink/p/?linkid=187811)

