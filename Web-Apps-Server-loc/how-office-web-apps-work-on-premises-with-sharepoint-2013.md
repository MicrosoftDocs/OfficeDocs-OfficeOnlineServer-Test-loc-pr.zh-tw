---
title: Office Web Apps 如何在內部部署中與 SharePoint 2013 搭配使用
TOCTitle: Office Web Apps 內部部署與 SharePoint 2013
ms:assetid: 8480064e-14a4-4b46-ad6b-0c836b192af2
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Ff431685(v=office.15)
ms:contentKeyID: 49565113
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps 如何在內部部署中與 SharePoint 2013 搭配使用

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**提供 Office Web Apps、Office Web Apps Server 以及其如何在內部部署中與 SharePoint 2013 搭配運作的資訊。

**對象：**IT 專業人員

與 SharePoint Server 2013 一起使用時，Office Web Apps Server 會提供更新版本的 Word Web App、Excel Web App、PowerPoint Web App 及 OneNote Web App。使用者可以在電腦及許多行動裝置 (例如 Windows Phone、iPhone、iPad、Windows 8 平板電腦及 Android 裝置) 上，使用受支援的網頁瀏覽器來檢視及 (在某些情況下) 編輯 SharePoint 程式庫中的 Office 文件。


**圖：不同裝置上之 Office Web Apps 的檢視和編輯功能。**

![這個圖表摘要說明不同裝置上 Office Web Apps 的檢視和編輯功能。圖中反白顯示已針對觸控螢幕進行最佳化的功能。](images/Ff431685.8bf76669-f511-4e02-8ed3-d658e9e746f0(Office.15).gif "這個圖表摘要說明不同裝置上 Office Web Apps 的檢視和編輯功能。圖中反白顯示已針對觸控螢幕進行最佳化的功能。")

## Office Web Apps Server 現在安裝為獨立伺服器

Office Web Apps 不是安裝在執行 SharePoint 2013 的同一台伺服器上。正確的做法是，您部署一或多部執行 Office Web Apps Server 的實體或虛擬伺服器，然後設定 SharePoint 2013 伺服器陣列來使用 Office Web Apps Server 伺服器陣列，以提供 Office Web Apps 功能給從 SharePoint 文件庫建立或開啟 Office 檔案的使用者。如需詳細資訊，請參閱＜[Office Web Apps Server 概觀](office-web-apps-server-overview.md)＞。

## Office Web Apps 搭配 SharePoint 2013 使用時的授權選項

Office Web Apps 授權提供兩個選項：

  - **僅供檢視**。根據預設，Office Web Apps 僅供檢視。僅供檢視功能為免費提供。

  - **編輯和檢視**。您將需要購買編輯授權，才能搭配 SharePoint 2013 使用 Office Web Apps 的編輯功能。您可以在建立 Office Web Apps Server 伺服器陣列時，啟用編輯功能。

如果貴組織透過大量授權方案獲得 Office 2013 授權，則可以對 SharePoint 2013 內部部署來啟用 Office Web Apps 編輯功能。這可協助確定使用者不管在家或在其他未安裝 Office 用戶端的位置，都擁有 Office 編輯功能。無法個別購買 Office Web Apps 的編輯授權。

如需關於您授權的確切詳細資料，請參閱在安裝 Office Web Apps Server 時顯示的 Microsoft 軟體授權條款。

SharePoint 2013 提供適用於 Office Web Apps 的新授權規定。如果您啟用 SharePoint 授權，然後啟用 Office Web Apps 編輯功能，則只有具備適當授權的使用者，才能在瀏覽器中實際編輯 Office 檔案。如果沒有為使用者套用任何 Office Web Apps 編輯授權，則僅支援檢視功能。

如需授權如何在 SharePoint 2013 中運作的詳細資訊，請參閱＜[在 SharePoint Server 2013 中設定授權](https://technet.microsoft.com/zh-tw/library/jj219627\(v=office.15\))＞。如需用來啟用編輯功能的 EditingEnabled 參數說明，請參閱＜[New-OfficeWebAppsFarm](new-officewebappsfarm.md)＞及＜[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)＞。

即使當沒有編輯授權時，以及當 Office Web Apps Server 伺服器陣列的編輯功能停用時，還是可以在 Office Web Apps 中編輯在 SharePoint 2013 中使用「以連結共用」功能傳送的檔案。

## 使用 Office Mobile Viewer 存取 SharePoint 網站上的檔案

Office Web Apps Server 提供 Office Mobile Viewer，讓行動使用者在存取 SharePoint Server 網站時可以使用 Office Web Apps。Office Mobile Viewer 預設為啟用，但是可由 SharePoint Server 網站管理員停用。啟用時，使用者可以使用行動裝置上的瀏覽器，瀏覽至 SharePoint Server 網站、點選 SharePoint Server 文件庫中要開啟的文件，該文件就會在行動瀏覽器中開啟。

您可以在＜[SharePoint 2013 的行動裝置新功能](https://technet.microsoft.com/zh-tw/library/fp161352\(v=office.15\))＞及＜[Overview of mobile devices and SharePoint Server 2013](https://technet.microsoft.com/zh-tw/library/fp161351\(v=office.15\))＞中找到在行動裝置上使用 SharePoint 文件庫的詳細資料。使用者可以在＜[在 Android、iPhone 或 Windows Phone 上使用 Office Web Apps](http://go.microsoft.com/fwlink/p/?linkid=271045)＞中深入了解如何在行動裝置上使用 Office Mobile Viewer。如果您決定要在 SharePoint 2013 上停用 Office Mobile Viewer，請使用 [Remove-SPWOPIBinding](remove-spwopibinding.md) Cmdlet。

## Excel Web App 與 SharePoint 中 Excel Services 的差異

Excel Web App 跟 SharePoint 中的 Excel Services 有很多共通點，但並不相同。Excel Services 只有在 SharePoint Server 2013 Enterprise 版本中才有。Excel Web App 則在 SharePoint Server 2013 與 SharePoint Foundation 2013 中都有。這兩個應用程式都可讓您在瀏覽器視窗中檢視活頁簿，也都可讓您操作及探索資料。

但是，Excel Web App 與 SharePoint 中的 Excel Services 還是有些不同之處。例如，Excel Services 支援外部資料連線、資料模型以及與使用資料模型的項目 (如樞紐分析圖報告、樞紐分析表報告與時間軸控制項) 互動的功能。Excel Services 提供比 Excel Web App 更多的商業智慧功能，但 Excel Services 無法讓使用者在瀏覽器視窗中建立或編輯活頁簿。

如需 Excel Web App 與 Excel Services 之差異的詳細資料，請參閱＜[SharePoint Server 2013 的 Excel Services 概觀](https://technet.microsoft.com/zh-tw/library/ee424405\(v=office.15\))＞及＜[比較 SharePoint 中的 Excel Services 與 Excel Web App](http://go.microsoft.com/fwlink/p/?linkid=255460)＞。

如果您的組織決定使用 Excel Services 在瀏覽器中檢視活頁簿，而不使用 Excel Web App，您可以使用 Windows PowerShell **New-SPWOPISuppressionSettings** Cmdlet 在 Excel 活頁簿上關閉 Excel Web App。如需詳細資訊，請參閱＜[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)＞。

## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[規劃 Office Web Apps (與 SharePoint 2013 搭配使用)](plan-office-web-apps-used-with-sharepoint-2013.md)  
  

[](plan-office-web-apps-used-with-sharepoint-2013.md)

