---
title: 套用軟體更新至 Office Web Apps Server
TOCTitle: 套用軟體更新至 Office Web Apps Server
ms:assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ966220(v=office.15)
ms:contentKeyID: 51442807
ms.date: 11/16/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 套用軟體更新至 Office Web Apps Server
 

_**適用版本：** Office Web Apps Server_

_**上次修改主題的時間：** 2016-12-16_

**摘要：** 說明如何套用軟體更新到 Office Web Apps Server 陣列。

**對象：** IT 專業人員

在新版 Office Web Apps Server 推出之後，Microsoft 提供了一系列的軟體更新來協助改善伺服器的安全性、效能和可靠性。本文說明如何套用軟體更新到 Office Web Apps Server Server 陣列中的個別伺服器。

> [!IMPORTANT]
> 本文為＜<a href="content-roadmap-for-office-web-apps-server.md">Office Web Apps Server 的內容藍圖</a>＞的一部分。請使用藍圖做為協助您部署和管理 Office Web Apps Server 之文章、下載及影片的起點。<br />
<strong>您在尋找在桌上型電腦或行動裝置上使用 Office Web Apps 的協助嗎？</strong>您可以在 <a href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</a> 上搜尋 &quot;Office Web Apps&quot; 來尋找此資訊。


> [!WARNING]
> Office Web Apps Server 不支援使用自動更新程序來套用 Office Web Apps Server 更新。這是因為 Office Web Apps Server 的更新必須以本文所述的特定方式套用。如果自動套用 Office Web Apps Server 更新，使用者可能無法在 Office Web Apps 檢視或編輯文件。如果發生此情況，您必須重建 Office Web Apps Server 伺服器陣列。若要重建伺服器陣列，您必須使用 <a href="https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps">Remove-OfficeWebAppsMachine</a> 從伺服器陣列中移除 Office Web Apps Server、使用 [新增或移除程式] 解除安裝 Office Web Apps Server，然後依照＜<a href="deploy-office-web-apps-server.md">部署 Office Web Apps Server</a>＞中所述的步驟重新安裝 Office Web Apps Server。在重新安裝之後，再依照本文章所述的步驟套用更新。<br />
請務必檢閱＜<a href="plan-office-web-apps-server.md">規劃 Office Web Apps Server 更新</a>＞中的方針，建立 Office Web Apps Server 伺服器陣列的更新程序。


## 開始之前

您可以在 [Microsoft Office 更新部落格](http://go.microsoft.com/fwlink/p/?linkid=280269)，以及在 [Office、Office 伺服器及相關產品的 TechNet 更新中心](http://go.microsoft.com/fwlink/p/?linkid=280271)上找到 Office Web Apps Server 可用更新的最新清單。

針對 Office Web Apps Server 發行的更新將會更新 Office Web Apps Server 及任何已安裝的 Office Web Apps Server 語言套件。沒有專為 Office Web Apps Server 語言套件而設的個別更新。

在升級過程中，您將必須重建 Office Web Apps Server伺服器陣列。要準備重建 Office Web Apps Server 伺服器陣列時，檢閱您目前的 Office Web Apps Server 伺服器陣列內容，方法是執行 Windows PowerShell Cmdlet **Get-OfficeWebAppsFarm** 並檢閱 [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) 的參數。您用於 **New-OfficeWebAppsFarm** 的參數，應該與您第一次設定 Office Web Apps Server 伺服器陣列時使用的參數相同。

> [!NOTE]
> 您可以使用滑鼠、快速鍵或觸控等方式來完成本文中的工作。如需詳細資訊，請參閱下列資源：
> <ul>
> <li><p><a href="http://go.microsoft.com/fwlink/?linkid=249150%26clcid=0x404">快速鍵</a></p></li>
> <li><p><a href="http://go.microsoft.com/fwlink/?linkid=249151%26clcid=0x404">觸控</a></p></li>
> </ul>


## 套用軟體更新至由單伺服器的 Office Web Apps Server 伺服器陣列

若要套用軟體更新到單伺服器的 Office Web Apps Server 伺服器陣列，請從伺服器陣列移除 Office Web Apps Server、套用軟體更新，然後重建 Office Web Apps Server 伺服器陣列。如果您的 Office Web Apps Server 伺服器陣列裡只有一台伺服器，在伺服器更新期間，使用者將無法使用 Office Web Apps。因此請考慮在非關鍵或非營業時間更新 Office Web Apps Server。

**套用軟體更新至單伺服器的伺服器陣列**

1.  如果更新尚未下載到 Office Web Apps Server，請從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?linkid=280274)下載想要套用的 Office Web Apps Server 更新。

2.  在您要套用軟體更新的 Office Web Apps Server 上，以系統管理員身分開啟 Windows PowerShell 提示，並執行下列命令。
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

3.  在該伺服器上安裝 Office Web Apps Server 更新。如果出現提示，請重新啟動伺服器。

4.  以系統管理員身分開啟 Windows PowerShell 提示字元，並執行 **New-OfficeWebAppsFarm** Cmdlet 來重建 Office Web Apps Server 伺服器陣列。您為 **–InternalURL** 指定的 URL，是執行 Office Web Apps Server 的伺服器名稱，例如 <strong>http://Contoso-WAC</strong> 。在此情況下，您會使用先前的 Office Web Apps Server 伺服器陣列所使用的相同名稱。請使用您第一次建立 Office Web Apps Server 伺服器陣列時所使用的相同額外參數。例如，**–AllowHttp** 參數會將伺服器陣列設定為使用 HTTP，而 **–EditingEnabled** 參數在與 SharePoint 2013 搭配使用時，則可啟用在 Office Web Apps 中進行編輯。Lync Server 2013 或 Exchange Server 2013 不使用 **–EditingEnabled** 參數，因為那些主機不支援編輯。
    
    下列範例中的程式碼會建立新的 Office Web Apps Server 伺服器陣列，名為 http://Contoso-WAC。
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    ＜[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)＞中將說明其他可設定翻譯服務、Proxy 伺服器、美工圖案支援與線上檢視程式的參數。

## 套用軟體更新至多 Office Web Apps Server 伺服器陣列

若要套用軟體更新至多 Office Web Apps Server 伺服器陣列，請先從負載平衡器集區和伺服器陣列中移除其中一台伺服器、套用軟體更新，然後建立更新過的 Office Web Apps Server 伺服器陣列。接著將 Office Web Apps Server 伺服器陣列中剩餘的伺服器移除、更新，再加到更新過的新伺服器陣列。當新的伺服器陣列中有足夠的伺服器可支援目前的流量時，就將流量負載平衡到新的伺服器陣列。使用此更新程序時，使用者可以在 Office Web Apps 中開啟及編輯文件，而不會受到中斷。

**套用軟體更新至多伺服器陣列**

1.  從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?linkid=280274)將您要套用的 Office Web Apps Server 更新，下載到 Office Web Apps Server 伺服器陣列可以使用的網路位置。

2.  從負載平衡器集區中移除您要套用軟體更新的 Office Web Apps Server。

3.  在該 Office Web Apps Server 上，以系統管理員身分開啟 Windows PowerShell 提示字元，並執行下列命令。
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

4.  在該伺服器上安裝 Office Web Apps Server 更新。如果出現提示，請重新啟動伺服器。

5.  以系統管理員身分開啟 Windows PowerShell 提示字元，並使用 Cmdlet **New-OfficeWebAppsFarm** 建立更新過的 Office Web Apps Server 伺服器陣列。您為 **–InternalURL** 指定的 URL，是執行 Office Web Apps Server 的伺服器名稱，例如 <strong>http://Contoso-WAC</strong>。在此情況下，請使用與現有 Office Web Apps Server 伺服器陣列相同的名稱。請使用您第一次建立 Office Web Apps Server 伺服器陣列時所使用的相同額外參數。例如，**–AllowHttp** 參數會將伺服器陣列設定為使用 HTTP，而 **–EditingEnabled** 參數在與 SharePoint 2013 搭配使用時，則可啟用在 Office Web Apps 中進行編輯。Lync Server 2013 或 Exchange Server 2013 不使用 **–EditingEnabled** 參數，因為那些主機不支援編輯。
    
    下列範例中的程式碼會建立新的 Office Web Apps Server 伺服器陣列，名為 http://Contoso-WAC。
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    ＜[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)＞中將說明其他可設定翻譯服務、Proxy 伺服器、美工圖案支援與線上檢視程式的參數。

6.  視 Office Web Apps Server 伺服器陣列有多少台伺服器而定，將流量負載平衡到新的伺服器陣列。您可以將此步驟延到在伺服器陣列中加入了更多更新過的伺服器後再執行。

7.  針對伺服器陣列裡剩餘的每台伺服器，遵循下列步驟。
    
    1.  從負載平衡器集區中移除下一台 Office Web Apps Server。
    
    2.  在該伺服器上安裝 Office Web Apps Server 更新。如果出現提示，請重新啟動伺服器。
    
    3.  以系統管理員身分開啟 Windows PowerShell 提示字元，並執行下列命令。**–MachineToJoin** 參數會將目前的伺服器新增到現有的 Office Web Apps Server 伺服器陣列。在此情況下，您會想要將伺服器新增到更新的 Office Web Apps Server 伺服器陣列。因此，請使用更新過之 Office Web Apps Server 伺服器陣列內其中一台伺服器的電腦名稱。
        
        ```PowerShell
            New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
        ```

## 另請參閱


[Remove-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[Get-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/get-officewebappsfarm?view=officewebapps-ps)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
  

[](content-roadmap-for-office-web-apps-server.md)

