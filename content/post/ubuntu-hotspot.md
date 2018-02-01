---
title: Ubuntu設定hotspot
date: 2017-11-21 22:02:45
tags: []
categories: ['筆記']
topics: ['筆記']
---

因為之前用windows的時候，會設定熱點，分享網路給手機使用，
所以希望在Ubuntu也能這麼做。

結果又是各種卡關  崩潰

<!--more-->

1. 連接有線網路

2. 新增hotspot連線
    編輯連線->新增->選「Wi-Fi」->自訂連線名稱。
    第一個標籤（General）勾選「自動連線」。
    第二個標籤（Wi-Fi）自訂SSID，Mode選擇「Hotspot」。
    第三個標籤（Wi-Fi Security），選擇「WPA & WPA2 Personal」，自訂密碼。
    完成後，存檔關閉。

  >參考：[How to Create WiFi Hotspot in Ubuntu 16.04 (Android is Supported) | UbuntuHandbook](http://ubuntuhandbook.org/index.php/2016/04/create-wifi-hotspot-ubuntu-16-04-android-supported/)

3. 啟用Wi-Fi，連接到剛剛新增的連線。
    若成功連接至此連線後，就可以拿起手機測試，看看是否能連到這個熱點。
    不過我是無法連線，卡關卡了好幾天啦...

4. 卡關：設定的過程中，有線網路顯示「Device Not Managed」
    發生的原因不明。

    解決方式是要修改「/etc/NetworkManager/NetworkManager.conf」，
    將「managed=false」修改「managed=true」

    但是此檔案需要root權限，無法直接修改，須執行以下指令：
   ```
   sudo nano /etc/NetworkManager/NetworkManager.conf
   ```

   完成後，重啟網路：

   ```
   sudo service network-manager restart
   ```

    > 參考：[network manager says "device not managed" - Ask Ubuntu](https://askubuntu.com/questions/71159/network-manager-says-device-not-managed) 

5. 卡關：無法連接到第2步新增的連線，顯示錯誤訊息:
    「Connection XXX is not available on the device wlp3s0 at this time.」

    (1) 停用預載的驅動
    System Settings -> Software & Updates -> Additional Drivers
    ->Broadcom corporation: BCM4313 802.11bgn Wireless Network Adapter
    改點選Do not use this device，點選Apply Changes

    (2) 重新安裝驅動
    執行指令
    ```
    sudo apt install firmware-b43-installer」
    ```

    ->出現錯誤訊息
    「"E: dpkg was interrupted, you must manually
    run 'sudo dpkg --configure -a' to correct the problem."」
    
    ->依指示執行
    ```
    sudo dpkg --configure -a
    ```

    ->重新執行指令
    ```
    sudo apt install firmware-b43-installer
    ```

    (3)執行指令重開機
    ```
    sudo reboot
    ```

    >參考：[networking - Created hotspot in ubuntu 16.04 is not able to connect - Ask Ubuntu](https://askubuntu.com/questions/786404/created-hotspot-in-ubuntu-16-04-is-not-able-to-connect/848495)

6. 第5步好不容易成功了，又突然連不上。
    原因不明，重開機就恢復了。

後來用了好幾天都沒再發生問題，但還是覺得一波三折...


