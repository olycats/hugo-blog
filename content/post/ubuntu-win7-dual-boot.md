---
title: Ubuntu/Windows7雙系統
date: 2017-11-21T20:24:07+08:00
tags: []
categories: ['筆記']
topics: ['筆記']
---


前一篇剛安裝完成Ubuntu，並完成基本設定。
完成後想重開機，重新登入windows，發現在windows的時間怎麼差了八小時！！

另外一開始只是抱著嘗試的心態在安裝Ubuntu，
後來想先移除，還原成只有win7單一作業系統，
才發現忘了先研究還原的方法，亂按一通結果差點開不了機XD
<!--more-->

## 系統日期、時間確認

安裝完Ubuntu後重新登入Windows，
發現windows系統日期時間，與實際時間差了八個小時。

這是因為每次在開機時，會透過BIOS讀取硬體時鐘，作為作業系統的系統時間。
Ubuntu預設讀取/寫入硬體時鐘的是UTC時間而Windows預設讀取/寫入硬體時鐘的是Local Time。
不同作業系統對於硬體時鐘的認定不同，造成在同一台電腦安裝兩個作業系統，會發生系統時間的衝突。

解決方法是在Ubuntu執行指令
```
timedatectl set-local-rtc 1
```
將Ubuntu調整為使用Local Time。

完成後即可重新登入windows，驗證系統日期時間正確性。
> 參考：[windows - Clock time is off on dual boot - Ask Ubuntu](https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)

> 以下引用自：[UbuntuTime - Community Help Wiki - Official Ubuntu Documentation](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
> Multiple Boot Systems Time Conflicts 
> Operating systems store and
>  retrieve the time in the hardware clock located on your motherboard so 
> that it can keep track of the time even when the system does not have 
> power. Most operating systems (Linux/Unix/Mac) store the time on the 
> hardware clock as UTC
>  by default, though some systems (notably Microsoft Windows) store the 
> time on the hardware clock as the 'local' time. This causes problems in a
>  dual boot system if both systems view the hardware clock differently.

## 移除Ubuntu的方法

### 1. 錯誤的作法，請不要學我！！

在Windows的磁碟管理，可以看到我之前切的C槽、D槽，
再後面有兩個磁區，被分配給Ubuntu使用。

我把那兩個分配給Ubuntu的磁區，點選「刪除磁區」，
傻傻的以為，這樣就能把Ubuntu刪除，復原到之前的樣子。

然後再重開機的時候，才發現我做錯了...

開機時仍然是預設進入GNU GRUB的開機選單，
也就是安裝完Ubuntu後，開機時都會出現，可以選擇要進入Ubuntu或windows的那個畫面。
但是因為之前安裝Ubuntu的磁區已經被刪掉，無法正常進入GNU GRUB。

總之就是造成一個Ubuntu已經被移除、但卻無法進入windows的窘境。

我的解決辦法是拿出之前安裝Ubuntu的USB隨身碟，
先把Ubuntu重新安裝，再重頭來過。

### 2. 正確的作法

#### 使用EasyBCD調整MBR
正確的作法必須調整MBR，這樣下一次開機時，
就可以還原到安裝Ubuntu之前，開機直接進入Windows作業系統。

(1) 下載、開啟工具「EasyBCD」
(2) BCD部屬->安裝 Windows Vista/7 Bootloader 到 MBR->寫入MBR。
(3) 編輯開機選單->略過開機選單->儲存設定。

#### 刪除Ubuntu所在的磁區
調整MBR後，建議先重開機，確認開機後是直接進入Windows作業系統。
確認無誤後，再將Ubuntu所在的磁區刪除。

> 參考：[[知識\] 如何從 Win7/Linux 雙系統中安全移除Linux作業系統](http://bruce30262.pixnet.net/blog/post/105625688) 
> 下載EasyBCD：[EasyBCD - NeoSmart Technologies](http://neosmart.net/EasyBCD/)

