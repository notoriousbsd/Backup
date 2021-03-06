---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 在 Windows 上配置 BMR 備份工作

**必要條件**

您需要購買 BMR 外掛程式，才能建立 BMR 備份。BMR 只適用於 Windows Bare Metal Server。VSI 沒有任何可用的 BMR 選項。

## 啟動 WebCC

您需要連接至 {{site.data.keyword.BluSoftlayer_full}} 專用網路，才能啟動 WebCC。
{:important}

1. 登入 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}/catalog/){:new_window}，然後按一下左上角的**功能表**圖示。選取**標準基礎架構**。

   或者，您也可以登入 [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}。
2. 按一下**儲存空間** > **備份**以顯示具有備份服務的伺服器。
3. 選取要備份之檔案所在的伺服器。按一下指向右方的展開箭頭來顯示 WebCC 鏈結。
4. 按一下 **WebCC 登入**，在瀏覽器中啟動 WebCC 用戶端。

   如果 WebCC 未啟動，則您可能會有 VPN 連線問題。您可能也會看到一則訊息，指出您傳送的表單不安全。這是預期的情況 - 請傳送表單來繼續進行。
   {:tip}

## 配置 BMR 備份工作

1. 在左導覽窗格中，按一下**所有代理程式**來顯示現行「IBM Cloud Backup 代理程式」。
2. 按一下**這是我想要配置的新代理程式**。
3. 為您正要配置或建立的工作輸入「工作名稱」及「工作說明」。
4. 對於**備份來源類型**，從清單中選取您要備份的檔案系統類型，然後按**下一步**。
5. 即會顯示**工作類型選取**功能表。請勾選 **Bare Metal Restore** 旁邊的勾選框，然後按**下一步**來繼續。
6. 在「確認」視窗上，按一下**是**。
7. 畫面會顯示新工作現在位於備份集。按**下一步**。
8. 畫面會顯示加密選項及進階備份選項。通常不需要這些選項。按**下一步**。   
9. 在**建立排程**頁面上，您有兩個選擇。
   - 按**下一步**來建立手動工作，並繼續執行新工作
   - 按一下**新增**來排程時間型備份工作。
     1. 選取要執行備份的日期和時間。
     2. 選取您的「保留方案」。

        如需「保留方案」的相關資訊，請參閱[常見問題](faqs.html)。
        {:tip}
     3. 在配置備份排程之後，請按一下**確定**來儲存它。您的已排定工作會新增至已排定工作清單。
10. 選取備份工作的儲存庫，然後按一下**儲存變更**。


## 執行 BMR 備份工作

  - 如果已排定時間型備份工作，則不需要執行其他任何作業。您的工作會依排程自動執行。
  - 如果您設定手動工作（不含時間型排程），則可以在工作清單中選取其列，然後按一下**執行備份**來執行它。<br/> 如同時間型工作，您可以選擇**保留方法**和**進階備份選項**。在您完成配置選擇之後，請按一下**啟動備份**來啟動工作。
