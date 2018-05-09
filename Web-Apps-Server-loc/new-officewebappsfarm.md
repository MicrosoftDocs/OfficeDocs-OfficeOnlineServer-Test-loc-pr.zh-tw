---
title: New-OfficeWebAppsFarm
TOCTitle: New-OfficeWebAppsFarm
ms:assetid: 3616a668-f76f-45c6-914c-3103cbded5d2
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ219436(v=office.15)
ms:contentKeyID: 49565097
ms.date: 12/21/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsFarm

 

_**適用版本：**Office Web Apps Server_

_**上次修改主題的時間：**2015-03-26_

在本機電腦上建立新的 Office Web Apps Server伺服器陣列。

## 語法

    New-OfficeWebAppsFarm [-AllowCEIP <SwitchParameter>] [-AllowHttp <SwitchParameter>] [-AllowHttpSecureStoreConnections <SwitchParameter>] [-CacheLocation <String>] [-CacheSizeInGB <Nullable>] [-CertificateName <String>] [-ClipartEnabled <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DocumentInfoCacheSize <Nullable>] [-EditingEnabled <SwitchParameter>] [-ExcelAllowExternalData <SwitchParameter>] [-ExcelConnectionLifetime <Nullable>] [-ExcelExternalDataCacheLifetime <Nullable>] [-ExcelPrivateBytesMax <Nullable>] [-ExcelRequestDurationMax <Nullable>] [-ExcelSessionTimeout <Nullable>] [-ExcelWarnOnDataRefresh <SwitchParameter>] [-ExcelWorkbookSizeMax <Nullable>] [-ExternalURL <String>] [-FarmOU <String>] [-Force <SwitchParameter>] [-InternalURL <String>] [-LogLocation <String>] [-LogRetentionInDays <Nullable>] [-LogVerbosity <String>] [-MaxMemoryCacheSizeInMB <Nullable>] [-MaxTranslationCharacterCount <Nullable>] [-OpenFromUncEnabled <SwitchParameter>] [-OpenFromUrlEnabled <SwitchParameter>] [-OpenFromUrlThrottlingEnabled <SwitchParameter>] [-PicturePasteDisabled <SwitchParameter>] [-Proxy <String>] [-RecycleActiveProcessCount <Nullable>] [-RemovePersonalInformationFromLogs <SwitchParameter>] [-RenderingLocalCacheLocation <String>] [-SSLOffloaded <SwitchParameter>] [-TranslationEnabled <SwitchParameter>] [-TranslationServiceAddress <String>] [-TranslationServiceAppId <String>] [-WhatIf [<SwitchParameter>]]

## 詳細描述

**New-OfficeWebAppsFarm** Cmdlet 會在本機電腦上建立新的 Office Web Apps Server伺服器陣列。您必須先在 Office Web Apps Server伺服器陣列中的第一部伺服器上執行此 Cmdlet，然後再使用 **New-OfficeWebAppsMachine** Cmdlet 將更多的伺服器加入伺服器陣列。

## 參數


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>參數</strong></th>
<th>必要</th>
<th>類型</th>
<th>說明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AllowCEIP</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>啟用 Office Web Apps Server伺服器陣列中之所有伺服器上的「客戶經驗改進計劃」(CEIP) 報告功能。</p></td>
</tr>
<tr class="even">
<td><p><strong>AllowHttp</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>指定應將 IIS 網站佈建到連接埠 80 供 HTTP 存取之用。只有所有電腦均需要 IPSEC (完整加密) 的環境或不含敏感性檔案的測試環境，才可使用 <strong>AllowHTTP</strong>。</p>
<p>啟用 <strong>SSLOffloaded</strong> 即會自動啟用。</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHttpSecureStoreConnections</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>指示可以使用非 SSL 連線 (例如 HTTP) 來建立 Secure Store 連線。預設值為 <strong>False</strong>。</p>
<p>僅於所有電腦都需要 IPSEC (完整加密) 的環境，或是未包含機密檔案的測試環境中，使用 <strong>AllowHTTPSecureStoreConnections</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheLocation</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定用以儲存轉譯後之圖像檔案的全域磁碟快取位置。預設位置為 <strong>%programdata%\Microsoft\OfficeWebApps\Working\d\</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheSizeInGB</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定全域磁碟快取的最大大小 (GB)。</p>
<p>此類型必須為 <strong>0</strong> 到任何正整數之間的整數值。預設大小為 <strong>15</strong> GB。</p></td>
</tr>
<tr class="even">
<td><p><strong>CertificateName</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定 Office Web Apps Server用於建立 HTTPS 繫結之認證的易記名稱。</p>
<p>若找不到指定的憑證或憑證已過期，或是指定的值關聯了多份憑證，除會記錄錯誤之外，也不會建立伺服器陣列。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>凡加入 Office Web Apps Server伺服器陣列的每部伺服器皆會使用此值。因此，伺服器陣列中的每部伺服器皆必須具備名稱易記的憑證。</td>
</tr>
</tbody>
</table>

</div>
<p>若是使用 <strong>AllowHttp</strong> 或 <strong>SSLOffloaded</strong> 參數，便無須指定 <strong>CertificateName</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClipartEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>啟用在 Office 文件中插入 Bing 圖片的功能。伺服器必須具備網路通訊能力，才能使用此功能；您可以直接設定網路通訊能力，也可使用 <strong>Proxy</strong> 參數來使用 Proxy。</p>
<p><strong>OpenFromUrlEnabled</strong> 參數必須設定為 <strong>True</strong>，Bing 圖片才能正常運作。預設值為 <strong>False</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>在執行命令之前，提示您確認操作。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>DocumentInfoCacheSize</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定記憶體快取中所能儲存的文件轉換記錄數上限。</p>
<p>預設值為 <strong>5000</strong> 筆記錄。</p></td>
</tr>
<tr class="even">
<td><p><strong>EditingEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>啟用在瀏覽器中編輯的支援。預設值為 <strong>False</strong>。唯有當您具有使用編輯功能的適當授權時，才設為 <strong>True</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelAllowExternalData</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>啟用在 Excel Web App活頁簿中重新整理受支援外部資料的功能 (其中活頁簿包含與外部資料的連線)。預設值為 <strong>True</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelConnectionLifetime</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定 Excel Web App的外部資料連線持續期間 (以秒為單位)。預設值為 <strong>1800</strong> 秒。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelExternalDataCacheLifetime</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定 Excel Web App 中的外部資料快取週期持續期間 (以秒為單位)。預設值為 <strong>300</strong> 秒。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelPrivateBytesMax</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定 Excel Web App 可使用的私用位元組上限 (MB)。若設為 <strong>-1</strong>，表示私用位元組上限為電腦 50% 的實體記憶體。</p>
<p>此類型必須為 <strong>-1</strong> 或任何正整數。預設值為 <strong>-1</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelRequestDurationMax</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>這會指定工作階段中單一要求的最長持續時間 (以秒為單位)。若超過這段時間，要求便會逾時。</p>
<p>此類型必須為 <strong>-1</strong> (無限制) 或 <strong>1</strong> 到 <strong>2073600</strong> 之間的整數。預設值為 <strong>300</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelSessionTimeout</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定當使用者停止活動後，Excel Web App 上之工作階段保持使用中的時間 (秒)。有效值包括：</p>
<p><strong>-1</strong> 工作階段永遠不過期。</p>
<p><strong>0</strong> 工作階段在單一要求結束時到期。</p>
<p><strong>1</strong> 到 <strong>2073600</strong> 工作階段保持使用中 1 秒到 24 天。預設值為 <strong>450</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExcelWarnOnDataRefresh</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>關閉或開啟當 Excel Web App中的資料重新整理時，所顯示的警告對話方塊。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcelWorkbookSizeMax</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>這會指定可載入之活頁簿的大小上限 (以 MB 為單位)。</p>
<p>此類型必須為 <strong>1</strong> 到 <strong>2000</strong> 之間的整數值。預設值為 <strong>10</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalURL</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定用戶端用於從網際網路存取 Office Web Apps Server伺服器陣列的 URL 根。 在負載平衡之多伺服器的 Office Web Apps Server伺服器陣列環境中，外部 URL 會繫結到外部對應之負載平衡器的 IP 位址。</p>
<p>Office Web Apps Server伺服器陣列至少須有一個 URL (可使用 <strong>ExternalURL</strong> 或 <strong>InternalURL</strong> 加以設定)。您也可以同時設定內部及外部的 URL。</p></td>
</tr>
<tr class="even">
<td><p><strong>FarmOU</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定伺服器隸屬之 Active Directory 組織單位 (OU) 的名稱，以加入 Office Web Apps Server伺服器陣列。使用此參數可避免未經授權的伺服器 (即非 OU 成員的伺服器) 加入 Office Web Apps Server伺服器陣列。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>回答「是」會隱藏所有的使用者提示。</p></td>
</tr>
<tr class="even">
<td><p><strong>InternalURL</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定用戶端用於從內部網路存取 Office Web Apps Server伺服器陣列的 URL 根。</p>
<p>Office Web Apps Server伺服器陣列至少須有一個 URL (可使用 <strong>ExternalURL</strong> 或 <strong>InternalURL</strong> 加以設定)。您也可以同時設定內部及外部的 URL。</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogLocation</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定活動記錄檔在本機電腦上的儲存位置。</p>
<p>伺服器陣列中的每部伺服器無法自訂位置而都會使用此位置。預設的位置是 <strong>%programdata%\Microsoft\OfficeWebApps\Data\Logs\ULS\</strong>。</p>
<p>記錄檔的存放磁碟機必須保留足夠的磁碟空間。</p></td>
</tr>
<tr class="even">
<td><p><strong>LogRetentionInDays</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定記錄檔的儲存天數。早於設定日期的記錄檔項目將予刪除。</p>
<p>此類型必須為 <strong>0</strong> 到 <strong>365</strong> 之間的整數值。預設值為 <strong>7</strong> 天。</p></td>
</tr>
<tr class="odd">
<td><p><strong>LogVerbosity</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定追蹤記錄檔所儲存的資訊量。其值包括：</p>
<p><strong>VerboseEX</strong> 在追蹤記錄檔中寫入精簡資料。當資料量可能十分龐大時可使用此值。</p>
<p><strong>Verbose</strong> 在追蹤記錄檔中寫入精簡資料。</p>
<p><strong>Medium</strong> 在追蹤記錄檔中寫入中等詳細程度的資料。</p>
<p><strong>High</strong> 在追蹤記錄檔中寫入詳細資料。</p>
<p><strong>Monitorable</strong> 寫入所監視之不尋常程式碼路徑與動作的追蹤資料。</p>
<p><strong>Unexpected</strong> 寫入所監視之未預期程式碼路徑與動作的追蹤資料。</p>
<p><strong>None</strong> 不在追蹤記錄檔中寫入任何追蹤資訊。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>長時間將 <strong>LogVerbosity</strong> 設為精簡程度，將會對效能造成負面的影響。</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>MaxMemoryCacheSizeInMB</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定轉譯快取所能使用的記憶體空間上限 (MB)。</p>
<p>此類型必須為 <strong>0</strong> 到任何正整數之間的整數值。預設大小為 <strong>75</strong> MB。</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxTranslationCharacterCount</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定文件中可翻譯的字元數量上限。</p>
<p>此類型必須是整數值。此值可設為 <strong>0</strong> (表示無限制) 或從 <strong>2000</strong> 到 <strong>2,000,000</strong> 的值。預設值為 <strong>125,000</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUncEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>開啟或關閉使用線上檢視程式來檢視 UNC 路徑中之 Office 檔案的功能。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219452.note(Office.15).gif" title="注意事項" alt="注意事項" /><strong>附註：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>您必須先將 <strong>OpenFromUrlEnabled</strong> 設為 <strong>True</strong>，線上檢視程式才能顯示 UNC 路徑中的檔案。</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p><strong>OpenFromUrlEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>開啟或關閉使用線上檢視程式來檢視 URL 或 UNC 路徑中之 Office 檔案的功能。預設值為 <strong>False</strong>。</p>
<p>當您使用 <strong>ClipartEnabled</strong> 時，必須將此參數設定為 True。</p></td>
</tr>
<tr class="even">
<td><p><strong>OpenFromUrlThrottlingEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>調節某時段中來自給定伺服器的「從 URL 開啟」數量。預設的節流值無法設定，可確保 Office Web Apps Server 伺服器陣列不會因為要求在線上檢視程式中檢視內容而佔用單一伺服器。</p></td>
</tr>
<tr class="odd">
<td><p><strong>PicturePasteDisabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>關閉使用者將影像從網頁貼上 Office Web Apps 的功能。預設值為 <strong>False</strong>。如果 <strong>OpenFromURLEnabled</strong> 設為 <strong>True</strong>，且 <strong>PicturePasteDisabled</strong> 未設定或設為 <strong>False</strong>，則使用者可以將影像貼上 Office Web Apps。</p></td>
</tr>
<tr class="even">
<td><p><strong>Proxy</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定設定為可將 HTTP 要求傳送至外部網站之 Proxy 伺服器的 URL。一般會搭配 <strong>ClipartEnabled</strong> 及 <strong>TranslationEnabled</strong> 參數一起設定。</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecycleActiveProcessCount</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Nullable</p></td>
<td><p>指定單一 Word 或 PowerPoint 處理序在處理序回收之前所能轉譯的檔案數目。</p>
<p>此類型必須為 <strong>1</strong> 到 <strong>1000</strong> 之間的整數值。預設值為 <strong>5</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>RemovePersonalInformationFromLogs</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>提供從 Office Web Apps Server 記錄清除個人資訊的最佳方法，並且以 SHA256 雜湊取代值。可清除的資訊包括：</p>
<ul>
<li><p>文件名稱及 URL</p></li>
<li><p>IP 位址</p></li>
<li><p>電子郵件地址</p></li>
<li><p>使用者名稱</p></li>
</ul>
<p>預設值為 <strong>False</strong>。請注意，啟用此參數不保證個人資訊不會記錄到 Office Web Apps Server 記錄。</p></td>
</tr>
<tr class="odd">
<td><p><strong>RenderingLocalCacheLocation</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定 Word Viewing Service 及 PowerPoint Viewing Service 所使用之暫存快取的位置。</p>
<p>預設位置為 <strong>%programdata%\Microsoft\OfficeWebApps\Working\waccache\</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>SSLOffloaded</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>指定 Office Web Apps Server伺服器陣列中要將 SSL 分攤到負載平衡器的伺服器。如有啟用 <strong>SSLOffloaded</strong>，Web 應用程式將會繫結到本機伺服器的連接埠 80 (HTTP)，但參考其他資源的 HTML (如 CSS 或圖像) 在參考中仍會使用 HTTPS URL。</p></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationEnabled</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>啟用 Microsoft Translator 自動翻譯文件的支援。Microsoft Translator 是可以在兩種語言之間進行翻譯的線上服務。翻譯後的檔案會顯示在 Word Web App 中。由於 Microsoft Translator 屬於線上服務，因此伺服器必須能夠直接連線到網路通訊，或是使用透過 <strong>Proxy</strong> 參數所指定的 Proxy。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ219449.important(Office.15).gif" title="重要事項" alt="重要事項" /><strong>重要事項：</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsoft Translator 可能會為了改善翻譯品質的目的而收集資料。</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p><strong>TranslationServiceAddress</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定要將翻譯要求傳送到哪個翻譯伺服器 URL。預設值為 Microsoft Translator 線上服務。除非您必須變更翻譯服務，否則通常不會使用此參數。</p></td>
</tr>
<tr class="odd">
<td><p><strong>TranslationServiceAppId</strong></p></td>
<td><p>選用</p></td>
<td><p>System.String</p></td>
<td><p>指定翻譯服務的應用程式識別碼。預設值為公用 Office Web Apps的應用程式識別碼。除非您已經和 Microsoft Translator 協調其他服務，並獲提供私人應用程式識別碼，否則大多不會使用此參數。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>選用</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>顯示訊息會描述命令的功效而不執行命令。如需詳細資訊，請輸入下列命令：<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
</tbody>
</table>


## 輸入類型

## 傳回類型

## 範例

\------------------範例 1---------------------

    New-OfficeWebAppsFarm -InternalUrl "https://server.corp.contoso.com" -ExternalUrl "https://server.external.contoso.com" -EditingEnabled:$true -SSLOffloaded

此範例會在已為 Office Web Apps啟用編輯功能的本機伺服器上，建立 Office Web Apps Server伺服器陣列。伺服器陣列會啟用 **SSLOffloaded** (這會自動啟用 **AllowHttp**)，以設定為負載平衡。若不使用負載平衡器，請務必設定 **CertificateName**。

## 另請參閱


[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  


[Office Web Apps Server 的內容藍圖](content-roadmap-for-office-web-apps-server.md)  
[部署基礎結構：Office Web Apps Server](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

