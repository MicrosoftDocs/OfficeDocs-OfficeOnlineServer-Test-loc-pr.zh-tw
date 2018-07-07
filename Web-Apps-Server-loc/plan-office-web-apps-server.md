---
title: 規劃 Office Web Apps Server
TOCTitle: 規劃 Office Web Apps Server
ms:assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219435(v=office.15)
ms:contentKeyID: 49565094
ms.date: 02/08/2018
mtps_version: v=office.15
ms.translationtype: MT
---

# 規劃 Office Web Apps Server

 

_**適用版本：** Office Web Apps Server_

_**上次修改主題的時間：** 2017-10-10_

**摘要：** 描述 Office Web Apps Server 需求和先決條件，包括 HTTPS、憑證、虛擬化、負載平衡、拓撲及安全性。

**對象：** IT 專業人員

Office Web Apps Server 在內部部署環境中提供瀏覽器型版本的 Office 應用程式，讓使用者更有彈性和共同作業機會。本文說明在您的組織中安裝 Office Web Apps Server 的需求和所需採取的步驟。

請務必小心規劃，讓所有主機，例如SharePoint 2013和Lync Server 2013，可以都彼此Office Web Apps Server。如需設定主機的其他指導，請參閱下列資源：

  - [規劃 Office Web Apps (與 SharePoint 2013 搭配使用)](plan-office-web-apps-used-with-sharepoint-2013.md)

  - [部署 Office Web Apps Server 及 Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=256902)

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SharePoint 2010 產品不能為Office Web Apps Server的主機。Office Web Apps Server不支援SharePoint Foundation 2010或SharePoint Server 2010。Office Web Apps Server也不受支援Exchange Server 2013。</td>
</tr>
</tbody>
</table>


本文內容：

  - Office Web Apps Server 的軟體、硬體及設定需求

  - Office Web Apps Server 的虛擬化支援

  - Office Web Apps Server 的防火牆需求

  - Office Web Apps Server 的負載平衡器需求

  - Office Web Apps Server 的 DNS 需求

  - 規劃 Office Web Apps Server 的語言套件

  - Office Web Apps Server 的拓撲規劃

  - Office Web Apps Server 的安全性規劃

  - 規劃 Office Web Apps Server 的線上檢視程式

  - 規劃 Office Web Apps Server 的更新

## Office Web Apps Server 的軟體、硬體及設定需求

您可以安裝 Office Web Apps Server 做為單一伺服器 Office Web Apps Server 伺服器陣列，或做為多伺服器的負載平衡 Office Web Apps Server 伺服器陣列。您可以使用實體伺服器或虛擬機器執行個體，但是您無法在 Office Web Apps Server 所在的同一部伺服器上安裝其他伺服器應用程式 (例如 SharePoint 2013 或 SQL Server)。

在包含實際使用者資料的環境中，我們一律會建議您使用 HTTPS，而您必須為其取得憑證。如果您是使用伺服器陣列中的多部伺服器，則必須設定硬體或軟體負載平衡解決方案。您可以在下列各節深入瞭解這些情況。

## Office Web Apps Server 的硬體需求

Office Web Apps Server 使用的最小硬體需求與 SharePoint Server 2013 相同。您可以在[硬體需求 — 網頁伺服器、應用程式伺服器及單一伺服器安裝](https://technet.microsoft.com/zh-tw/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)中找到 SharePoint 2013 需求的完整組合。

## 支援 Office Web Apps Server 的作業系統

您可以在下列作業系統上執行 Office Web Apps Server：

  - 64 位元版本的Windows Server 2008 R2 Service Pack 1 (SP1) Standard、 Enterprise 或 Datacenter 安裝[更新的 Windows Server 2008 R2 x64 Edition](https://go.microsoft.com/fwlink/p/?linkid=236954)

  - 64 位元版本 Windows Server 2012 Standard 或 Datacenter

  - 64 位元版本 Windows Server 2012 R2。若要使用這個作業系統，您必須使用 Office Web Apps Server Service Pack 1 (SP1)。

## Office Web Apps Server 的網域需求

Office Web Apps Server 伺服器陣列中的所有伺服器必須是網域的一部分。它們可以在同一個網域 (建議作法) 或者在同一個樹系的網域中。不過，如果您嘗試將 Office Web Apps Server 安裝在網域控制站上，它不會有任何作用。

## Office Web Apps Server 所需的伺服器角色、服務及其他軟體

首先，以下是部署 Office Web Apps Server 時不應執行的一些操作。

  - **請勿在執行 Office Web Apps Server** 的伺服器上安裝任何其他伺服器應用程式。這包括 Exchange Server、SharePoint Server、Lync Server 和 SQL Server。如果您伺服器數量不夠，可考慮在上述其中一個伺服器的虛擬機器執行個體中執行 Office Web Apps Server。

  - **請勿安裝與連接埠 80、443 或 809 上網頁伺服器 (IIS) 相關聯的任何服務或角色**，因為 Office Web Apps Server 會定期移除這些連接埠上的 Web 應用程式。

  - **請勿安裝任何版本的 Office**。如果已安裝，您必須先解除安裝，才能安裝 Office Web Apps Server。

  - **請勿在網域控制站上安裝 Office Web Apps Server**。它不會在執行 Active Directory 網域服務 (AD DS) 的伺服器上執行。

以下是「確實」需要安裝的項目。如需詳細資料，請參閱下列表格。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /> <strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>從<a href="https://go.microsoft.com/fwlink/p/?linkid=256561">大量授權服務服務中心 (VLSC)</a>下載只有Office Web Apps Server 。若要下載Office Web Apps Server必須授權之大量授權合約， Office Professional Plus 2013、 Office Standard 2013，或Office for Mac 2011下。下載 （英文） 位於下 VLSC 入口網站這些Office產品。</td>
</tr>
</tbody>
</table>


### Office Web Apps Server 所需的下載、伺服器角色及功能

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>下載、伺服器角色或功能</th>
<th>如果在 Windows Server 2008 R2 上安裝</th>
<th>如果在 Windows Server 2012 上安裝</th>
<th>如果在 Windows Server 2012 R2 上安裝</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>下載：</strong>Office Web Apps Server</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
</tr>
<tr class="even">
<td><p><strong>下載：</strong>Office Web Apps Server SP1</p></td>
<td><p>建議使用</p></td>
<td><p>建議使用</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510097">Office Web Apps Server SP1</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>下載：</strong>正確版本的 .NET Framework</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256560">.NET Framework 4.5</a></p></td>
<td><p>已經安裝 .NET Framework 4.5</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510096">.NET Framework 4.5.2</a></p></td>
</tr>
<tr class="even">
<td><p><strong>下載：</strong>Windows Server 2008 R2 x64 Edition 更新</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=236954">Windows Server 2008 R2 x64 Edition 更新</a></p></td>
<td><p>不適用</p></td>
<td><p>不適用</p></td>
</tr>
<tr class="odd">
<td><p><strong>下載：</strong>Windows PowerShell 3.0</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=244693">Windows PowerShell 3.0</a></p></td>
<td><p>已安裝</p></td>
<td><p>已安裝</p></td>
</tr>
<tr class="even">
<td><p><strong>伺服器角色：</strong>網頁伺服器 (IIS)</p></td>
<td><p>以下是<strong>網頁伺服器 (IIS)</strong> 伺服器角色所需的最小角色服務。</p>
<p><strong>一般 HTTP 功能</strong></p>
<ul>
<li><p>靜態內容</p></li>
<li><p>預設文件</p></li>
</ul>
<p><strong>應用程式開發</strong></p>
<ul>
<li><p>ASP.NET</p></li>
<li><p>.NET 擴充性</p></li>
<li><p>ISAPI 擴充性</p></li>
<li><p>ISAPI 篩選</p></li>
<li><p>伺服器端包括</p></li>
</ul>
<p><strong>安全性</strong></p>
<ul>
<li><p>Windows 驗證</p></li>
<li><p>要求篩選</p></li>
</ul>
<p><strong>管理工具</strong></p>
<ul>
<li><p>IIS 管理主控台</p></li>
</ul>
<p>建議使用下列選項，但非必要：</p>
<p><strong>效能</strong></p>
<ul>
<li><p>靜態內容壓縮</p></li>
<li><p>動態內容壓縮</p></li>
</ul></td>
<td><p>以下是<strong>網頁伺服器 (IIS)</strong> 伺服器角色所需的最小角色服務。</p>
<p><strong>管理工具</strong></p>
<ul>
<li><p>IIS 管理主控台</p></li>
</ul>
<p><strong>網頁伺服器</strong></p>
<ul>
<li><p>一般 HTTP 功能</p></li>
<li><p>預設文件</p></li>
<li><p>靜態內容</p></li>
</ul>
<p><strong>安全性</strong></p>
<ul>
<li><p>要求篩選</p></li>
<li><p>Windows 驗證</p></li>
</ul>
<p><strong>應用程式開發</strong></p>
<ul>
<li><p>.NET 擴充性 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI 擴充性</p></li>
<li><p>ISAPI 篩選</p></li>
<li><p>伺服器端包括</p></li>
</ul>
<p>建議使用下列服務，但非必要：</p>
<p><strong>效能</strong></p>
<ul>
<li><p>靜態內容壓縮</p></li>
<li><p>動態內容壓縮</p></li>
</ul></td>
<td><p>以下是<strong>網頁伺服器 (IIS)</strong> 伺服器角色所需的最小角色服務。</p>
<p><strong>管理工具</strong></p>
<ul>
<li><p>IIS 管理主控台</p></li>
</ul>
<p><strong>網頁伺服器</strong></p>
<ul>
<li><p>一般 HTTP 功能</p></li>
<li><p>預設文件</p></li>
<li><p>靜態內容</p></li>
</ul>
<p><strong>安全性</strong></p>
<ul>
<li><p>要求篩選</p></li>
<li><p>Windows 驗證</p></li>
</ul>
<p><strong>應用程式開發</strong></p>
<ul>
<li><p>.NET 擴充性 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI 擴充性</p></li>
<li><p>ISAPI 篩選</p></li>
<li><p>伺服器端包括</p></li>
</ul>
<p>建議使用下列服務，但非必要：</p>
<p><strong>效能</strong></p>
<ul>
<li><p>靜態內容壓縮</p></li>
<li><p>動態內容壓縮</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>功能：</strong>筆跡及手寫服務</p></td>
<td><p><strong>筆跡及手寫服務</strong></p>
<ul>
<li><p>筆跡支援</p></li>
</ul></td>
<td><p><strong>筆跡及手寫服務</strong></p>
<ul>
<li><p>不需要筆跡支援。</p></li>
</ul></td>
<td><p><strong>筆跡及手寫服務</strong></p>
<ul>
<li><p>不需要筆跡支援。</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Office Web Apps Server 的虛擬化支援

當您使用 Windows Server Hyper-V 技術來部署時，可完全支援 Office Web Apps Server。如果您計劃要虛擬化 Office Web Apps Server，請遵循下列指引：

  - 將 Office Web Apps Server 安裝在它自己的虛擬機器執行個體中。請勿在此執行個體中安裝任何其他伺服器應用程式，例如 SharePoint 2013。

  - 若有需要，可以將 Office Web Apps Server 安裝在由執行 SharePoint 2013 的伺服器所主控的虛擬機器執行個體中。

  - 若是多重伺服器 Office Web Apps Server 伺服器陣列，每個執行個體都應該在個別的虛擬機器主機上，如此一來，如果有其中一個主機故障，Office Web Apps Server 伺服器陣列仍然可以使用。

## Office Web Apps Server 的防火牆需求

防火牆會封鎖網頁瀏覽器、執行 Office Web Apps Server 的伺服器和執行 SharePoint 2013 的伺服器之間的通訊而造成問題。伺服器位在網路的不同部分時，這些問題會更加複雜。

請確定在執行 Office Web Apps Server 的伺服器或負載平衡器上，下列的連接埠都沒有被防火牆封鎖：

  - 連接埠 443，用於 HTTPS 流量

  - 連接埠 80，用於 HTTP 流量

  - 連接埠 809，用於各個執行 Office Web Apps Server 的伺服器之間的私人流量 (如果您要設定多伺服器的伺服器陣列)

## Office Web Apps Server 的負載平衡器需求

當您在兩部以上的伺服器上執行 Office Web Apps Server 時，建議您使用負載平衡解決方案。任何負載平衡解決方案均可，其中包括執行網頁伺服器 (IIS) 角色的伺服器 (執行應用程式要求路由 (ARR))。事實上，您可以在執行 Office Web Apps Server 的其中一部伺服器上執行 ARR。如果您沒有負載平衡解決方案，請瞭解以下可將 IIS 與 ARR 搭配使用的資源：

  - [安裝應用程式要求路由](https://go.microsoft.com/fwlink/?linkid=236955)

  - [應用程式要求路由說明](https://go.microsoft.com/fwlink/?linkid=236956)

在理想的情況下，請嘗試找出支援下列功能的負載平衡解決方案：

  - 第 7 層路由

  - 啟用用戶端相關性或前端相關性

  - 啟用 SSL 卸載

如果您使用負載平衡器，必須在負載平衡器上安裝憑證，如使用 HTTPS 保護 Office Web Apps Server 通訊所述。

## Office Web Apps Server 的 DNS 需求

在使用 HTTPS 及負載平衡的環境中，您必須更新 DNS，這樣憑證的完整網域名稱 (FQDN) 才會解析成執行 Office Web Apps Server 之伺服器的 IP 位址，或是指派給 Office Web Apps Server 伺服器陣列之負載平衡器的 IP 位址。

## 規劃 Office Web Apps Server 的語言套件

Office Web Apps Server 2013 語言套件可讓使用者從 SharePoint 2013 文件庫、Outlook Web App (以附件預覽方式) 及 Lync 2013 (以 PowerPoint 廣播方式)，以多種語言檢視 Web Office 檔案。不過，這需視主機上設定的語言而定。若要從主機以多種語言檢視 Web Office 檔案，必須滿足下列條件：

  - 若要執行的應用程式中的其他語言設定 （例如SharePoint Server 2013或Lync Server 2013） 主機。安裝及設定主機上的語言套件的程序無關Office Web Apps Server伺服器陣列上安裝語言套件。

  - 已安裝這些語言並可用於 Office Web Apps Server伺服器陣列中的所有伺服器。

以下是其中[下載 Office Web Apps Server 的語言套件](https://go.microsoft.com/fwlink/p/?linkid=263945)。

## Office Web Apps Server 的拓撲規劃

在最低限度下， Office Web Apps Server拓撲將會包含一個實體或虛擬機器執行Office Web Apps Server、 和至少一個主機 （例如執行Lync Server 2013或SharePoint 2013伺服器）。當然，您需要的用戶端電腦或裝置能夠連線至其中一個主機並使用Office Web Apps功能和。從該最小的拓撲，您可以新增更多主機和更多伺服器至Office Web Apps Server的伺服器陣列所需以符合組織的需求。

當 Office Web Apps Server 拓撲變得更複雜時，您應該牢記下列建議清單。

  - **規劃備援。** 如果您有使用虛擬機器執行個體，請務必將它們放在個別的虛擬機器主機上，以供備援。主機上的其他執行個體如果需要，可以執行伺服器應用程式。只要不是在與 Office Web Apps Server 相同的執行個體上執行伺服器應用程式即可。

  - **遵循一個資料中心的原則。** Office Web Apps Server 伺服器陣列中的伺服器必須位在相同的資料中心。請勿將它們分散各地。一般而言，您只需要一個伺服器陣列，除非您有安全性的需求，而需要有自己的 Office Web Apps Server 伺服器陣列的隔離網路。

  - **主機愈靠近愈好。** Office Web Apps Server 伺服器陣列不一定要和所服務的主機位在同一個資料中心，不過，如果若要進行大量編輯，建議您將 Office Web Apps Server 伺服器陣列盡量放置在靠近主機的位置。對於主要使用 Office Web Apps 檢視 Office 檔案的組織而言，就不需要考慮此建議。

  - **規劃連線。** 只相互連接 Office Web Apps Server 伺服器陣列中的每部伺服器。若要將這些伺服器連結到頻寬更寬的網路，請透過反向 Proxy 負載平衡器防火牆。

  - **對於 HTTP 或 HTTPS 要求設定防火牆。** 請確定防火牆允許執行 Office Web Apps Server 的伺服器向主機發出 HTTP 或 HTTPS 要求。

  - **規劃傳入和傳出的通訊。** 在網際網路對向部署中，透過 NAT 裝置路由傳送所有傳出的通訊。在多伺服器陣列中，使用負載平衡器處理所有傳入的通訊。

  - **確定 Office Web Apps Server 伺服器陣列中的所有伺服器都加入網域，成為相同組織單位 (OU) 的一部分。**使用 [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) Cmdlet 中的 **FarmOU** 參數，防止不在此 OU 中的其他伺服器加入伺服器陣列。

  - **針對所有傳入的要求使用超文字安全傳輸通訊協定 (HTTPS)。**

  - **如果在網路上部署 IPsec，請用它來加密伺服器之間的流量。**

  - **規劃使用網際網路的 Office 功能。** 如果需要如美工圖案與翻譯服務的功能，而伺服器陣列中的伺服器無法將要求傳送至網際網路，則您必須為 Office Web Apps Server 伺服器陣列設定 Proxy 伺服器。這樣可以允許將 HTTP 要求傳送至外部網站。

## Office Web Apps Server 的安全性規劃

下列資訊簡介 Office Web Apps Server 的安全性指引。

## 使用 HTTPS 保護 Office Web Apps Server 通訊

Office Web Apps Server可以互相SharePoint 2013與Lync Server 2013使用 HTTPS 通訊協定。在實際執行環境中，我們強烈建議您使用 HTTPS。您必須安裝網際網路伺服器憑證可指派至執行Office Web Apps Server （如果您使用的單一伺服器） 的伺服器或負載平衡器 （如果您使用多部執行Office Web Apps Server）。

不包含任何使用者資料的測試環境，您可以使用 HTTP 來進行SharePoint 2013並略過的憑證需求。Lync Server 2013支援僅 HTTPS。

Office Web Apps Server 使用的憑證必須符合下列需求：

  - 憑證必須來自信任的憑證授權單位，而且 \[SAN\] (主體別名) 欄位中必須包含 Office Web Apps Server 伺服器陣列的完整網域名稱 (FQDN)。(如果 \[SAN\] 中沒有 FQDN，當您嘗試使用憑證時，瀏覽器將會顯示安全性警告，或者不處理回應)。

  - 憑證必須要有可匯出的私密金鑰。在單一伺服器的伺服器陣列上，當您使用 Internet Information Services (IIS) Manager 嵌入式管理單元匯入憑證時，預設會選取此選項。

  - \[易記名稱\] 欄位在信任的根憑證授權單位存放區中必須是唯一的。如果您有多個共用 \[易記名稱\] 欄位的憑證，伺服器陣列建立將會失敗，因為 New-OfficeWebAppsFarm Cmdlet 會不知道要使用哪一個憑證。

  - Office Web Apps Server 不需要任何特殊的憑證內容或副檔名。用戶端增強金鑰使用方法 (EKU) 延伸或伺服器 EKU 延伸就不需要。

  - 在 Windows Server 2012 或 Windows Server 2012 R2 上，您必須安裝 \[允許 HTTP 啟用\] Windows Communication Foundation (WCF) 功能。

憑證必須匯入如下：

  - **針對單一伺服器的伺服器陣列**   您必須直接將憑證匯入執行 Office Web Apps Server 的伺服器。請勿手動繫結憑證。您稍後執行的 New-OfficeWebAppsFarm Cmdlet 會為您執行此作業。如果您手動繫結憑證，每次伺服器重新啟動時，都會將其刪除。

  - **針對負載平衡伺服器陣列**   如果您卸載 SSL，必須將憑證匯入硬體負載平衡器。如果您未卸載 SSL，您必須在 Office Web Apps Server 伺服器陣列中的每部伺服器安裝憑證。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /> <strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>除非在非關鍵測試環境中，否則請勿使用自我簽署憑證。</td>
</tr>
</tbody>
</table>


如需憑證的詳細資訊，請參閱 ＜[如何取得 SSL 憑證](https://go.microsoft.com/fwlink/p/?linkid=269700)。

## 針對硬體負載平衡器使用 SSL 卸載

當您設定新的 Office Web Apps Server 伺服器陣列時，預設會將 SSL 卸載設為關閉。如果您使用硬體負載平衡器，建議您將 SSL 卸載設定為「開啟」，讓伺服器陣列中的每個 Office Web Apps Server 能使用 HTTP 與負載平衡器通訊。將 SSL 卸載設定為「開啟」也會有下列優點：

  - 簡化憑證管理

  - 改善軟性親和性

  - 改善效能

請注意當您使用 HTTP 時，從負載平衡器傳送到執行 Office Web Apps Server 之伺服器的流量不會加密，因此您必須確定網路本身是安全的。使用私人子網路可以協助保護流量。

## 依據 OU 成員資格，限制哪些伺服器可以加入 Office Web Apps Server 伺服器陣列

您可以為這些伺服器建立組織單位，然後在建立伺服器陣列時指定 FarmOU 參數，以防止未經授權的伺服器加入 Office Web Apps Server 伺服器陣列。如需 FarmOU 參數的詳細資訊，請參閱 [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)。

## 使用允許清單限制 Office Web Apps Server 的主機存取

允許清單是一種安全性功能，可防止不想要的主機連接至 Office Web Apps Server 伺服器陣列，並且還在未經您同意的情況下，使用伺服器陣列來進行檔案作業。將包含核准主機的網域新增至允許清單，即可限制 Office Web Apps Server 允許檔案作業要求 (例如檔案擷取、中繼資料擷取和檔案變更) 的主機。

您可以在建立 Office Web Apps Server 伺服器陣列之後，再將網域新增至允許清單。若要瞭解如何新增網域至允許清單，請參閱 [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps)。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /> <strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果您不新增網域至允許清單，Office Web Apps Server 會允許任何網域中的主機提出檔案要求。如果從網際網路可以存取您的 Office Web Apps Server 伺服器陣列，請務必不要將此清單留白。否則，任何人都可以使用您的 Office Web Apps Server 伺服器陣列來檢視及編輯內容。</td>
</tr>
</tbody>
</table>


## 規劃 Office Web Apps Server 的線上檢視程式

根據預設，在您安裝 Office Web Apps Server 之後，就會啟用線上檢視程式功能。如果您計劃要在組織中使用線上檢視程式，請檢閱下列指引。在某些情況下，您可能會想要停用線上檢視程式中的部分功能。這些指引是參照使用 Windows PowerShell Cmdlet [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) 及 [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) 設定的參數。

## 線上檢視程式的安全性考量

檔案若要使用線上檢視程式透過網頁瀏覽器來檢視，絕不能要求驗證。換句話說，檔案必須可以公開使用，因為線上檢視程式在擷取檔案時，不能執行驗證。強烈建議您用於線上檢視程式的 Office Web Apps Server 伺服器陣列只能於內部網路或網際網路擇一存取，但不要都能存取。這是因為 Office Web Apps Server 無法分別內部網路和網際網路 URL 的要求。這樣網際網路上的某人就可要求內部 URL 來檢視內部文件，因此造成安全性漏洞。

基於同樣的理由，如果您將 Office Web Apps Server 設定為只連接至網際網路，強烈建議您停用線上檢視程式中的 UNC 支援。若要停用 UNC 支援，請使用 Windows PowerShell Cmdlet [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (適用於新的伺服器陣列) 或 [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (適用於現有的伺服器陣列)，將 OpenFromUncEnabled 參數設為 False。

另外為預防安全性問題，線上檢視程式限制為只能檢視 10 MB 以下的 Office 檔案。

## 線上檢視程式的設定選項

您可以在 [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (適用於新的伺服器陣列) 或 [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (適用於現有的伺服器陣列) 中使用下列 Windows PowerShell 參數，設定線上檢視程式。

  - **OpenFromUrlEnabled：** 開啟或關閉線上檢視程式。此參數可以為具有 URL 和 UNC 路徑的檔案，控制線上檢視程式。根據預設，當您建立新的 Office Web Apps Server 伺服器陣列時，此參數會設為 False (停用)。

  - **OpenFromUncEnabled**   當線上檢視程式開啟時 (使用 OpenFromUrlEnabled 設為 True)，此參數會開啟或關閉線上檢視程式顯示 UNC 路徑中檔案的功能。根據預設，此參數設為 True，但是在您允許從 UNC 路徑開啟檔案之前，請確定 OpenFromUrlEnabled 也設為 True。如前所述，如果您已設定 Office Web Apps Server 連接至網際網路，建議您將此參數設為 False。

  - **OpenFromUrlThrottlingEnabled**   在一段時間內，控制可以從特定的任何伺服器提出「從 URL 開啟」要求的數量。預設的節流值 (不可設定) 可確保 Office Web Apps Server 伺服器陣列不會因為傳送在線上檢視程式中檢視內容的要求，而讓單一伺服器無法負荷。

## 規劃 Office Web Apps Server 的更新

部署 Office Web Apps Server 之前，您必須決定您的組織要如何管理 Office Web Apps Server 伺服器陣列的軟體更新。雖然軟體更新會協助改善伺服器安全性、效能及可靠性，但是錯誤地安裝更新會造成 Office Web Apps Server 的問題。

Office Web Apps Server 不支援使用 Microsoft 自動更新程序套用 Office Web Apps Server 更新。Office Web Apps Server 的更新必須以特定方式套用，如[套用軟體更新至 Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md)中所述。如果自動套用 Office Web Apps Server 更新，使用者可能無法檢視或編輯 Office Web Apps 中的文件。如果發生這種情形，您必須重新建立 Office Web Apps Server 伺服器陣列。

建議您使用 Windows Server Update Services (WSUS) 或使用 System Center 設定管理員 (其使用 WSUS) 來管理更新。WSUS 可以讓您為 Office Web Apps Server 伺服器陣列中的每部伺服器，全權管理透過 Microsoft Update 發行的軟體散佈。您可以使用 WSUS 來決定哪些更新可以自動套用至伺服器陣列，而哪些更新必須手動套用，例如 Office Web Apps Server 更新。如需 WSUS 的詳細資訊，請參閱 [Windows Server Update Services](https://go.microsoft.com/fwlink/p/?linkid=294822)。

如果您未使用 WSUS 或 System Center 設定管理員，請在 Office Web Apps Server 伺服器陣列中的每部伺服器上，將 Microsoft 自動更新設為 \[自動下載但是通知使用者安裝\]。當您收到 Office Web Apps Server 更新的通知時，請遵循[套用軟體更新至 Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md) 中的步驟進行。若要套用 Windows 更新並且保護伺服器的安全，請在收到可用更新的通知時接受 Windows 更新。

## 另請參閱


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps Server 概觀](office-web-apps-server-overview.md)  
[部署 Office Web Apps Server](deploy-office-web-apps-server.md)  
[套用軟體更新至 Office Web Apps Server](apply-software-updates-to-office-web-apps-server.md)  


[Office.com （提供桌上型電腦或行動裝置上的 Office Web Apps）](https://go.microsoft.com/fwlink/p/?linkid=266657)  
  

[https://technet.microsoft.com/zh-tw/library/jj966220](apply-software-updates-to-office-web-apps-server.md)

