---
title: Office Web Apps Server 概觀
TOCTitle: 概觀：Office Web Apps Server 概觀
ms:assetid: 4b199a88-387f-4121-820d-7af580e2a3e8
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219437(v=office.15)
ms:contentKeyID: 49565101
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# Office Web Apps Server 概觀

 

**適用版本：** Office Web Apps Server

**上次修改主題的時間：** 2017-05-26

**摘要：** 了解 Office Web Apps Server，以及其如何為受支援的主機提供瀏覽器型 Office 功能。

**對象：** IT 專業人員

Office Web Apps Server是將瀏覽器型版本的Word、 PowerPoint、 Excel及OneNote新Office伺服器產品。單一 Office Web Apps Server 伺服器陣列可支援透過SharePoint 2013、 Lync Server 2013、 共用的資料夾及網站存取Office檔案的使用者。新的獨立部署模型表示您可以管理更新至 Office Web Apps Server 伺服器陣列獨立部署其他Office Server 產品在組織中。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /> <strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>本文為＜<a href="content-roadmap-for-office-web-apps-server.md">Office Web Apps Server 的內容藍圖</a>＞的一部分。請使用藍圖做為協助您部署和管理 Office Web Apps Server 之文章、下載及影片的起點。<br />
<strong>您在尋找在桌上型電腦或行動裝置上使用 Office Web Apps 的協助嗎？</strong>您可以在 <a href="https://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a> 上搜尋 &quot;Office Web Apps&quot; 來尋找此資訊。</td>
</tr>
</tbody>
</table>


本文內容：

  - 關於 Office Web Apps Server

  - SharePoint 2013 如何使用 Office Web Apps Server 來檢視和編輯 Office 文件

  - Lync Server 2013 如何使用 Office Web Apps Server 來檢視 PowerPoint 廣播

  - Office Web Apps Server 如何讓使用者能夠利用線上檢視程式來檢視共用資料夾和網站中的 Office 檔案

## 關於 Office Web Apps Server

Office Web Apps Server是提供瀏覽器為基礎的檔案檢視和編輯Office檔案服務Office伺服器產品。Office Web Apps Server適用於產品和服務支援 WOPI，Web 應用程式開啟的平台介面通訊協定。這些產品稱為主機，包含SharePoint 2013和Lync Server 2013。Office Web Apps Server 伺服器陣列可以提供Office服務至多個內部部署主機，且您可以向外延展至多部伺服器一部伺服器從伺服器陣列，您的組織需要成長。雖然Office Web Apps Server需要不執行任何其他伺服器應用程式的專用的伺服器，您可以在虛擬機器執行個體改用安裝Office Web Apps Server 。

會比較容易部署和管理組織內的Office Web Apps ，現在是獨立的產品。如果您要部署SharePoint 2013，例如不再必須最佳化 SharePoint 基礎結構以支援 Office Web Apps，這在舊版本中已SharePoint Server 2010變得更密切整合。您也可以套用更新 Office Web Apps Server 伺服器陣列分開並在不同的頻率比您更新 SharePoint 或 Lync Server。具有獨立的 Office Web Apps Server 伺服器陣列也表示使用者可以檢視或編輯的儲存外部SharePoint Server，例如中共用的資料夾或其他網站的Office檔案。這項功能是稱為 「 線上檢視程式的功能所提供。

下圖顯示 Office Web Apps 先前部署模型與 Office Web Apps 新獨立部署模型之間的差異。

**Office Web Apps 部署模型之間的差異**

![針對 Office Web Apps Server 顯示先前部署模型與新獨立部署模型之間的差異](images/JJ219437.f16dd9d1-c9b7-4c8b-a8de-f1f82c0ee1e2(Office.15).gif "針對 Office Web Apps Server 顯示先前部署模型與新獨立部署模型之間的差異")

## SharePoint 2013 如何使用 Office Web Apps Server 來檢視和編輯 Office 文件

與 SharePoint Server 2013 搭配使用時，Office Web Apps Server 會提供更新版本的 Word Web App、Excel Web App、PowerPoint Web App 及 OneNote Web App。使用者可以在電腦以及許多行動裝置 (例如 Windows Phone、iPhone、iPad 和 Windows 8 平板電腦) 上，使用受支援的網頁瀏覽器來檢視和 (在某些情況下) 編輯 SharePoint 文件庫中的 Office 文件。Office Web Apps 中有許多新功能，其中改良的觸控支援和編輯功能，可讓 iPad 和 Windows 8 平板電腦的使用者直接從其裝置來編輯和檢視 Office 文件。

下圖摘要 Office Web Apps 在各種不同裝置上的檢視和編輯功能。

**Office Web Apps 的檢視和編輯功能**

![這個圖表摘要說明不同裝置上 Office Web Apps 的檢視和編輯功能。圖中反白顯示已針對觸控螢幕進行最佳化的功能。](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "這個圖表摘要說明不同裝置上 Office Web Apps 的檢視和編輯功能。圖中反白顯示已針對觸控螢幕進行最佳化的功能。")

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SharePoint 2013 中已移除 PowerPoint 廣播。您可以透過 OneDrive 和 Lync Server 2013 來使用此功能。</td>
</tr>
</tbody>
</table>


如需 Office Web Apps 新功能的詳細資訊，請參閱＜[Office Web Apps 如何在內部部署中與 SharePoint 2013 搭配使用](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)＞。

## Lync Server 2013 如何使用 Office Web Apps Server 來檢視 PowerPoint 廣播

在 Lync Server 2010 中，有兩種方法可以用來檢視 PowerPoint 簡報。如果使用者執行 Lync 2010，則會使用 PowerPoint 97-2003 格式來展示 PowerPoint 簡報，並使用內嵌版的 PowerPoint 檢視器來檢視該簡報。如果使用者執行 Lync Web App，則 PowerPoint 簡報會轉換成動態 HTML 檔案，然後再使用自訂 DHTML 檔案與 Silverlight 的組合來檢視。這個方法通常是有效的，但有些限制：

  - 內嵌型 PowerPoint Viewer (提供較佳的檢視體驗) 只能在 Windows 平台上使用。

  - 許多行動裝置 (包括某些較熱門的行動電話) 不支援 Silverlight。
    
    無論是 PowerPoint Viewer 還是 DHTML/Silverlight 方法，都不能完全支援較新版 PowerPoint 中的所有功能 (包括投影片切換效果及內嵌視訊)。

為了協助解決這些問題，以及改善展示或檢視 PowerPoint 簡報者的整體經驗，Lync Server 2013 使用 Office Web Apps Server 來處理 PowerPoint 簡報。這個新方法有許多優點，可提供下列功能：

  - 顯示的解析度較高，並且為動畫、投影片切換效果及內嵌視訊之類的 PowerPoint 功能提供較佳的支援。

  - 其他行動裝置可以存取這些簡報。那是因為 Lync Server 2013 是使用標準 DHTML 和 JavaScript 來廣播 PowerPoint 簡報，而不是使用自訂的 DHTML 和 Silverlight。

  - 擁有適當權限的使用者可以與簡報本身分開，獨立地捲動整個 PowerPoint 簡報。例如，當 Ken Myer 在展示其投影片時，Pilar Ackerman 可以捲動整個簡報，檢視她要想要查看的任何投影片，而不會影響 Ken 的簡報。

如需如何設定使用Office Web Apps ServerLync Server 2013的詳細資訊，請參閱[部署 Office Web Apps Server 及 Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)。

## Office Web Apps Server 如何讓使用者能夠利用線上檢視程式來檢視共用資料夾和網站中的 Office 檔案

線上檢視程式可讓使用者使用網頁瀏覽器，來檢視儲存在組織網頁伺服器或共用資料夾中的 Excel、PowerPoint 和 Word 檔案。使用者可以方便地在網頁瀏覽器中檢視 Office 檔案，而不需要另外開啟應用程式。此外，線上檢視程式不需要在使用者的電腦上安裝 Office 2013。線上檢視程式也會產生在網頁中連結或內嵌 URL 時所需的程式碼。您可以在內部網路或網際網路上使用線上檢視程式。

Office Web Apps Server 在位址 http://*OfficeWebAppsServername*/op/generate.aspx 提供一個頁面，可讓您用來產生具有 UNC 或 URL 位址的公開可用文件連結。當使用者選取所產生的 URL 時，線上檢視程式可讓 Office Web Apps Server 從其位置取得檔案，然後使用 Office Web Apps 來轉譯。使用者可以在瀏覽器中檢視 Word、Excel 或 PowerPoint 檔案，而完全不會用到 Office 功能。Word 文件中的格式和版面配置可以被保留，Excel 活頁簿中的資料可供篩選和排序，而 PowerPoint 簡報中可以播放動畫。不過請注意，線上檢視程式可讓使用者檢視，但不能編輯檔案，而且線上檢視程式不能開啟任何需要驗證的檔案。

如需線上檢視程式的詳細資訊，請參閱＜[規劃線上檢視程式](plan-office-web-apps-server.md)＞。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsoft 在 <a href="http://go.microsoft.com/fwlink/?linkid=256548%26clcid=0x404">Office.com</a> 上有裝載限定網際網路對應版的「建立 URL」功能。</td>
</tr>
</tbody>
</table>


## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[規劃 Office Web Apps Server](plan-office-web-apps-server.md)  
[部署 Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[https://technet.microsoft.com/zh-tw/library/jj219455](deploy-office-web-apps-server.md)

