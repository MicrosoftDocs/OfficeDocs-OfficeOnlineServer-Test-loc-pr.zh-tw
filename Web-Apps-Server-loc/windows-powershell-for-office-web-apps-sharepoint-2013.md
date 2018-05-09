---
title: Office Web Apps (SharePoint 2013) 的 Windows PowerShell
TOCTitle: Windows PowerShell for Office Web Apps
ms:assetid: eb4b96e4-b12d-43e7-b1ce-fc04f5cbbd31
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219457(v=office.15)
ms:contentKeyID: 49565154
ms.date: 01/03/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps (SharePoint 2013) 的 Windows PowerShell

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**尋找用來設定 Office Web Apps 之 SPWOPI Windows PowerShell Cmdlet 的相關文章。

**對象：**IT 專業人員

與 SharePoint 2013 內部部署搭配使用時，Office Web Apps 會提供更新版本的 Word Web App、Excel Web App、PowerPoint Web App 及 OneNote Web App。使用者可以在電腦及不同的行動裝置 (例如 Windows Phone、iPhone 及 iPad) 上，使用受支援的網頁瀏覽器來檢視及選擇性地編輯 Office 文件。

![Office 2013 標誌](images/JJ219447.a106e261-2cd0-43b7-af77-92de7e4b6fb9(Office.15).png "Office 2013 標誌")下表列出並說明的文章是關於設定 Office Web Apps 來搭配使用 SharePoint 2013 的每個 SPWOPI Windows PowerShell Cmdlet 。


### SPWOPI Windows PowerShell Cmdlet

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>文章</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="get-spwopibinding.md">Get-SPWOPIBinding</a></p></td>
<td><p>傳回在目前執行此 Cmdlet 之 SharePoint 伺服器陣列上使用 <strong>New-SPWOPIBinding</strong> 建立的繫結清單。</p></td>
</tr>
<tr class="even">
<td><p><a href="get-spwopisuppressionsetting.md">Get-SPWOPISuppressionSetting</a></p></td>
<td><p>傳回目前執行此 Cmdlet 之 SharePoint 伺服器陣列上的隱藏設定。</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-spwopizone.md">Get-SPWOPIZone</a></p></td>
<td><p>傳回 WOPI 應用程式所使用並於目前的 SharePoint 伺服器陣列上設定的區域。</p></td>
</tr>
<tr class="even">
<td><p><a href="new-spwopibinding.md">New-SPWOPIBinding</a></p></td>
<td><p>在目前執行此 Cmdlet 的 SharePoint 伺服器陣列上，建立新繫結以將副檔名或應用程式關聯至動作。</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-spwopisuppressionsetting.md">New-SPWOPISuppressionSetting</a></p></td>
<td><p>針對您在目前 SharePoint 伺服器陣列上指定的動作和文件類型或繫結，關閉 Office Web Apps 。</p></td>
</tr>
<tr class="even">
<td><p><a href="remove-spwopibinding.md">Remove-SPWOPIBinding</a></p></td>
<td><p>從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除應用程式、副檔名及其相關聯動作的繫結。</p></td>
</tr>
<tr class="odd">
<td><p><a href="remove-spwopisuppressionsetting.md">Remove-SPWOPISuppressionSetting</a></p></td>
<td><p>從目前執行此 Cmdlet 的 SharePoint 伺服器陣列中，移除檔案類型或程式識別碼 (ProgID) 的隱藏設定。</p></td>
</tr>
<tr class="even">
<td><p><a href="set-spwopibinding.md">Set-SPWOPIBinding</a></p></td>
<td><p>更新應用程式或副檔名繫結的預設按鍵動作。</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-spwopizone.md">Set-SPWOPIZone</a></p></td>
<td><p>設定目前的 SharePoint 伺服器陣列透過瀏覽器瀏覽至 WOPI 應用程式所使用的區域。</p></td>
</tr>
<tr class="even">
<td><p><a href="update-spwopiproofkey.md">Update-SPWOPIProofKey</a></p></td>
<td><p>更新用於連線到此 Cmdlet 目前執行所在之 SharePoint 伺服器陣列的 WOPI 應用程式的公開金鑰。</p></td>
</tr>
</tbody>
</table>


### 適用於 IT 專業人員的其他 Office 資源

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/JJ219447.22cad0f4-303d-4a40-90a3-fa08e69dfdaf(Office.15).png" title="新功能圖示 (方塊)" alt="新功能圖示 (方塊)" /></p></td>
<td><p><strong>新發佈的內容</strong></p></td>
<td><p>請參閱下文，取得最新或最近更新之 Office Web Apps Server 文章的清單。</p>
<ul>
<li><p><a href="https://technet.microsoft.com/zh-tw/library/ff433481(v=office.15)">Office Web Apps 與 Office Web Apps Server 的最新發佈內容</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><img src="images/JJ219447.6b2d6dfa-7dc8-40fb-8335-af68b575f8cb(Office.15).png" title="快速入門" alt="快速入門" /></p></td>
<td><p><strong>快速入門</strong></p></td>
<td><p>下載 Office Web Apps Server。</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256561">大量授權服務中心 (VLSC)</a></p>
<p>若要下載 Office Web Apps Server，您必須擁有 Office Professional Plus 2013、Office Standard 2013 或 Office for Mac 2011 的大量授權合約所授予的授權。下載位於 VLSC 入口網站的這些 Office 產品之下。</p></li>
</ul>
<p>下載 Office Web Apps Server 的語言套件。</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=263945">Microsoft 下載中心</a></p></li>
</ul>
<p>深入了解 Office Web Apps Server。</p>
<ul>
<li><p><a href="deploy-the-infrastructure-office-web-apps-server.md">部署基礎結構：Office Web Apps Server</a></p></li>
</ul>
<p>探索下列連結，以了解 Office Server 產品如何能夠使用 Office Web Apps Server 來提供 Office 檔案的 Web 型檢視和編輯。</p>
<ul>
<li><p><a href="use-office-web-apps-with-sharepoint-2013.md">搭配並用 Office Web Apps 與 SharePoint 2013</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ219447.6fa793ee-ede9-4476-901c-de96ea37fc3a(Office.15).png" title="聊天圖示" alt="聊天圖示" /></p></td>
<td><p><strong>提供意見反應</strong></p></td>
<td><p>若要提供對 Office 2013Office 365 專業增強版 文件的意見，請選擇頁面底端的 [意見反應] 連結。如此會將您的意見反應直接傳送給文件小組。</p></td>
</tr>
</tbody>
</table>


## 尋找與 Office 相關的訓練及其他資源


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Download</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/evalcenter/hh973391">Office 365 專業增強版</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=507653">Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/evalcenter/ee390818.aspx">Office 2013</a></p></li>
<li><p><a href="https://code.msdn.microsoft.com/office/">Office 程式碼範例</a></p></li>
<li><p><a href="https://gallery.technet.microsoft.com/office/">Office 指令碼和範例檔</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office/aa905351">Office 開發人員下載</a></p></li>
<li><p><a href="http://www.microsoft.com/zh-tw/download/office.aspx?q=office">Office 下載</a></p></li>
<li><p><a href="http://www.microsoft.com/zh-tw/download/search.aspx?q=office+365">Office 365 下載</a></p></li>
</ul></td>
<td><p><strong>作法</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/zh-tw/library/jj220060.aspx">建立 Office 相關應用程式</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/library/cc178982.aspx">部署 Office 2013</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/library/cc179068.aspx">管理 Office 2013</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/office/ff381682.aspx">訓練 Office 2010 使用者</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office/aa905496.aspx">Office SDK</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office/aa905375">Office 開發人員訓練</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=odc%26from=mscomodc">Office 開發人員影片</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=o365%26from=mscomo365">Office 365 開發人員影片</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/office/ff519671">Office IT 專業人員訓練</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/en-us/office/media/video/video.html?cid=otc%26from=mscomotc">Office IT 專業人員影片</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/en-us/office/media/video/video.html?cid=o365%26from=mscomo365">Office 365 IT pro videos</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/openspecifications/">開放規格</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/library/cc307282(v=office.12).aspx">Office 通訊協定</a></p></li>
</ul></td>
<td><p><strong>Sites</strong></p>
<ul>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office">Office 開發人員</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/office">Office IT 專業人員</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office/hh506337">Office 365 開發人員</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/hh912691">Office 365 IT 專業人員</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/library/cc303401.aspx">Office 2013 Resource Kit</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/sharepoint">SharePoint 開發人員</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/sharepoint">SharePoint IT 專業人員</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/vstudio/aa718325">Visual Studio 開發人員</a></p></li>
<li><p><a href="http://office.microsoft.com/">Office.com</a></p></li>
</ul></td>
<td><p><strong>Help</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/zh-tw/office/ee748587.aspx">Office 更新</a></p></li>
<li><p><a href="https://blogs.msdn.com/b/officeapps">Office 相關應用程式及 SharePoint 部落格</a></p></li>
<li><p><a href="https://social.msdn.microsoft.com/forums/zh-tw/category/officedev%2coldevelopment%2csharepoint2010%2csharepoint%2cprojectserver2010%2cprojectprofessional2010%2cuc/">論壇：Office for Developers</a></p></li>
<li><p><a href="https://answers.microsoft.com/zh-tw/msoffice">論壇：Office 365</a></p></li>
<li><p><a href="https://social.technet.microsoft.com/wiki">TechNet Wiki</a></p></li>
<li><p><a href="https://stackoverflow.com/search?q=office">StackOverflow：Office</a></p></li>
<li><p><a href="https://mvp.microsoft.com/zh-tw/mvp/search-mvp.aspx?kw=office">Office MVP</a></p></li>
<li><p><a href="https://technet.microsoft.com/zh-tw/ms772425">Office IT 專業人員支援</a></p></li>
<li><p><a href="https://msdn.microsoft.com/zh-tw/office/aa905515">Office 開發人員支援</a></p></li>
</ul></td>
</tr>
</tbody>
</table>


[](use-office-web-apps-with-sharepoint-2013.md)

