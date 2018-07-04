---
title: 部署 Office Web Apps Server
TOCTitle: 部署 Office Web Apps Server
ms:assetid: e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219455(v=office.15)
ms:contentKeyID: 49565151
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 部署 Office Web Apps Server

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2017-10-05_

**摘要：**說明如何部署 Office Web Apps Server 內部部署，以供 SharePoint 2013 及 Lync Server 2013使用。

**對象：**IT 專業人員

請注意，本文涵蓋為貴公司安裝 Office Web Apps Server。如果您要尋找 Office 或 Office Web Apps 的個人複本的說明，請參閱 <https://support.office.com>。

部署 [Office Web Apps Server](office-web-apps-server-overview.md) 包括安裝一些必要軟體以及執行少許 Windows PowerShell 命令，但是整個過程設計得相當簡單。本文將引導您逐步完成將伺服器準備就緒的程序，然後提供 Windows PowerShell 命令讓您設定 Office Web Apps Server 伺服器陣列。

本文內容：

  - 觀賞影片來了解進行方式

  - 開始之前檢閱這些資源

  - 準備伺服器來執行 Office Web Apps Server

  - 部署 Office Web Apps Server 伺服器陣列

  - 如果您看到「500 Web 服務例外狀況」或「500.21 - 內部伺服器錯誤」訊息

## 觀賞影片來了解進行方式

觀賞下列影片以了解如何在測試環境中設定 Office Web Apps Server。您也會預覽如何設定 SharePoint 2013 來使用 Office Web Apps Server。

**在測試環境中設定 Office Web Apps Server**

> [!VIDEO https://www.microsoft.com/zh-tw/videoplayer/embed/179bf96f-09e1-407a-bb1b-a8e6623eabae]

## 開始之前檢閱這些資源

開始之前，請先確定您已看過下列資源：

  - 如需硬體和軟體需求的詳細資訊，請[看一下規劃方針](plan-office-web-apps-server.md)。

  - Office Web Apps Server 預設可讓您檢視 Office 檔案，但不能編輯。若要編輯檔案，您需要有編輯授權 (請參閱＜[規劃 Office Web Apps (與 SharePoint 2013 搭配使用)](plan-office-web-apps-used-with-sharepoint-2013.md)＞及＜[在 SharePoint Server 2013 中設定授權](https://technet.microsoft.com/zh-tw/library/jj219627\(v=office.15\))＞)。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>您可以使用滑鼠、快速鍵或觸控等方式完成所有 Office 2013 套裝軟體 中的工作。如需如何使用 Office 產品與服務中的快速鍵和觸控功能的詳細資訊，請參閱＜<a href="https://go.microsoft.com/fwlink/p/?linkid=249150">快速鍵</a>＞與＜<a href="https://go.microsoft.com/fwlink/p/?linkid=253163">Office 觸控指南</a>＞。</td>
</tr>
</tbody>
</table>


## 準備伺服器來執行 Office Web Apps Server

在所有要執行 Office Web Apps Server 的伺服器上執行下列程序。

**圖：準備 Office Web Apps Server 伺服器的步驟**

![為 Office Web Apps Server 準備伺服器的三大步驟。](images/JJ219455.af2a4690-4f8b-42c3-aab5-f7066bc0a936(Office.15).gif "為 Office Web Apps Server 準備伺服器的三大步驟。") 

## 步驟 1：安裝 Office Web Apps Server 的必要軟體

Windows Server 2008 R2、Windows Server 2012 與 Windows Server 2012 R2 的必要條件有點不同，因此請選取下面的適當程序，為您的作業系統安裝正確的必要條件。

**在 Windows Server 2008 R2**

1.  安裝下列軟體：
    
      - [Windows Server 2008 R2 Service Pack 1](http://go.microsoft.com/fwlink/p/?linkid=252370)
    
      - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=256560)
    
      - [Windows PowerShell 3.0](https://go.microsoft.com/fwlink/p/?linkid=244693)
    
      - [Windows 7 SP1 和 Windows Server 2008 R2 SP1 的平台更新 (KB2670838)](https://go.microsoft.com/fwlink/p/?linkid=293629)

2.  以系統管理員身分開啟 Windows PowerShell 提示，並執行下列命令以安裝必要的角色和服務。
    
        Import-Module ServerManager
    
    然後，執行此命令：
    
        Add-WindowsFeature Web-Server,Web-WebServer,Web-Common-Http,Web-Static-Content,Web-App-Dev,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,Web-Security,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Dyn-Compression,Web-Mgmt-Console,Ink-Handwriting,IH-Ink-Support,NET-Framework,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-Win-CFAC
    
    依照系統提示來重新啟動伺服器。

**在 Windows Server 2012**

1.  以系統管理員身分開啟 Windows PowerShell 提示，並執行此命令以安裝必要的角色及服務。
    
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    
    依照系統提示來重新啟動伺服器。

**在 Windows Server 2012 R2**

1.  安裝下列軟體：
    
      - [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?linkid=510096)

2.  以系統管理員身分開啟 Windows PowerShell 提示，並執行此命令以安裝必要的角色及服務。
    
        Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45
    
    依照系統提示來重新啟動伺服器。

## 步驟 2：安裝 Office Web Apps Server 和相關更新

在任何要執行 Office Web Apps Server 的伺服器上完成下列步驟。

1.  從[大量授權服務中心 (VLSC)](https://go.microsoft.com/fwlink/p/?linkid=256561) 下載 Office Web Apps Server。若要下載Office Web Apps Server，您必須擁有 Office Professional Plus 2013、Office Standard 2013 或 Office for Mac 2011 的大量授權合約所授予的授權。下載位於 VLSC 入口網站的這些 Office 產品之下。

2.  執行下列其中一項動作：
    
      - 若為 Windows Server 2012 或 Windows Server 2012 R2，請直接開啟 .img 檔案並執行 **Setup.exe**。
    
      - 若為 Windows Server 2008 R2 SP1，請使用能掛載或解壓縮 .img 檔案的程式，然後執行 **Setup.exe**。

3.  在 \[閱讀 Microsoft 軟體授權合約\] 頁面上，選取 \[我接受這份合約條款\]，並按一下 \[繼續\]。

4.  在 \[選擇檔案位置\] 頁面上，選取要安裝 Office Web Apps Server 檔案的資料夾 (例如 C:\\Program Files\\Microsoft Office Web Apps)，並選取 \[立即安裝\]。如果您指定的資料夾不存在，安裝程式將會為您建立該資料夾。
    
    我們建議在系統磁碟上安裝 Office Web Apps Server。

5.  當安裝程式完成安裝 Office Web Apps Server 時，選擇 \[關閉\]。

6.  下載並安裝 [Office Web Apps Server SP1](https://go.microsoft.com/fwlink/p/?linkid=510097) (對於 Windows Server 2012 和 Windows Server 2008 R2 SP1 而言為建議項目。對於 Windows Server 2012 R2 而言則為必要項目。)
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>如果您之後想要套用 Office Web Apps Server SP1，請遵循＜<a href="apply-software-updates-to-office-web-apps-server.md">套用軟體更新至 Office Web Apps Server</a>＞中的指示。</td>
    </tr>
    </tbody>
    </table>


7.  檢閱 [Office、Office Server 與相關產品的 TechNet 更新中心](https://go.microsoft.com/fwlink/p/?linkid=280271)上的清單，看看是否有最新的 Office Web Apps Server 更新。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>如果您並未安裝 Office Web Apps Server SP1，請套用 <a href="https://go.microsoft.com/fwlink/p/?linkid=296579">KB2810007</a>。</td>
    </tr>
    </tbody>
    </table>


## 步驟 3：安裝 Office Web Apps Server 的語言套件

Office Web Apps Server 2013 語言套件可讓使用者以多種語言檢視 Web 型 Office 檔案 (不論是從 SharePoint 2013 文件庫、Outlook Web Access (以附件預覽方式) 還是 Lync 2013 (以 PowerPoint 廣播方式) 開啟)。在＜[規劃 Office Web Apps Server 的語言套件](plan-office-web-apps-server.md)＞深入了解語言套件的運作方式。

若要安裝語言套件，請遵循下列步驟：


1.  從 [Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?linkid=263945)下載 Office Web Apps Server 語言套件。

2.  執行 **WebAppsServerLP\_en-us\_x64.exe**。

3.  在 Office Web Apps Server Language Pack 2013 精靈的 \[閱讀 Microsoft 軟體授權合約\] 頁面上，選取 \[我接受這份合約條款\]，並選取 \[繼續\]。

4.  當安裝程式完成安裝 Office Web Apps Server 時，選擇 \[關閉\]。

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>若要在建立 Office Web Apps Server 伺服器陣列後安裝語言套件，您必須從伺服器陣列中移除某台伺服器、在該伺服器上安裝語言套件，然後再將伺服器加回伺服器陣列中。</p></li>
<li><p>若要讓語言套件正常運作，您需要將它安裝在伺服器陣列的所有伺服器上。</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 部署 Office Web Apps Server 伺服器陣列

請根據您想要建立的 Office Web Apps Server 伺服器陣列類型，遵循下列三節之一的程序 。

<table>
<thead>
<tr class="header">
<th><img src="images/Ee890080.tip(Office.15).gif" title="提示" alt="提示" /><strong>提示：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果 Windows PowerShell 無法識別您執行的 <strong>New-OfficeWebAppsFarm</strong> Cmdlet，您可能需要匯入 <strong>OfficeWebApps</strong> 模組。請使用下列命令：<br />
<code>Import-Module -Name OfficeWebApps</code></td>
</tr>
</tbody>
</table>


## 部署使用 HTTP 的單一伺服器 Office Web Apps Server 伺服器陣列

如果您部署 Office Web Apps Server 只是為了要進行測試或內部使用，而且不需要提供 Office Web Apps Server 功能給 Lync Server 2013，則您適合採取此程序。在這裡，您將安裝使用 HTTP 的單一伺服器 Office Web Apps Server 伺服器陣列。您不需要有憑證或負載平衡器，但是需要有未執行任何其他伺服器應用程式的專用實體伺服器或虛擬機器執行個體。

您可以使用這個 Office Web Apps Server 伺服器陣列來提供 Office Web Apps 功能給 SharePoint 2013。

**圖：部署 Office Web Apps Server 的步驟**

![部署單一伺服器 Office Web Apps Server 伺服器陣列的三大步驟。](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "部署單一伺服器 Office Web Apps Server 伺服器陣列的三大步驟。")

## 步驟 1：建立 Office Web Apps Server 伺服器陣列

使用 **New-OfficeWebAppsFarm** 命令建立含有單一伺服器的新 Office Web Apps Server 伺服器陣列，如下列範例所示。

    New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp -EditingEnabled

**參數**

  - **–InternalURL** 是執行 Office Web Apps Server 的伺服器名稱，例如 **http://servername**。

  - **–AllowHttp** 會設定伺服器陣列來使用 HTTP。

  - **–EditingEnabled**可再搭配 SharePoint 2013 使用時於 Office Web Apps 中啟用編輯功能。Lync Server 2013 不會使用此參數，因為這些主機不支援編輯功能。

＜[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)＞中將說明其他用來設定翻譯服務、Proxy 伺服器、美工圖案支援與線上檢視程式的參數。

如果您看到「500 Web 服務例外狀況」或「500.21 - 內部伺服器錯誤」訊息

## 步驟 2：驗證已成功建立 Office Web Apps Server 伺服器陣列

建立伺服器陣列之後，Windows PowerShell 提示中會顯示伺服器陣列的詳細資料。若要驗證已正確安裝及設定 Office Web Apps Server，請使用網頁瀏覽器來存取 Office Web Apps Server 搜索 URL，如下列範例所示。搜索 URL 是您在設定 Office Web Apps Server 伺服器陣列時指定的 *InternalUrl* 參數，後面接 **/hosting/discovery**，例如：

    http://servername/hosting/discovery

如果 Office Web Apps Server 如預期正常運作，您應該會在網頁瀏覽器中看到 Web 應用程式開放式平台介面通訊協定 (WOPI) 搜索 XML 檔案。該檔案的前幾行應該會像下列範例一樣。

    <?xml version="1.0" encoding="utf-8" ?> 
    - <wopi-discovery>
    - <net-zone name="internal-http">
    - <app name="Excel" favIconUrl="http://servername/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
    <action name="view" ext="ods" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xls" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsb" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
    <action name="view" ext="xlsm" default="true" urlsrc="http://servername/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 

## 步驟 3：設定主機

陣列現在已準備好透過 HTTP 提供 Office Web Apps 功能給主機。如需關於如何設定主機的詳細資訊，請造訪[設定 Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)。

## 部署使用 HTTPS 的單一伺服器 Office Web Apps Server 伺服器陣列
<a name="singlehttps"> </a>

在大部分的實際執行環境中，強烈建議使用 HTTPS 作為安全性功能。此外，如果想要提供 Office Web Apps Server 功能給 Lync Server 2013 (其可讓使用者在瀏覽器中檢視 PowerPoint 廣播)，則也需要 HTTPS。以下是如何安裝使用 HTTPS 的單一伺服器 Office Web Apps Server 伺服器陣列。您將需要在伺服器上安裝憑證 (如＜[使用 HTTPS 保護 Office Web Apps Server 通訊](plan-office-web-apps-server.md)＞所述)。

此 Office Web Apps Server 伺服器陣列會提供 Office Web Apps 功能給 SharePoint 2013 和 Lync Server 2013。

**圖：部署 Office Web Apps Server 的步驟**

![部署單一伺服器 Office Web Apps Server 伺服器陣列的三大步驟。](images/JJ219455.de5b3ed2-d7a7-489e-9de2-f3f068ebe836(Office.15).gif "部署單一伺服器 Office Web Apps Server 伺服器陣列的三大步驟。")

## 步驟 1：建立 Office Web Apps Server 伺服器陣列

使用 **New-OfficeWebAppsFarm** 命令建立含有單一伺服器的新 Office Web Apps Server 伺服器陣列，如下列範例所示。

    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate" -EditingEnabled

**參數**

  - **–InternalURL** 是執行 Office Web Apps Server 之伺服器的完整網域名稱 (FQDN)，例如 **http://servername.contoso.com**。

  - **–ExternalURL** 是可從網際網路上存取的 FQDN。

  - **–CertificateName** 是憑證的易記名稱。

  - **–EditingEnabled** 是選用項目，可在搭配 SharePoint 2013 使用時於 Office Web Apps 中啟用編輯功能。Lync Server 2013 不會使用此參數，因為這些主機不支援編輯功能。

＜[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)＞中將說明其他用來設定翻譯服務、Proxy 伺服器、美工圖案支援與線上檢視程式的參數。

如果您看到「500 Web 服務例外狀況」或「500.21 - 內部伺服器錯誤」訊息

## 步驟 2：驗證已成功建立 Office Web Apps Server 伺服器陣列

建立伺服器陣列之後，Windows PowerShell 提示中會顯示伺服器陣列的詳細資料。若要驗證已正確安裝及設定 Office Web Apps Server，請使用網頁瀏覽器來存取 Office Web Apps Server 搜索 URL，如下列範例所示。搜索 URL 是您在設定 Office Web Apps Server 伺服器陣列時指定的 *InternalUrl* 參數，後面接 **/hosting/discovery**，例如：

    https://server.contoso.com/hosting/discovery

如果 Office Web Apps Server 如預期正常運作，您應該會在網頁瀏覽器中看到 Web 應用程式開放式平台介面通訊協定 (WOPI) 搜索 XML 檔案。該檔案的前幾行應該會像下列範例一樣：

``` 
<?xml version="1.0" encoding="UTF-8"?>
<wopi-discovery><net-zone 
name="internal-https"><app name="Excel" checkLicense="true" 
favIconUrl="https://wac.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action 
name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="ods"/><action name="view" 
urlsrc="https://wac.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" 
default="true" ext="xls"/><action name="view"
 
```

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>依據網頁瀏覽器的安全性設定，在搜索 XML 檔案的內容顯示之前，您可能會看到訊息提示您選取 <strong>[顯示所有內容]</strong>。</td>
</tr>
</tbody>
</table>


## 步驟 3：設定主機

伺服器陣列現在已準備好，可透過 HTTPS 提供 Office Web Apps 功能給主機。如需如何設定主機的詳細資訊，請瀏覽下列文章。

  - [設定 Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [部署 Office Web Apps Server 及 Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

## 部署使用 HTTPS 的多伺服器、負載平衡 Office Web Apps Server 伺服器陣列
<a name="multihttps"> </a>

如果您預期會有許多流量流進 Office Web Apps Server 伺服器陣列，而且想要在網際網路和內部網路上提供該伺服器陣列，則可以使用這類型的拓撲。本節顯示如何安裝使用負載平衡器與 HTTPS 的多伺服器 Office Web Apps Server 伺服器陣列。如果有興趣，可[閱讀關於此拓撲的詳細資訊](plan-office-web-apps-server.md)。

開始之前，請確定已設定負載平衡器 (如＜[Office Web Apps Server 的負載平衡器需求](plan-office-web-apps-server.md)＞所述)。此外，也需要在負載平衡器上安裝憑證 (如＜[使用 HTTPS 保護 Office Web Apps Server 通訊](plan-office-web-apps-server.md)所述＞)。此 Office Web Apps Server 伺服器陣列會提供 Office Web Apps 功能給 SharePoint 2013 和 Lync Server 2013。

**圖：部署 Office Web Apps Server 的步驟**

![部署多伺服器 Office Web Apps Server 伺服器陣列的四大步驟。](images/JJ219455.4c4b31cb-961b-4efd-b755-a18bdcb5c191(Office.15).gif "部署多伺服器 Office Web Apps Server 伺服器陣列的四大步驟。")

## 步驟 1：在第一部伺服器上建立 Office Web Apps Server 伺服器陣列

在第一部伺服器上使用 **New-OfficeWebAppsFarm** 命令，建立新的 Office Web Apps Server 伺服器陣列，如下列範例所示。

    New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -SSLOffloaded -EditingEnabled

**參數**

  - **–InternalURL** 是執行 Office Web Apps Server 之伺服器的完整網域名稱 (FQDN)，例如 **http://servername.contoso.com**。

  - **–ExternalURL** 是可從網際網路上存取的 FQDN 名稱。

  - **-SSLOffloaded** 可啟用將 SSL 終止卸載至負載平衡器。

  - **–EditingEnabled** 是選用項目，可在搭配 SharePoint 2013 使用時於 Office Web Apps 中啟用編輯功能。Lync Server 2013 不會使用此參數，因為這些主機不支援編輯功能。

＜[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)＞中將說明其他用來設定翻譯服務、Proxy 伺服器、美工圖案支援與線上檢視程式的參數。

如果您看到「500 Web 服務例外狀況」或「500.21 - 內部伺服器錯誤」訊息

## 步驟 2：新增更多伺服器至伺服器陣列

第一部伺服器執行 Office Web Apps Server 之後，請在每部您要新增至 Office Web Apps Server 伺服器陣列的伺服器上執行 **New-OfficeWebAppsMachine** 命令。對於 **–MachineToJoin** 參數，請使用 Office Web Apps Server 伺服器陣列中已有之伺服器的電腦名稱。例如，如果伺服器陣列中已有 server1.contoso.com，請使用：

    New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"

需要這些參數的更多相關資訊嗎？您可以在＜[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)＞中找到這些參數。

## 步驟 3：驗證已成功建立 Office Web Apps Server 伺服器陣列

建立伺服器陣列之後，Windows PowerShell 提示中會顯示伺服器陣列的詳細資料。若要驗證已正確安裝及設定 Office Web Apps Server，請使用網頁瀏覽器來存取 Office Web Apps Server 搜索 URL，如下列範例所示。搜索 URL 是您在設定 Office Web Apps Server 伺服器陣列時指定的 *InternalUrl* 參數，後面接 **/hosting/discovery**。例如：

    https://server.contoso.com/hosting/discovery

如果 Office Web Apps Server 如預期正常運作，您應該會在網頁瀏覽器中看到 Web 應用程式開放式平台介面通訊協定 (WOPI) 搜索 XML 檔案。該檔案的前幾行應該會像下列範例一樣：

    <?xml version="1.0" encoding="UTF-8"?>
    <wopi-discovery><net-zone name="internal-https"><app name="Excel" checkLicense="true" favIconUrl="https://officewebapps.contoso.com/x/_layouts/images/FavIcon_Excel.ico"><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="ods"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xls"/><action name="view" urlsrc="https://officewebapps.contoso.com/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" default="true" ext="xlsb"/> 

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>依據網頁瀏覽器的安全性設定，在搜索 XML 檔案的內容顯示之前，您可能會看到訊息提示您選取 <strong>[顯示所有內容]</strong>。</td>
</tr>
</tbody>
</table>


## 步驟 4：設定主機

伺服器陣列現在已準備好，可透過 HTTPS 提供 Office Web Apps 功能給主機。如需如何設定主機的詳細資訊，請瀏覽下列文章。

  - [設定 Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)

  - [部署 Office Web Apps Server 及 Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

## 如果您看到「500 Web 服務例外狀況」或「500.21 - 內部伺服器錯誤」訊息

如果曾經安裝又移除過 .NET Framework 3.5 的功能，則當您執行 OfficeWebApps Cmdlet 時，可能會看到「500 Web 服務例外狀況」或「500.21 – 內部伺服器錯誤」訊息。若要修正此狀況，請從已提升權限的命令提示字元執行下列範例命令，以清理導致 Office Web Apps Server 無法正常運作的設定：

**若是 Windows Server 2008 R2**

    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -iru

    iisreset /restart /noforce

**若是 Windows Server 2012 或 Windows Server 2012 R2**

    dism /online /enable-feature /featurename:IIS-ASPNET45

## 另請參閱


[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[規劃 Office Web Apps Server](plan-office-web-apps-server.md)  
[設定 Office Web Apps for SharePoint 2013](configure-office-web-apps-for-sharepoint-2013.md)  


[部署 Office Web Apps Server 及 Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)  
  

[](configure-office-web-apps-for-sharepoint-2013.md)

