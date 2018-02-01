---
title: 在Ubuntu安裝rvest
date: 2017-11-24 16:41:06
tags: []
categories: ['筆記']
topics: ['筆記']
---


在Ubuntu安裝R語言的rvest套件。
<!--more-->

[rvest](https://github.com/hadley/rvest)是R語言的一個套件，安裝的方式是在R執行
```
install.packages("rvest")
```

之前在Windows的環境下可以應該是直接安裝就可以了，
但換成在Ubuntu，卻無法直接安裝。執行時會出現一些錯誤訊息。


## 錯誤訊息1
>------------------------- ANTICONF ERROR ---------------------------
Configuration failed because libcurl was not found. Try installing:
 * deb: libcurl4-openssl-dev (Debian, Ubuntu, etc)
 * rpm: libcurl-devel (Fedora, CentOS, RHEL)
 * csw: libcurl_dev (Solaris)
If libcurl is already installed, check that 'pkg-config' is in your
PATH and PKG_CONFIG_PATH contains a libcurl.pc file. If pkg-config
is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
>--------------------------------------------------------------------

解決方式：依指示到terminal安裝libcurl4-openssl-dev

```
sudo apt-get update
sudo apt-get install libcurl4-openssl-dev
```



## 錯誤訊息2
>------------------------- ANTICONF ERROR ---------------------------
Configuration failed because openssl was not found. Try installing:
 * deb: libssl-dev (Debian, Ubuntu, etc)
 * rpm: openssl-devel (Fedora, CentOS, RHEL)
 * csw: libssl_dev (Solaris)
 * brew: openssl@1.1 (Mac OSX)
If openssl is already installed, check that 'pkg-config' is in your
PATH and PKG_CONFIG_PATH contains a openssl.pc file. If pkg-config
is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
>--------------------------------------------------------------------

解決方式：依指示到terminal安裝libssl-dev
```
sudo apt-get update
sudo apt-get install libssl-dev
```



## 錯誤訊息3
>------------------------- ANTICONF ERROR ---------------------------
Configuration failed because libxml-2.0 was not found. Try installing:
 * deb: libxml2-dev (Debian, Ubuntu, etc)
 * rpm: libxml2-devel (Fedora, CentOS, RHEL)
 * csw: libxml2_dev (Solaris)
If libxml-2.0 is already installed, check that 'pkg-config' is in your
PATH and PKG_CONFIG_PATH contains a libxml-2.0.pc file. If pkg-config
is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
>--------------------------------------------------------------------

解決方式：依指示到terminal安裝libxml2-dev
```
sudo apt-get update
sudo apt-get install libxml2-dev
```

## 重新安裝
最後再回到R的環境下重新安裝rvest
```
install.packages("rvest")
```

安裝完成後，輸入以下指令確認是否有安裝成功。
```
library(rvest)
```

