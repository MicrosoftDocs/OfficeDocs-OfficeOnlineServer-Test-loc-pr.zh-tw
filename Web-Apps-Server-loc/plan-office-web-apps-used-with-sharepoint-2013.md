---
title: 規劃 Office Web Apps (與 SharePoint 2013 搭配使用)
TOCTitle: 規劃 Office Web Apps
ms:assetid: 3bd0a617-5f12-4a7e-bb75-b15c86c7e504
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Ff431682(v=office.15)
ms:contentKeyID: 49565099
ms.date: 11/16/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 規劃 Office Web Apps (與 SharePoint 2013 搭配使用)

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**檢閱 Office Web Apps 搭配 SharePoint 2013 內部部署使用的規劃指引。

**對象：**IT 專業人員

若要規劃 Office Web Apps 與 SharePoint 2013 內部部署的搭配使用，應檢閱使用 Office Web Apps 來檢視及編輯 Office 檔案的瀏覽器支援、SharePoint 驗證需求和授權考量事項。然後，您就可以決定當使用者從 SharePoint 2013 文件庫開啟 Office 檔案時，要讓 SharePoint 2013 使用網頁瀏覽器還是用戶端應用程式。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>本文是 <a href="content-roadmap-for-office-web-apps-server.md">Office Web Apps Server 的內容藍圖</a>的一部分。請以藍圖做為起點來取得文章、下載檔及影片，以協助您部署及管理 Office Web Apps Server。<br />
<strong>您在尋找在桌上型電腦或行動裝置上使用 Office Web Apps 的協助嗎？</strong>您可以在 <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a> 上搜尋 &quot;Office Web Apps&quot; 來尋找此資訊。</td>
</tr>
</tbody>
</table>


本文內容：

  - 關於規劃 Office Web Apps

  - Office Web Apps 的瀏覽器支援

  - Office Web Apps 的 SharePoint 驗證需求

  - 授權 Office Web Apps 編輯 Office 檔案

  - 部署 Office Web Apps 搭配 SharePoint 2010 使用的客戶考量

  - 從 SharePoint 2013 文件庫開啟文件的預設開啟行為

## 關於規劃 Office Web Apps

本文中指引的是您在組織中部署 Office Web Apps Server 內部部署時，所要執行之整體規劃的一部分。例如，軟硬體和虛擬化需求、伺服器陣列大小調整和拓撲，以及安全性，全都是 Office Web Apps Server 規劃的一部分。在做了那些決定之後，您可以規劃如何設定 SharePoint 2013 專屬的 Office Web Apps 功能。如果您沒聽過 Office Web Apps Server 或檢閱過其需求及規劃指引，請參閱＜[Office Web Apps Server 概觀](office-web-apps-server-overview.md)＞和＜[規劃 Office Web Apps Server](plan-office-web-apps-server.md)＞。

## Office Web Apps 的瀏覽器支援

Office Web Apps 的瀏覽器支援與 SharePoint 2013 相同。如需詳細資訊，請參閱＜[在 SharePoint 2013 中規劃瀏覽器支援](https://technet.microsoft.com/zh-tw/library/cc263526\(v=office.15\))＞。

## Office Web Apps 的 SharePoint 驗證需求

只有擁有宣告式驗證的 SharePoint 2013 Web 應用程式可以使用 Office Web Apps。在使用傳統模式驗證的 SharePoint 2013 Web 應用程式上，Office Web Apps 的轉譯和編輯無法運作。若您將使用傳統模式驗證的 SharePoint 2010 Web 應用程式移轉至 SharePoint 2013，就必須將該應用程式移轉至宣告式驗證以允許其搭配 Office Web Apps 使用。若要深入了解，請參閱＜[在 SharePoint 2013 中從傳統模式移轉至宣告式驗證](https://technet.microsoft.com/zh-tw/library/gg251985\(v=office.15\))＞。

## 授權 Office Web Apps 編輯 Office 檔案

透過大量授權方案取得 Office 2013 授權的企業客戶可以對 SharePoint 2013 內部部署來啟用 Office Web Apps 編輯功能。這可協助確定使用者不管在家或在其他未安裝 Office 用戶端的位置，都擁有 Office 編輯功能。

如需關於您授權的確切詳細資料，請參閱在安裝 Office Web Apps Server 時顯示的 Microsoft 軟體授權條款。如需關於授權如何在 SharePoint 2013 中運作的詳細資訊，請參閱＜[在 SharePoint Server 2013 中設定授權](https://technet.microsoft.com/zh-tw/library/jj219627\(v=office.15\))＞。

## 使用資料庫附加方法從 SharePoint 2010 升級的客戶考量

如果您已將 Office Web Apps 與 SharePoint 2010 一起安裝，則在您升級至 SharePoint 2013 之後將無法使用 Office Web Apps。您必須在內容資料庫升級之後，部署 Office Web Apps Server，然後將其連接至 SharePoint 2013。由於 SharePoint 2013 中 Office Web Apps Server 支援 2010 及 2013 網站集合模式，因此您不需要等到升級網站集合之後才連接。如需關於資料庫附加方法的詳細資訊，請參閱＜[升級到 SharePoint 2013 的程序概觀](https://technet.microsoft.com/zh-tw/library/cc262483\(v=office.15\))＞。

## 從 SharePoint 2013 文件庫開啟之文件的預設開啟行為

您可以設定要在用戶端應用程式 (若有安裝的話) 還是在瀏覽器中開啟 Word、PowerPoint、Excel 和 OneNote 檔案。根據預設，將 SharePoint 2013 設定為使用 Office Web Apps Server 之後，就會在瀏覽器中開啟 Office 檔案。有兩種方法可以變更此預設行為，以允許用戶端應用程式直接開啟檔案：

  - **若是 SharePoint 2013 伺服器陣列** 您可以使用 [New-SPWOPIBinding](new-spwopibinding.md) 和 [Set-SPWOPIBinding](set-spwopibinding.md)Windows PowerShell Cmdlet，依照每個檔案類型為 SharePoint 2013 伺服器陣列調整預設開啟行為。

  - **在網站集合或文件庫上** 網站集合管理員和使用者可以指定是否要在用戶端應用程式 (若已安裝) 上開啟 Office 檔案。使用者可以在文件庫屬性中變更此設定，而網站集合管理員可以在網站集合管理中變更此設定，或是使用 Install-SPFeature Cmdlet 來安裝 OpenInClient 功能。如需詳細資訊，請參閱＜[Install-SPFeature](https://technet.microsoft.com/zh-tw/library/ff607825\(v=office.15\))＞。

## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps 如何在內部部署中與 SharePoint 2013 搭配使用](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  


[設定 SharePoint 2013 Preview 在使用 HTTP 的測試環境中使用 Office Web Apps Server Preview](configure-office-web-apps-for-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

