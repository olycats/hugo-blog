---
title: 重灌Win7＆安裝Ubuntu前的準備
date: 2017-11-21 19:48:55
tags: []
categories: ['筆記']
topics: ['筆記']
---

手邊的筆電是七年前購買的 Toshiba L640。
硬體設備十分老舊，年久失修，不太夠用，準備要淘汰了。
但卻因為選擇障礙、猶豫不決，一直沒有出手買新筆電。

趁著最近比較有空，不如把舊筆電整理一下，
想試試看雙系統灌Ubuntu，也順便把原本的win7重灌。

因為找不到光碟片，重灌、啟用windows處處卡關，
最後暫時先放棄，把磁區整理好，準備灌Ubuntu。

紀錄一下過程中遇到的困難及解決方法。
<!--more-->

## 重灌windows 7

### 方法1-- 使用原廠還原光碟
使用還原光碟應該是最標準、最建議的作法了，但是我找不到光碟... 

### 方法2-- 系統內建「**一鍵還原**」
查了一下，發現不用還原光碟，也可以使用內建的還原系統，重灌windows。
Toshiba的還原鍵是[0]。
但嘗試過按電源鍵前開始按、看到Toshiba Logo時才開始按、長按、連續按...
試了各種方法都按不出來。
希望落空。

>參考資料： 
 - [輕鬆使用還原鍵，來重灌各廠牌電腦(筆電/桌機)的Windows作業系統](https://mrtang.tw/blog/post/31901145)
 - [藤小二筆電知識-各家筆電還原鍵    (1030916修改)](http://kato3c.pixnet.net/blog/post/283103387)
 
### 方法3-- 製作USB開機隨身碟
先下載win7的映像檔，就可以用
Windows USB/DVD Download Tool ，製作USB開機碟。

>參考資料： 
 - [用「USB隨身碟」安裝、重灌 Windows ，速度大提昇！](https://briian.com/6658/) 

#### 製作USB開機隨身碟

##### 卡關-- win7 映像檔，無法由微軟官網取得 

官網有提供連結，輸入產品金鑰後就可以下載映像檔。 
但輸入筆電授權貼紙的Product Key，卻顯示錯誤：
>您輸入的產品金鑰似乎屬於由裝置製造商預先安裝的軟體。
>請連絡裝置製造商以取得修復軟體選項。

>官網下載連結：
>[下載 Windows 7 光碟映像 (ISO 檔案)](https://www.microsoft.com/zh-tw/software-download/windows7)

##### 解決方法-- 改用Microsoft Windows and Office ISO Download Tool下載映像檔
先下載Microsoft Windows and Office ISO Download Tool，
這個工具不用輸入產品金鑰，就能下載映像檔。

>參考：
>[[問題\] 筆電序號無法至windows官網下載ISO?](https://www.ptt.cc/bbs/Notebook/M.1465043372.A.957.html)
>（一樓的推文=>）
> [從 Microsoft 官方網站免費下載 Windows 7、8.1 及 10 中文光碟映像檔（ISO）教學](https://free.com.tw/download-windows-7-and-8-1-and-10-iso-from-microsoft/)
>（再連結到=>）
>[Windows and Office ISO Downloader 從微軟官方網站免費下載 Windows、Office 安裝程式](https://free.com.tw/windows-and-office-iso-downloader/)

下載完成後，使用映像檔製作開機隨身碟、再用選擇USB開機，
就能順利進入系統還原，沒有遇到什麼困難。
直到系統還原的步驟接近尾聲...又卡關了！！

##### 再次卡關-- 無法啟用windows
輸入產品金鑰顯示錯誤訊息
>Product Key Doesn't Match the Current SKU」
>（當下未紀錄此錯誤訊息，不確定中文完整的句子）

進入window之後，輸入產品金鑰仍然無法啟用。
撥打微軟的語音專線，系統要我輸入產品識別碼，但不知道為什麼一直輸入錯誤。
剩下只能改天上班時間再次撥打，轉客服處理了。

這次主要是想要摸索Ubuntu，所以win7無法啟用的問題，也暫時不想管了。

另外也紀錄一下，作為開機碟的USB隨身碟，已使用的容量是2.6GB，
剛重灌Win7，系統槽已使用的容量是9.16GB。

## windows 7 網路測通
(2017/12/04新增)

### 安裝網卡驅動
本次是使用微軟官方的映像檔安裝，所以由Toshiba預先載入的軟體及驅動都沒有包含在內。
進入控制台=>裝置管理員，發現有四個裝置缺少驅動：
* Ethernet控制卡
* PCI簡單通訊控制器
* 無法辨識的裝置
* 網路控制卡

有線、無線網卡的驅動都有問題，所以想由網路下載驅動也無法，因為無法連線。
我是在Ubuntu的環境下載需要的東西，再放到windows的資料下。

到這個網站：
>[Toshiba - Driver & BIOS Download](https://pc.toshiba-asia.com/support/drivers/)

輸入筆電型號、作業系統，篩選條件勾選「Network」，就可以找到相關的驅動。
需要安裝的兩個驅動，分別是有線及無線網路：
* Atheros LAN Driver
* Broadcom Wireless LAN Driver

下載後直接執行就可以安裝了。

>參考：
> [[心得\] Toshiba NB 驅動程式下載- 看板Notebook - 批踢踢實業坊](https://www.ptt.cc/bbs/Notebook/M.1302076096.A.8C5.html)


### 設定網路連線
設定網路連線，測通網路。
我會把網路連線設定一個捷徑到桌面，並拉一份到啟動區，
這樣在開機時就會自動連上網路了。

### 分享熱點
將前一步驟設定的網路連線設定為共用。
開啟wifi，執行以下語法（需要以系統管理員身份執行）
```
netsh wlan set hostednetwork mode=allow ssid=<熱點要顯示的名稱> key=<連接熱點的密碼>
netsh wlan start hostednetwork
```

## 安裝Ubuntu前的準備--磁碟管理
在重灌的時候，已經把原本的磁區全部刪除，重頭來過。
分配C槽120GB、D槽250GB，剩下90GB左右未配置的磁區，留給Ubuntu使用。

在Ubuntu可以讀取在Windows的檔案，但是不會顯示磁碟代號（C槽、D槽）。
所以我在windows設定磁碟標籤為WIN7(C:)、Data(D:)。
如此一來在Ubuntu就會顯示路徑為/media/olycats/WIN7、/media/olycats/Data。

