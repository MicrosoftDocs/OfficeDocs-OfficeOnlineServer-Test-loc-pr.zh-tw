---
title: 設定供瀏覽器使用之文件的預設開啟行為 (搭配 SharePoint 2013 使用時為 Office Web Apps)
TOCTitle: 設定供瀏覽器使用之文件的預設開啟行為
ms:assetid: e27e0bc8-5fb5-4bb1-8157-d7c90654175e
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Ee837425(v=office.15)
ms:contentKeyID: 50181138
ms.date: 05/27/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 設定供瀏覽器使用之文件的預設開啟行為 (搭配 SharePoint 2013 使用時為 Office Web Apps)

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**說明如何為 SharePoint 網站集合和文件庫中的 Office 文件設定預設開啟行為

**對象：**IT 專業人員

若要開啟 SharePoint 2013 文件庫中的文件，只要按一下文件的標題即可。接下來發生的情況 (在用戶端應用程式或瀏覽器中開啟檔案) 取決於多種因素，例如檔案類型、設定 Office Web Apps Server 伺服器陣列的方式，以及文件庫或網站集合的 OpenInClient 功能的設定方式。下列步驟顯示如何在將 SharePoint 2013 設定為使用 Office Web Apps Server 的 Office 上設定文件的預設開啟行為。

## 設定從 SharePoint 2013 文件庫開啟文件的方式

根據預設，將 SharePoint 2013 設定為使用 Office Web Apps Server 之後，按一下 Word、PowerPoint、Excel 或 OneNote 檔案就會在瀏覽器中開啟該檔案。PDF 文件會在 Word Web App 中開啟。有兩種方法可以變更此預設行為，以便改為在用戶端應用程式 (或預設的 PDF 閱讀程式) 開啟檔案：

  - **若是 SharePoint 2013 伺服器陣列**   您可以使用 [New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps) 和 [Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps)Windows PowerShell Cmdlet，依照每個檔案類型為 SharePoint 2013 伺服器陣列調整預設開啟行為。這些 Cmdlet 也可用來[調整 PDF 文件的行為](http://go.microsoft.com/fwlink/p/?linkid=330246)。

  - **在網站集合或文件庫中**   網站集合管理員和使用者可以使用 SharePoint 2013 中的 OpenInClient 功能指定要在用戶端應用程式或瀏覽器中開啟 Office 檔案。使用者可以在文件庫內容中變更此設定，而網站集合管理員則可以在網站集合管理中變更此設定，或是使用 [Enable-SPFeature](https://technet.microsoft.com/zh-tw/library/ff607803\(v=office.15\)) Cmdlet 啟用 OpenInClient 功能。關於啟用 OpenInClient 功能的幾種不同的方法，請參閱下一節。

一般而言，OpenInClient 功能會覆寫您在 SharePoint 2013 與 Office Web Apps Server 之間設定的所有 WOPI 繫結。換句話說，如果啟用 SharePoint 2013 文件庫或網站集合的 OpenInClient 功能，將會在用戶端應用程式中開啟文件，即使您已經設定 SharePoint 2013 伺服器使用 Office Web Apps Server 也是如此。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>針對供瀏覽器使用的文件設定預設開啟行為，並不影響使用者是否能夠使用 SharePoint 2013 的 [簽出] 和 [傳送到] 功能來下載文件。如需如何在 SharePoint 2013 中設定簽出、下載及檢視權限的詳細資訊，請參閱 <a href="https://technet.microsoft.com/zh-tw/library/cc262939(v=office.15)">在 SharePoint 2013 中規劃網站及內容的權限</a>。</td>
</tr>
</tbody>
</table>


## 為文件庫或網站集合設定 OpenInClient 功能

使用下列其中一個程序設定 SharePoint 2013 中的 OpenInClient 功能。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>本文中的某些程序使用 SharePoint 2013 管理命令介面執行 SharePoint Cmdlet。如果您選擇使用 Windows PowerShell 主控台，則必須使用 <strong>Add-PSSnapin</strong> Cmdlet 新增 Microsoft.SharePoint.PowerShell 嵌入式管理單元。如需 Windows PowerShell 與 SharePoint 2013 如何搭配使用的詳細資訊，請參閱<a href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">使用 Windows Powershell 管理 SharePoint 2013</a>。</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>您可以使用滑鼠、鍵盤快速鍵或觸控等方式完成所有 Office 2013 套裝軟體 中的工作。如需如何使用 Office 產品與服務中的鍵盤快速鍵和觸控功能的詳細資訊，請參閱<a href="http://go.microsoft.com/fwlink/p/?linkid=249150">鍵盤快速鍵</a>與<a href="http://go.microsoft.com/fwlink/p/?linkid=253163">Office 觸控指南</a>。</td>
</tr>
</tbody>
</table>


 **設定網站集合的 OpenInClient 功能**

1.  在 SharePoint 網站集合中，選擇 \[設定\] 圖示 \> \[網站設定\]。

2.  在 \[網站設定\] 頁面的 \[網站集合管理\] 下，選擇 \[網站集合功能\]。

3.  在 \[功能\] 頁面的 \[預設以用戶端應用程式開啟文件\] 功能中，選擇 \[啟動\] (OpenInClient 功能已啟用)，就會以用戶端應用程式開啟文件。選擇 \[停用\] (OpenInClient 功能已停用)，就會以瀏覽器開啟文件。

 **使用 Windows PowerShell 設定網站集合的預設開啟行為**

1.  首先，確認您具備下列成員資格：
    
      - SQL Server 執行個體上的 **securityadmin** 固定伺服器角色。
    
      - 待更新之所有資料庫上的 **db\_owner** 固定資料庫角色。
    
      - 正在執行 Windows PowerShell Cmdlet 之所在伺服器上的管理員群組。
    
    另外，請閱讀 [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)，並新增其他任何所需的成員資格。
    
    管理員可以使用 **Add-SPShellAdmin** Cmdlet 來授與使用 SharePoint 2013 Cmdlet 的權限。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>如果您沒有權限，請連絡安裝程式系統管理員或 SQL Server 系統管理員要求權限。如需 Windows PowerShell 權限的其他資訊，請參閱<a href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">權限</a>與 <a href="https://technet.microsoft.com/zh-tw/library/ff607596(v=office.15)">Add-SPShellAdmin</a>。</td>
    </tr>
    </tbody>
    </table>


2.  開啟已提升權限的 SharePoint 2013 管理命令介面：
    
    **在 Windows Server 2008 中**
    
    1.  在 \[開始\] 功能表上，選取 \[所有程式\]。
    
    2.  選取 **\[Microsoft SharePoint 2013 產品\]**。
    
    3.  選擇 \[SharePoint 2013 管理命令介面\]，並顯示捷徑功能表 (按一下滑鼠右鍵)。
    
    4.  從捷徑功能表中，選擇 \[以系統管理員身分執行\]。
    
    **在 Windows Server 2012 中**
    
    1.  從螢幕邊緣往內撥動以顯示圖標，並且選擇 \[搜尋\] 查看電腦上安裝的所有應用程式。
    
    2.  選擇 (以滑鼠右鍵按一下) **\[SharePoint 2013 管理命令介面\]** 以顯示應用程式列。
    
    3.  在應用程式列中，選取 **\[以系統管理員身分執行\]**。

3.  在 Windows PowerShell 命令提示字元中，輸入下列其中一個命令：
    
      - 若要啟用特定網站集合 (在用戶端應用程式中開啟文件) 的 OpenInClient 功能，輸入下列命令：
        
            Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        其中 *\<SiteCollURL\>* 是網站集合的 URL。
    
      - 若要啟用所有網站集合 (在用戶端應用程式中開啟文件) 的 OpenInClient 功能，輸入下列命令：
        
            Get-SPSite -limit ALL |foreach{ Enable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }
    
      - 若要停用特定網站集合的 OpenInClient 功能 (以瀏覽器開啟文件)，輸入下列命令：
        
            Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url <SiteCollURL>
        
        其中 *\<SiteCollURL\>* 是網站集合的 URL。
    
      - 若要停用所有網站集合的 OpenInClient 功能 (以瀏覽器開啟文件)，輸入下列命令：
        
            Get-SPSite -limit ALL |foreach{ Disable-SPFeature 8A4B8DE2-6FD8-41e9-923C-C7C3C00F8295 -url $_.URL }

 **使用 \[文件庫設定\] 頁面設定文件庫的預設開啟行為**

1.  在文件庫頁面，選擇 **\[文件庫\]** 索引標籤。

2.  在 **\[設定\]** 群組中，選擇 **\[文件庫設定\]**。

3.  在 **\[文件庫設定\]** 頁面，選擇 **\[進階設定\]**。

4.  在 **\[進階設定\]** 頁面的 **\[在瀏覽器中開啟文件\]** 中，選取下列其中一個選項：
    
      - **以用戶端應用程式開啟**   當使用者選擇此文件庫中的文件時，將會以對應的用戶端應用程式 (若可用的話) 開啟文件。
    
      - **在瀏覽器中開啟**   當使用者選擇此文件庫中的文件時，將會在該文件類型的 Web 應用程式中以網頁瀏覽器開啟文件。在 Web 應用程式中開啟文件之後，使用者就可以決定以用戶端應用程式開啟文件。
    
      - **使用伺服器預設值**   當使用者選擇此文件庫中的文件時，將會以執行 SharePoint 2013 的伺服器所指定的預設開啟行為開啟文件。

 **使用 Windows PowerShell 設定受 IRM 保護之文件庫的預設開啟行為**

1.  首先，確認您具備下列成員資格：
    
      - SQL Server 執行個體上的 **securityadmin** 固定伺服器角色。
    
      - 待更新之所有資料庫上的 **db\_owner** 固定資料庫角色。
    
      - 正在執行 Windows PowerShell Cmdlet 之所在伺服器上的管理員群組。
    
    另外，請閱讀 [about\_Execution\_Policies](http://go.microsoft.com/fwlink/p/?linkid=193050)，並新增其他任何所需的成員資格。
    
    管理員可以使用 **Add-SPShellAdmin** Cmdlet 來授與使用 SharePoint 2013 Cmdlet 的權限。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>如果您沒有權限，請連絡安裝程式系統管理員或 SQL Server 系統管理員要求權限。如需 Windows PowerShell 權限的其他資訊，請參閱<a href="https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps">權限</a>與 <a href="https://technet.microsoft.com/zh-tw/library/ff607596(v=office.15)">Add-SPShellAdmin</a>。</td>
    </tr>
    </tbody>
    </table>


2.  開啟已提升權限的 SharePoint 2013 管理命令介面：
    
    **在 Windows Server 2008 中**
    
    1.  在 \[開始\] 功能表上，選取 \[所有程式\]。
    
    2.  選取 **\[Microsoft SharePoint 2013 產品\]**。
    
    3.  選擇 \[SharePoint 2013 管理命令介面\]，並顯示捷徑功能表 (按一下滑鼠右鍵)。
    
    4.  從捷徑功能表中，選擇 \[以系統管理員身分執行\]。
    
    **在 Windows Server 2012 中**
    
    1.  從螢幕邊緣往內撥動以顯示圖標，並且選擇 **\[搜尋\]** 查看電腦上安裝的所有應用程式。
    
    2.  選擇 (以滑鼠右鍵按一下) \[SharePoint 2013 管理命令介面\] 以顯示應用程式列。
    
    3.  在應用程式列中，選取 **\[以系統管理員身分執行\]**。

3.  在 Windows PowerShell 命令提示字元處，輸入下列命令：
    
        Get-SPWeb -site <SiteCollURL> | % {$_.Lists} | where {$_.IrmEnabled -eq $true} | % {$_.DefaultItemOpen =[Microsoft.Sharepoint.DefaultItemOpen]::<DefaultItemOpenSetting>; $_.Update()}
    
    其中：
    
      - *\<SiteCollURL\>* 是文件庫所在之網站集合的 URL。
    
      - *\<DefaultItemOpenSetting\>* 是指定預設開啟行為的 **DefaultItemOpen** 列舉值。使用 **PreferClient** 以相關聯的用戶端應用程式 (若可用) 開啟文件。使用 **Browser** 以瀏覽器開啟文件。

## 另請參閱


[Get-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIBinding?view=sharepoint-ps)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[使用 Windows Powershell 管理 SharePoint 2013](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/?view=sharepoint-ps)  
[Office Web Apps Server](office-web-apps-server.md)  


[Get-SPWeb](https://technet.microsoft.com/zh-tw/library/ff607807\(v=office.15\))  
[Get-SPSite](https://technet.microsoft.com/zh-tw/library/ff607950\(v=office.15\))  
[Get-SPFeature](https://technet.microsoft.com/zh-tw/library/ff607945\(v=office.15\))

