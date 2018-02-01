---
title: Ubuntu-R語言
date: 2017-11-22T02:42:51+08:00
tags: []
categories: ['筆記']
topics: ['筆記']
---

Ubuntu 16.04 LTS 安裝R以及RStudio
<!--more-->

## 安裝R

到R官網底下的[R CRAN Mirrors](https://cran.r-project.org/mirrors.html)，依所在地區選擇一個點進去，

> R 官網：
>[R: The R Project for Statistical Computing](https://www.r-project.org/)

我選擇離我最近的：[National Taiwan University, Taipei ](http://cran.csie.ntu.edu.tw/)

點選[Download R for Linux](http://cran.csie.ntu.edu.tw/bin/linux/)點選[ubuntu](http://cran.csie.ntu.edu.tw/bin/linux/ubuntu/)
再點選[README.html](http://cran.csie.ntu.edu.tw/bin/linux/ubuntu/README.html)，裡面會說明如何安裝R的方法。


首先要先知道自己的ubuntu版本，例如我是16.04，那就是「xenial」
不知道怎麼對應的話，[Ubuntu Wiki](https://wiki.ubuntu.com)可以查：
>[Releases - Ubuntu Wiki](https://wiki.ubuntu.com/Releases)

所以帶入CRAN的網址、以及Ubuntu版本，
我要安裝R，要先在「/etc/apt/sources.list」這個檔案加入：
「deb http://cran.csie.ntu.edu.tw/bin/linux/ubuntu xenial/」

但因為「/etc/apt/sources.list」是唯讀，
要打指令才能作修改這個檔案：
```
sudo nano /etc/apt/sources.list
```

加入完成後，再執行指令：
```
sudo apt-get update
sudo apt-get install r-base
sudo apt-get install r-base-dev
```

這樣就安裝完成了。

## 安裝RStudio

1. 至RStudio官方網站，選擇對應的作業系統下載

    > 下載RStudio：[Download RStudio – RStudio](https://www.rstudio.com/products/rstudio/download/#download)


2. 下載完卻不知道如何安裝...
    只能以指令安裝(後面帶的是第一步下載Rstudio的路徑，請自行修改)
    ```
    sudo dpkg -i /tmp/mozilla_olycats0/rstudio-xenial-1.1.383-amd64.deb
    ```

    執行後會顯示一些錯誤訊息，應是有一些套件沒有安裝。
    執行
    ```
    sudo apt-get -f install
    ```
    再重新執行安裝
    ```
    sudo dpkg -i /tmp/mozilla_olycats0/rstudio-xenial-1.1.383-amd64.deb
    ```

    > 參考：[Installing RStudio Desktop on Ubuntu 16.04 LTS – RStudio Support](https://support.rstudio.com/hc/en-us/community/posts/209074748-Installing-RStudio-Desktop-on-Ubuntu-16-04-LTS)

