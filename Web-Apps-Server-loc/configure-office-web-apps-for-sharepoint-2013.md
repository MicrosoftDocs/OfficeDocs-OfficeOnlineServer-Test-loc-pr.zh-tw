---
title: 設定 Office Web Apps for SharePoint 2013
TOCTitle: 設定 Office Web Apps for SharePoint 2013
ms:assetid: a5276781-133b-413c-beca-b851e17c2081
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Ff431687(v=office.15)
ms:contentKeyID: 49565120
ms.date: 11/16/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# 設定 Office Web Apps for SharePoint 2013

 

_**適用版本：**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**上次修改主題的時間：**2016-12-16_

**摘要：**說明如何設定 SharePoint 2013 使用 Office Web Apps。

**對象：**IT 專業人員

本文接續＜[部署 Office Web Apps Server](deploy-office-web-apps-server.md)＞的內容。在該文中，您設定了執行 Office Web Apps Server 的伺服器。在本文中，您將設定 SharePoint 2013 來使用 Office Web Apps Server。首先，您需要從 SharePoint 2013 執行一些 Windows PowerShell Cmdlet，之後，使用者便可以使用瀏覽器開啟 SharePoint 2013 文件庫中的 Office 檔案。

如果您不熟悉 Office Web Apps Server 的功能，請[閱讀概觀主題](office-web-apps-server-overview.md)。

本文內容：

  - 設定 SharePoint 2013 使用 Office Web Apps Server 之前

  - 設定 SharePoint 2013 使用 Office Web Apps Server

  - 疑難排解 Office Web Apps 在搭配 SharePoint 2013 使用時的錯誤

  - 中斷 SharePoint 2013 與 Office Web Apps Server 間的連線

## 設定 SharePoint 2013 使用 Office Web Apps Server 之前

開始之前需要檢查幾件事：

  - 安裝 SharePoint 2013。如需指引，請參閱＜[安裝 SharePoint 2013](https://technet.microsoft.com/zh-tw/library/cc303424\(v=office.15\))＞。

  - 確定所有 SharePoint 2013 Web 應用程式皆使用宣告式驗證。在使用傳統模式驗證的 SharePoint 2013 Web 應用程式上，Office Web Apps 的轉譯和編輯無法運作。如需詳細資訊，請參閱＜[適用於 Office Web Apps 的 SharePoint 驗證需求](plan-office-web-apps-used-with-sharepoint-2013.md)＞。

  - 若要讓使用者能夠在網頁瀏覽器中編輯 (而不只是讀取) Office 文件，您需要有編輯授權。此外，您也需要在 Office Web Apps Server 伺服器陣列上啟用編輯功能。您可以在＜[授權 Office Web Apps 編輯 Office 檔案](plan-office-web-apps-used-with-sharepoint-2013.md)＞中深入了解授權需求。

  - 如果您使用系統帳戶登入 SharePoint 2013，將無法測試 SharePoint 2013 與 Office Web Apps Server 間的連線。請使用不同的帳戶登入來測試連線。

  - 記憶體過低的狀況可能會導致無法在 Office Web Apps 中預覽 Office 文件。請檢閱 SharePoint 2013 的＜[硬體需求 - 網頁伺服器、應用程式伺服器與單一伺服器安裝](https://technet.microsoft.com/zh-tw/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)＞一文。這些是 Office Web Apps Server 所使用的相同需求。

## 設定 SharePoint 2013 使用 Office Web Apps Server

請根據是要使用 HTTP 還是 HTTPS 來選擇下列其中一節。HTTP 一般只建議用於測試環境。在實際執行環境中，較安全的 HTTPS 通訊協定會是比較好的選擇。

## 在使用 HTTP 的測試環境

若是此組態，請確定您已按照＜[在測試環境中部署單一伺服器 Office Web Apps Server 伺服器陣列](deploy-office-web-apps-server.md)＞中的步驟設定 Office Web Apps Server。請務必設定 Office Web Apps Server 伺服器陣列使用內部 URL 與 HTTP。[影片：設定 Office Web Apps for SharePoint 2013](video-configure-office-web-apps-for-sharepoint-2013.md)展示如何設定 Office Web Apps Server 以及在測試環境中設定 SharePoint 2013 使用 Office Web Apps Server。

## 步驟 1：開啟已提升權限的 SharePoint 2013 管理命令介面

選取與您的伺服器作業系統對應的程序。

**在 Windows Server 2008 R2**

1.  按一下 \[開始\] \> \[所有程式\] \> \[Microsoft SharePoint 2013 產品\]。

2.  以滑鼠右鍵按一下 \[SharePoint 2013 管理命令介面\]，並按一下 \[以系統管理員身分執行\]。

**在 Windows Server 2012**

1.  按 Windows 標誌鍵 + Q 鍵，或從螢幕邊緣往內撥動以顯示圖標，然後按一下 \[搜尋\] 查看電腦上安裝的所有應用程式。

2.  以滑鼠右鍵按一下 \[SharePoint 2013 管理命令介面\]來顯示應用程式列。

3.  在應用程式列中，按一下 \[以系統管理員身分執行\]。

## 步驟 2：建立 SharePoint 2013 與 Office Web Apps Server 間的繫結

執行下列命令，其中 \<WacServerName\> 是您為內部 URL 設定之 URL 的完整網域名稱 (FQDN)。這是 Office Web Apps Server 流量的進入點。就此測試環境而言，您需要指定 –AllowHTTP 參數，以允許 SharePoint 2013 使用 HTTP 接收來自 Office Web Apps Server 伺服器陣列的探索資訊。如果您未指定 -AllowHTTP，SharePoint 2013 將嘗試使用 HTTPS 來與 Office Web Apps Server 伺服器陣列通訊，而此命令將不會運作。

    New-SPWOPIBinding -ServerName <WacServerName> -AllowHTTP

執行此命令後，您應該會看見 Windows PowerShell 命令提示字元中顯示繫結清單。

需要說明嗎？請參閱＜[New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps)＞。

## 步驟 3：檢視 SharePoint 繫結的 WOPI 區域

Office Web Apps Server 使用區域來決定當與主機 (在此例中為 SharePoint 2013) 通訊時，要使用的 URL (內部或外部) 與通訊協定 (HTTP 或 HTTPS)。依預設，SharePoint Server 2013 會使用 **internal-https** 區域。請執行下列命令，看看您目前是在哪個區域。

    Get-SPWOPIZone

此命令所顯示的 WOPI 區域應該是 **internal-http**。如果顯示正確，請跳至步驟 5。否則，請參閱下一個步驟。

需要說明嗎？請參閱＜[Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps)＞。

## 步驟 4：將 WOPI 區域變更為 internal-http

如果在步驟 3 得到的結果為 **internal-https**，請執行下列命令將區域變更為 **internal-http**。您需要進行此項變更，因為 SharePoint 2013 的區域必須符合 Office Web Apps Server 伺服器陣列的區域。

    Set-SPWOPIZone -zone "internal-http"

重新執行 **Get-SPWOPIZone**，以確認新區域為 **internal-http**。

需要說明嗎？請參閱＜[Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps)＞與＜[Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps)＞。

## 步驟 5：將 SharePoint 2013 中的 AllowOAuthOverHttp 設定變更為 True

若要在測試環境中透過 HTTP 搭配使用 Office Web Apps 與 SharePoint 2013，您需要將 AllowOAuthOverHttp 設定為 **True**，否則 Office Web Apps 將無法運作。您可以執行下列範例來檢查目前的狀態：

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

如果此命令傳回 **False**，請執行下列命令將此設為 **True**。

    $config = (Get-SPSecurityTokenServiceConfig)

    $config.AllowOAuthOverHttp = $true

    $config.Update()

再次執行下列命令，確認現在 AllowOAuthOverHttp 設定已設為**True**。

    (Get-SPSecurityTokenServiceConfig).AllowOAuthOverHttp

需要說明嗎？請參閱＜[Get-SPSecurityTokenServiceConfig](https://technet.microsoft.com/zh-tw/library/ff607642\(v=office.15\))＞。

## 步驟 6：確認 Office Web Apps 正常運作

在 SharePoint 2013 中，請確定您未以系統帳戶登入，這是因為您如果是以該帳戶登入，您將無法使用 Office Web Apps 編輯或檢視文件。請移至包含 Office 文件的 SharePoint 2013 文件庫，並檢視 Word、PowerPoint、Excel 或 OneNote 檔案。文件應該會在瀏覽器中開啟，而瀏覽器是以 Office Web Apps 來顯示檔案。

如果此步驟失敗，請參閱＜疑難排解 Office Web Apps 中的錯誤＞。

## 在使用 HTTPS 的實際執行環境

在開始進行下列程序前，請確定您已按照＜[部署使用 HTTPS 的單一伺服器 Office Web Apps Server 陣列](e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5\(office.15\)#singlehttps)＞或＜[部署使用 HTTPS 的多伺服器、負載平衡 Office Web Apps Server 伺服器陣列](e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5\(office.15\)#multihttps)＞中的步驟設定 Office Web Apps Server。

## 步驟 1：開啟 SharePoint 2013 管理命令介面

選取與您的伺服器作業系統對應的程序。

**在 Windows Server 2008 R2**

1.  選取 \[開始\] \> \[所有程式\] \> \[Microsoft SharePoint 2013 產品\]。

2.  以滑鼠右鍵按一下 \[SharePoint 2013 管理介面\] 來顯示快顯功能表，並按一下 \[以管理員身分執行\]。

**在 Windows Server 2012**

1.  按 Windows 標誌鍵 + Q 鍵，或從螢幕邊緣往內撥動以顯示圖標，然後按一下 \[搜尋\] 查看電腦上安裝的所有應用程式。

2.  以滑鼠右鍵按一下 \[SharePoint 2013 管理命令介面\] 來顯示應用程式列。

3.  在應用程式列中，按一下 \[以系統管理員身分執行\]。

## 步驟 2：建立 SharePoint 2013 與 Office Web Apps Server 間的繫結

執行下列命令，其中 \<WacServerName\> 是您為內部 URL 設定之 URL 的完整網域名稱 (FQDN)。這是 Office Web Apps Server 流量的進入點。

    New-SPWOPIBinding -ServerName <WacServerName> 

需要說明嗎？請參閱＜[New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps)＞。

## 步驟 3：檢視 SharePoint 2013 的 WOPI 區域

Office Web Apps Server 使用區域來決定當與主機 (在此例中為 SharePoint 2013) 通訊時，要使用的 URL (內部或外部) 與通訊協定 (HTTP 或 HTTPS)。依預設，SharePoint Server 2013 會使用 **internal-https** 區域。請執行下列命令，確認此為目前的區域：

    Get-SPWOPIZone

請記下所顯示的 WOPI 區域。

需要說明嗎？請參閱＜[Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps)＞。

## 步驟 4：視需要變更 WOPI 區域

根據您環境不同的不同，您可能必須變更 WOPI 區域。如果您擁有內外兼用的 SharePoint 伺服器陣列，請指定外部。如果您僅有內部用的 SharePoint 伺服器陣列，請指定內部。

如果在步驟 3 得到的結果顯示 **internal-https** 且 SharePoint 伺服器陣列僅為內部用，您可以略過此步驟。如果您擁有內外兼用的 SharePoint 伺服器陣列，則需要執行下列命令，將區域變更為 **external-https**。

    Set-SPWOPIZone -zone "external-https"

需要說明嗎？請參閱＜[Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps)＞。

## 步驟 5：確認 Office Web Apps 正常運作

在 SharePoint 2013 中，請確定您未以系統帳戶登入，這是因為您如果是以該帳戶登入，您將無法使用 Office Web Apps 編輯或檢視文件。請移至包含 Office 文件的 SharePoint 2013 文件庫，並檢視 Word、PowerPoint、Excel 或 OneNote 檔案。文件應該會在瀏覽器中開啟，而瀏覽器是以 Office Web Apps 來顯示檔案。

如果此步驟失敗，請參閱＜疑難排解 Office Web Apps 中的錯誤＞。

## 疑難排解當 Office Web Apps 與 SharePoint 2013 搭配使用時的錯誤

如果 Office Web Apps 搭配 SharePoint 2013 一起使用時無法正常運作，請在下面找出徵狀，並展開標題來尋找疑難排解步驟。

## 問題：在 SharePoint 文件庫中選取「新文件」連結時，會出現上傳文件的提示，而不是看到建立新 Office 文件的選項。選擇 (以滑鼠左鍵按一下) Office 文件時，會在用戶端應用程式中開啟該檔案。不會顯示 Office 文件預覽。

以下是一些可嘗試的疑難排解選項。

**確認用來建立新文件的 SharePoint Web 應用程式是使用宣告式驗證**

只有使用宣告式驗證的 Web 應用程式才能在 Office Web Apps 中開啟檔案。若要判斷 Web 應用程式的驗證提供者，請遵循以下步驟：

1.  在 SharePoint 2013 管理中心，按一下 \[管理 Web 應用程式\]。

2.  選取您要檢查的 Web 應用程式，然後按一下功能區中的 \[驗證提供者\]。

顯示的驗證提供者必須是 \[宣告式驗證\]，如此 Office Web Apps 才能正確搭配 Web 應用程式運作。若要解決此問題，您可以刪除 Web 應用程式，再使用宣告式驗證重新建立 Web 應用程式，或者變更 Web 應用程式的驗證方法。您可以在＜[適用於 Office Web Apps 的 SharePoint 驗證需求](plan-office-web-apps-used-with-sharepoint-2013.md)＞中找到詳細資訊。

**確定 SharePoint 2013 與 Office Web Apps Server 伺服器陣列上的 WOPI 區域相符。**

若要執行此動作，請在 SharePoint Server 上執行下列命令：

    Get-SPWopiZone 

結果會是下列其中一個：

  - internal-https

  - internal-http

  - external-https

  - external-http

接著，在 SharePoint Server 執行下列命令。

    Get-SPWOPIBinding

在輸出中，尋找 **WopiZone: *zone***。如果得自 Get-SPWopiZone 的結果與 Get-SPWOPIBinding 傳回的區域不符，請在 SharePoint Server 上執行 **Set-SPWOPIZone -Zone** Cmdlet，將 WOPI 區域變更為符合得自 Get-SPWOPIBinding 的結果。如需這些 Cmdlet 的使用說明，請參閱＜[Get-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIBinding?view=sharepoint-ps)＞、＜[Set-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIBinding?view=sharepoint-ps)＞和＜[Get-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Get-SPWOPIZone?view=sharepoint-ps)＞。

## 問題：嘗試在 Office Web Apps 中編輯 Office 文件時，收到「很抱歉，無法開啟文件進行編輯」錯誤。

在某些情況下，屬於 Active Directory (AD) 安全性群組的成員可能無法在瀏覽器中編輯文件。解決方法是確認正確設定使用者設定檔服務應用程式 (UPA) 並且與使用者和群組成員完全同步處理。如需詳細資訊，請參閱 KB 文章 [SharePoint 2013 無法對於身為安全性群組成員的使用者編輯 Office Web Apps 2013 檔案](http://support.microsoft.com/kb/2908321?ln=zh-tw)。

## 問題：嘗試在 Office Web Apps 中檢視 Office 文件時，收到「很抱歉，發生錯誤」錯誤。

請確定您未以系統帳戶登入，這是因為您如果是以該帳戶登入，您將無法編輯或檢視文件。請以不同使用者登入，再重新存取 Office Web Apps。

## 問題：嘗試在 Office Web Apps 中檢視 Office 文件時，收到「很抱歉，發生錯誤，無法開啟文件」錯誤。

如果您在使用 HTTP 的測試環境中設定 Office Web Apps，請務必依照＜步驟 5：將 SharePoint 2013 中的 AllowOAuthOverHttp 設定變更為 True＞中的說明，將 AllowOAuthOverHttp 設定為 **True**。

如果您已使用 [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps) Cmdlet 將網域新增至 \[允許清單\]，請確定您是從 \[允許清單\] 中的主機網域存取 Office Web Apps。若要檢視 \[允許清單\] 中的主機網域，請在 Office Web Apps Server 上以系統管理員身分開啟 Windows PowerShell 提示，然後執行 [Get-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/get-officewebappshost?view=officewebapps-ps) Cmdlet。若要將網域新增至 \[允許清單\]，請使用 [New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps) Cmdlet。

## 問題：嘗試在 Office Web Apps 中檢視 Office 文件時，收到「抱歉，Word Web App 無法開啟這份文件，因為服務目前忙碌中。請稍後再試」錯誤。

  - 您不巧將 Office Web Apps Server 安裝在網域控制站嗎？很不幸，Office Web Apps Server 無法在網域控制站上執行。Office Web Apps Server 必須安裝在網域中的另一部伺服器上。如需詳細資訊，請參閱＜[Office Web Apps Server 的軟體、硬體及設定需求](plan-office-web-apps-server.md)＞。

  - 確定您執行 SharePoint 2013 組建 15.0.4420.1017 或更新版本。在 SharePoint 2013 伺服器上，請按照下列步驟檢查組建編號：
    
    1.  移至 \[開始\] \> \[所有程式\] \> \[Microsoft SharePoint 2013 產品\] \> \[SharePoint 2013 管理中心\]。
    
    2.  選擇 \[系統設定\] \> \[管理此伺服器陣列中的伺服器\]。
    
    檢查 \[設定資料庫版本\] 是 **15.0.4420.1017** 或更高版本。如果不是，請參閱 [Office、Office 伺服器與相關產品的更新中心](http://go.microsoft.com/fwlink/p/?linkid=160585) 取得詳細資訊。

## 問題：嘗試在 Office Web Apps 中以使用者產生的 URL 檢視 Office 文件時，收到「找不到檔案。原始檔的 URL 不正確，或文件未供公開存取。請確認 URL 正確，然後連絡文件擁有者」錯誤。

您嘗試從使用者產生的 URL 存取檔案大小大於 10 MB 的文件嗎？請確定文件未超過 10 MB。

## 問題：SharePoint 2013 中未顯示 Office 文件的預覽畫面，卻顯示「此內容無法在框架中顯示」錯誤。

記憶體過低的狀況可能會導致 Office 文件預覽有問題。請閱讀＜[硬體需求 - 網頁伺服器、應用程式伺服器與單一伺服器安裝](https://technet.microsoft.com/zh-tw/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)＞以查看 SharePoint 2013 的記憶體需求。這些是 Office Web Apps Server 所使用的相同需求。

## 問題：您收到「資料連線是設為永遠使用連線檔案，而 {0:ExcelWebApp} 不支援外部連線檔案。無法重新整理下列連線：資料連線」錯誤。

這是因為 Office Web Apps Server 不支援儲存資料連線資訊的 Office 資料連線 (ODC) 檔案。若要解決此問題，請遵循下列步驟：

1.  在 Excel 用戶端應用程式中開啟活頁簿。

2.  按一下 \[資料\] \> \[連線\]。

3.  選取訊息中列出的資料連線，並按一下 \[內容\]。

4.  按一下 \[定義\] 索引標籤。

5.  清除 \[永遠使用連線檔案\] 核取方塊。

6.  將活頁簿重新上傳至 SharePoint 文件庫。

若要讓使用者在瀏覽器視窗中與包含資料模型或 Power View 檢視的活頁簿互動，請在 SharePoint Server 中設定 Excel Services 來顯示活頁簿。這需要 SharePoint 系統管理員在安裝 SharePoint Server 的伺服器上執行 New-SPWOPISupressionSetting Cmdlet。如需詳細資訊，請參閱 [New-SPWOPISuppressionSetting](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPISuppressionSetting?view=sharepoint-ps) 和[在 SharePoint Server 2013 中管理 Excel Services](https://technet.microsoft.com/zh-tw/library/ee681487\(v=office.15\))。

## 中斷 SharePoint 2013 與 Office Web Apps Server 間的連線

如果有任何原因您想要中斷 SharePoint 2013 與 Office Web Apps Server 間的連線，請使用下列命令範例。

    Remove-SPWOPIBinding -All:$true

需要說明嗎？請參閱＜[Remove-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Remove-SPWOPIBinding?view=sharepoint-ps)＞。

## 另請參閱


[New-SPWOPIBinding](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/New-SPWOPIBinding?view=sharepoint-ps)  
[Set-SPWOPIZone](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/Set-SPWOPIZone?view=sharepoint-ps)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署 Office Web Apps Server](deploy-office-web-apps-server.md)  
  

[](deploy-office-web-apps-server.md)

