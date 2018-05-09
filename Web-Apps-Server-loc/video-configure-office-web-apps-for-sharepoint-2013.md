---
title: 影片：設定 Office Web Apps for SharePoint 2013
TOCTitle: 影片：設定 Office Web Apps for SharePoint 2013
ms:assetid: 0c02633f-3839-448b-ae83-24f24c254179
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Dn455088(v=office.15)
ms:contentKeyID: 59152164
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 影片：設定 Office Web Apps for SharePoint 2013

 

_**適用版本：**Office Web Apps, Office Web Apps Server, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**引導您逐步完成設定 Office Web Apps Server 伺服器陣列來使用 SharePoint 2013 的九個主要步驟。

為 SharePoint 2013 設定 Office Web Apps 是個相當簡單的程序。此影片顯示如何在測試環境中設定 Office Web Apps Server 並設定 SharePoint 2013 使用 Office Web Apps Server。


**觀賞「設定 Office Web Apps for SharePoint 2013」影片。**

> [!VIDEO https://www.microsoft.com/zh-tw/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

此影片涵蓋在兩部伺服器上執行的程序：一部是執行 Office Web Apps Server 的伺服器，一部是執行 SharePoint 2013 的伺服器。這些必須是不同的伺服器 (如＜[Office Web Apps Server 的軟體、 硬體及設定需求](plan-office-web-apps-server.md)＞所述)。

**在執行 Office Web Apps Server 的伺服器上，此影片顯示如何：**

1\. 開啟 Windows PowerShell 命令提示字元，並安裝 Office Web Apps Server 所需的角色和服務。請參閱[準備伺服器執行 Office Web Apps Server](deploy-office-web-apps-server.md)。這是必要的動作，因為缺少所需的角色和服務，無法安裝 Office Web Apps Server。  
2\. 從 [大量授權服務中心 (VLSC)](http://go.microsoft.com/fwlink/p/?linkid=256561) 安裝 Office Web Apps Server 軟體。若要下載 Office Web Apps Server，您必須擁有 Office Professional Plus 2013、Office Standard 2013 或 Office for Mac 2011 的大量授權合約所授予的授權。下載位於 VLSC 入口網站的這些 Office 產品之下。  
3\. 使用 [New-OfficeWebAppsFarm](new-officewebappsfarm.md) 建立 Office Web Apps Server 伺服器陣列。  
4\. 開啟瀏覽器視窗並移至 http://*ServerName*/hosting/discovery，確認已成功建立 Office Web Apps Server 伺服器陣列。

**在執行 SharePoint 2013 的伺服器上，此影片顯示如何：**

5\. 開啟 SharePoint 2013 管理命令介面。  
6\. 使用 [New-SPWOPIBinding](new-spwopibinding.md) 建立 Office Web Apps Server 與 SharePoint 2013 之間的繫結。這會設定執行 SharePoint 2013 之伺服器與執行 Office Web Apps Server 之伺服器間的通訊。  
7\. 使用 [Get-SPWOPIZone](get-spwopizone.md) 檢視 SharePoint 2013 的 WOPI 區域。此步驟會突顯出兩部伺服器是使用不同 WOPI 區域的事實：SharePoint 2013 使用 internal-https，而 Office Web Apps Server 則使用 internal-http。區域必須相符，Office Web Apps 才能正常運作。  
8\. 使用 [Set-SPWOPIZone](set-spwopizone.md) 將 WOPI 區域變更為 internal-http，以變更 SharePoint 2013 的 WOPI 區域。  
9\. 開啟 SharePoint 2013 文件庫中的 Office 文件，以確認 Office Web Apps 可以運作。

如需其中每個步驟的詳細資料，請參閱＜[部署 Office Web Apps Server](deploy-office-web-apps-server.md)＞及＜[設定 Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)＞文章中的下列各節。

  - [準備伺服器來執行 Office Web Apps Server](deploy-office-web-apps-server.md)

  - [在測試環境中部署單一伺服器 Office Web Apps Server 伺服器陣列](deploy-office-web-apps-server.md)

  - [準備設定 SharePoint 2013 使用 Office Web Apps Server](configure-office-web-apps-for-sharepoint-2013.md)

  - [在使用 HTTP 的測試環境中設定 SharePoint 2013 使用 Office Web Apps Server](configure-office-web-apps-for-sharepoint-2013.md)

## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[規劃 Office Web Apps (與 SharePoint 2013 搭配使用)](plan-office-web-apps-used-with-sharepoint-2013.md)  
[Office Web Apps 如何在內部部署中與 SharePoint 2013 搭配使用](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)  
  

[](how-office-web-apps-work-on-premises-with-sharepoint-2013.md)

