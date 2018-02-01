---
title: Ubuntu安裝、基本設定
date: 2017-11-21 20:10:55
tags: []
categories: ['筆記']
topics: ['筆記']
---


第一次安裝Ubuntu，
事先沒有做太多功課，隨意摸索，遇到問題才去找解答。
以此篇紀錄一下步驟、以及過程中遇到的困難。
<!--more-->

## 安裝Ubuntu

1. 下載Ubuntu桌面版本 - 16.04 LTS - 64 位元版本，下載的是.iso光碟映像檔。

2. 下載、執行UNetbootin。
    有兩個選項「發行版」、「映像檔」。
    選擇「映像檔」，路徑選擇第一步下載的映像檔，
    再選擇要使用的USB隨身碟，再按確定即可。
    ＊如果沒有先下載映像檔，在這裡也可以點選「發行版」，
      會自動下載對應的映像檔。

3. 重開機、使用USB開機，接下來就跟著指示安裝Ubuntu即可。

4. 本電腦目前安裝有多套作業系統，請問要怎麼處理？
    「將Ubuntu與他們安裝在一起」、「清除磁碟並安裝Ubuntu」
    因為要灌雙系統所以選擇第一個「將Ubuntu與他們安裝在一起」

5. 第一次安裝時我選擇中文，但覺得中文化不算那麼完整，
    正式安裝時改選English(US)。

6. 製作Live USB的隨身碟已使用的容量是1.6GB。
    安裝Ubuntu的磁區，安裝完已使用的容量是3.8GB。

> Ubuntu下載：[下載Ubuntu | Ubuntu 正體中文站](https://www.ubuntu-tw.org/modules/tinyd0/) 
> UNetbootin：[UNetbootin - Homepage and Downloads](https://unetbootin.github.io/)
> 參考：[Ubuntu 16.04製作Live USB隨身碟的軟體Unetbootin](http://blog.xuite.net/yh96301/blog/57645340)


## Ubuntu安裝的重要設定

### 網路測通

目前是使用中華電信的有線網路，需要登入使用者名稱、密碼。

1. 新增連線
    編輯連線->新增->選「DSL」->自訂連線名稱->輸入使用者名稱、密碼。
    第一個標籤（General）勾選「自動連線」

2. 開啟內建瀏覽器firefox
    測試看看是否網路有通。

3. 測試 (https://tw.yahoo.com/)
    測試看看會不會跑很久、等好幾分鐘網頁都跑不出來。
    剛好在PTT看到這個問題，解決方法是輸入指令
    ```
    sudo pppoeconf
    ```
   依照指示操作完成後，測試網頁可以正常開啟（30秒內）

> 參考：
> [[問題\] Ubuntu 16.04瀏覽某些網頁速度超慢- 看板Linux - 批踢踢實業坊](https://www.ptt.cc/bbs/Linux/M.1499242463.A.249.html) 
> [Re: [問題\] Ubuntu 16.04瀏覽某些網頁速度超慢- 看板Linux - 批踢踢實業坊](https://www.ptt.cc/bbs/Linux/M.1501682884.A.DA4.html)

### 設定新酷音輸入法

System Settings -> Language Support ->
Install / Remove Languages -> 勾選Chinese (traditional)

Keyboard input method system 選擇fcitx

此時可能需要重開Ubuntu

在輸入法那邊，點選「ConfigureFcitx」，新增「Chewing」
即完成新增新酷音輸入法。

覺得跟微軟的新注音操作不太一樣，目前不太順手，還在適應中。

