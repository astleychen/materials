檢查您現有的 Microsoft Account 是否有啟用過 Azure Pass

(若您沒有 Microsoft Account，請跳過本段落，直接進行註冊 Microsoft Account)

l  開啟網頁瀏覽器(如:Microsoft Edge、Internet Explorer 等)，連到 https://account.azure.com/Subscriptions ，並以您的  Microsoft Account 登入

l  若有看到 Azure Pass 字樣，則此帳戶曾經啟用過 Azure Pass，請重新註冊新的 Microsoft Account

l  若沒有看到 Azure Pass 字樣，則此帳戶可啟用 Azure Pass，您可跳過註冊 Microsoft Account，直接進行啟用 Azure Pass

 

註冊 Microsoft Account

1.        開啟網頁瀏覽器(如:Microsoft Edge、Internet Explorer 等)，連到 http://sigup.live.com

2.        按[建立帳戶]後，輸入您想要使用的使用者名稱後，按[下一步]

3.        輸入您想要使用的帳戶密碼後，按[下一步]

4.        輸入您的姓氏及名字後，按[下一步]

5.        選取您的出生日期後，按[下一步]

6.        輸入您的電話號碼後，按[傳送驗證碼]

7.        查看您的手機簡訊，輸入驗證碼後，按[下一步]

 

啟用 Azure Pass

1.        在網頁瀏覽器連到 http://www.microsoftazurepass.com/

2.        按[Start]後，以您的 Microsoft Account 登入

3.        按[Confirm Microsoft Account]

4.        輸入您的 Promo Code 後，按[Claim Promo Code]

5.        按[Activate]

6.        輸入您聯絡用的 Email Address 後，在 Organization 輸入貴公司名稱(可不輸入)，在 Tax Id 輸入貴公司的統一編號(您也可以輸入 00000000)，然後按[Next]

7.        輸入您的手機號碼後，按[Next]

8.        勾選[I agree to the ...]後，按[Sign up]

9.        等待數分鐘，看到「Your Subscription is ready for you!」後，按[PORTAL](在右上方)

10.    進到 Azure Portal(https://portal.azure.com) 後，按[稍後再說]

 

建立儲存體帳戶

1.        在 Azure Portal(https://portal.azure.com) 中，依次點選[建立資源]→[Storage]→[儲存體帳戶]

2.        在[名稱]輸入 storxxxxxx (xxxxxx 為您自行決定的小寫英文字母或數字,儲存體帳戶的名稱需3~24個字元、全世界唯一且只能使用小寫英文字母與阿拉伯數字)

3.        在[資源群組]輸入 RG-LAB，在[位置]選取 東南亞 後，按[建立]

4.        等待通知已成功部署後，依次點選[儲存體帳戶]→[storxxxxxx](您先前所建立的儲存體帳戶)

5.        點選[檔案]後，按[+檔案共用]

6.        在[名稱]輸入 share ，在配額輸入 5120 後，按[確定]

7.        點選[share]後，按[連接]，然後按最右方中間的複製圖示

8.        開啟命令提示字元後，按滑鼠右鍵(即可貼上)後，按 Enter

9.        若您的 Windows 系統為 Windows 8/2012(含以上) 預設即有支援 SMB 3.0，此時將把您儲存體帳戶中的 share 共用對應為 Z: 磁碟(若您的 Windows 系統為 Windows 7，此操作將出現錯誤訊息)

 

建立虛擬網路

1.         在 Azure Portal 中，依次點選[建立資源]→[網路]→[虛擬網路]

2.         在[名稱]輸入 VNet-Lab ，在[位址空間]輸入 172.16.0.0/16 ，在[資源群組]點選[使用現有項目]並選取[RG-LAB]，確認[位置]為 東南亞，在[位址範圍]輸入 172.16.0.0/24 後，點一下畫面空白處，然後按[建立]

 

建立可用性設定組

1.        在 Azure Portal 中，按[建立資源]，在 Search the marketplace 輸入 avail 後，選取 Availability Set，然後按[建立]

2.        在[名稱]輸入 WebFarm ，，在[資源群組]點選[使用現有項目]並選取[RG-LAB]，確認[位置]為 東南亞 後，按[建立]

 

建立兩部在同一個可用性設定組中的虛擬機器

1.        在 Azure Portal 中，依次點選[建立資源]→[Windows Server 2016 VM]

2.        在[名稱]輸入 VM1 ，在[使用者名稱]輸入 VMAdmin ，在[密碼]及[確認密碼]輸入 Pa55w.rd1234 ，在[資源群組]點選[使用現有項目]並選取[RG-LAB]，確認[位置]為 東南亞 後，按[確定]

3.        在[選擇大小]點選[DS1_V2]後，按[選取]

4.        點選[可用性設定組]後，選取[WebFarm]，點選[診斷儲存體帳戶]後，選取[storxxxxxx](您先前所建立的儲存體帳戶)，然後按[確定]→[建立]

5.        再次點選[建立資源]→[Windows Server 2016 VM]

6.        在[名稱]輸入 VM2 ，在[使用者名稱]輸入 VMAdmin ，在[密碼]及[確認密碼]輸入 Pa55w.rd1234 ，在[資源群組]點選[使用現有項目]並選取[RG-LAB]，確認[位置]為 東南亞 後，按[確定]

7.        在[選擇大小]點選[DS1_V2]後，按[選取]

8.        點選[可用性設定組]後，選取[WebFarm]，點選[診斷儲存體帳戶]後，選取[storxxxxxx](您先前所建立的儲存體帳戶)，然後按[確定]→[建立]

 

 

建立與設定負載平衡器

1.        在 Azure Portal 中，依次點選[建立資源]→[網路]→[負載平衡器]

2.        在[名稱]輸入 WebFarm-LB ，確認[類型]為 公用，點選[公用 IP 位址]→[建立新的項目]後，在[名稱]輸入 WebFarm-LB-IP ，然後按[確定]

3.        在[資源群組]點選[使用現有項目]並選取[RG-LAB]，確認[位置]為 東南亞 後，按[建立]

4.        等待負載平衡器建立後，點選[所有資源]後，在訂用帳戶:Azure Pass 字樣下方的篩選欄位內輸入 LB，點選[WebFarm-LB]

5.        點選[健康狀態探查]後，按[新增]

6.        在[名稱]輸入 WebFarm-LB-Probe-http 後，點選[HTTP] ，然後按[確定]

7.        等待更新完成後，點選[後端集區]，然後按[新增]

8.        在[名稱]輸入 WebFarm-LB-Pool1 ，在[關聯對象]選取[可用性設定組]，在[可用性設定組]選取[WebFarm]，然後按一下[新增目標網路 IP 設定]

9.        在[目標虛擬機器]選取[VM1]，在[網路 IP 設定]選取[ipconfig1(172.16.0.4)]，然後再按一下[新增目標網路 IP 設定]

10.    在[目標虛擬機器]選取[VM2]，在[網路 IP 設定]選取[ipconfig1(172.16.0.5)]，然後按一下[確定]

11.    等待更新完成後，點選[負載平衡規則]，然後按[新增]

12.    在[名稱]輸入 WebFarm-LB-WebRule 後，確認通訊協定為 TCP、[連接埠]與[後端連接埠]皆為 80 後，按[確定]

 

設定網路安全性群組        

1.        點選[所有資源]後，在訂用帳戶:Azure Pass 字樣下方的篩選欄位內輸入 NSG，點選[VM1-nsg]

2.        點選[輸入安全性規則]後，按[新增]

3.        在[目的地連接埠範圍]輸入[80]，在[通訊協定]點選[TCP]，然後按[確定]

4.        再次點選[所有資源]後，在訂用帳戶:Azure Pass 字樣下方的篩選欄位內輸入 NSG，點選[VM2-nsg]

5.        點選[輸入安全性規則]後，按[新增]

6.        在[目的地連接埠範圍]輸入[80]，在[通訊協定]點選[TCP]，然後按[確定]

 

測試 Web Farm

1.        點選[虛擬機器]→[VM1]後，按[連接]→[開啟]

2.        按[連接]，輸入 VMAdmin 與 Pa55w.rd1234 後，按[確定]→[是]

3.        在 VM1 桌面出現後，在[Networks]按[No]

4.        開啟 Windows PowerShell (按左下方視窗圖示，再點[Windows PowerShell]

5.        在 Windows PowerShell 中輸入

Install-WindowsFeature  Web-Server  -IncludeManagementTools 後，按 Enter

6.        將遠端桌面連線視窗最小化，回到 Azure Portal

7.        再次點選[虛擬機器]，選取[VM2]後，按[連接]→[開啟]

8.        按[連接]，輸入 VMAdmin 與 Pa55w.rd1234 後，按[確定]→[是]

9.        在 VM1 桌面出現後，在[Networks]按[No]

10.    開啟 Windows PowerShell (按左下方視窗圖示，再點[Windows PowerShell])

11.    在 Windows PowerShell 中輸入

Install-WindowsFeature  Web-Server  -IncludeManagementTools 後，按 Enter

12.    將 VM2 的遠端桌面連線視窗最小化，切換到 VM1 的遠端桌面連線視窗中

13.    開啟檔案總管，找到 C:\Inetpub\wwwroot 中的 iisstart.png，開啟此圖檔進行編輯，加上您容易辨識的文字或圖樣(例如: 1)，然後存檔

14.    將 VM1 的遠端桌面連線視窗最小化，切換到 VM2 的遠端桌面連線視窗中

15.    開啟檔案總管，找到 C:\Inetpub\wwwroot 中的 iisstart.png，開啟此圖檔進行編輯，加上您容易辨識的文字或圖樣(例如: 2)，然後存檔

16.    確認 VM1 與 VM2 的 IIS(Web-Server) 皆已安裝完成後，將 VM1 與 VM2 的遠端桌面連線視窗皆最小化，回到 Azure Portal

17.    點選[所有資源]後，在訂用帳戶:Azure Pass 字樣下方的篩選欄位內輸入 LB，點選[WebFarm-LB]後，記下您的[公用 IP 位址]

18.    在網頁瀏覽器開啟新的頁籤，連到您記下的公用 IP 位址，確認連到的是 VM1 或 VM2

19.    切換到您剛才在網頁瀏覽器所連到的那一部 VM 的遠端桌面連線視窗中

20.    在 Windows PowerShell 執行 services.msc，往下捲動找到[World Wide Web Publishing Service]

21.    對[World Wide Web Publishing Service]按右鍵，選取[Stop]，確認此服務已停止後，將遠端桌面連線視窗最小化

22.    回到您剛才的網頁瀏覽器後，等待十秒鐘，然後將網頁重新整理(按 Ctrl+F5)，您將看到已 failover 到另一部 VM 了

 

使用資訊安全中心為 VM 們安裝 Endpoint Protection

1.        在 Azure Portal 左方我的最愛區塊往下捲動，點選[資訊安全中心]

2.        等待她重新整理完成(需要一會兒)後，點選[計算]，然後點選[Endpoint Protection 問題]，接著點選[Azure VM 上未安裝 Endpoint Protection]

3.        依次按[安裝在兩台 VM 上]→[Mirosoft Antimalware]→[建立]→[確定]

 

附註：完成實作練習後，您可在 Azure Portal 左方我的最愛區塊中點選[虛擬機器]，然後勾選 VM1 及 VM2 前方的 check box 後，按[停止]→[是]，以節省費用。

