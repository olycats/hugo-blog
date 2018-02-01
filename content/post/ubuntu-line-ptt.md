---
title: 在Ubuntu使用line、ptt
date: 2017-11-22T02:42:40+08:00
tags: []
categories: ['筆記']
topics: ['筆記']
---

安裝Google Chrome、LINE、用Ubuntu上PTT
<!--more-->

## Google Chrome 

內建的firefox就很好用了，安裝Google Chrome其實是因為要安裝LINE啦！

嘗試過直接由網頁下載Chrome，卻無法安裝，只好用下指令的方式安裝。

1. 下載：
    ```
    wget -c https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    ```

2. 安裝： 
    ```
    sudo dpkg -i google-chrome-stable_current_amd64.deb
    ```

3. 安裝過程中發生錯誤，似乎有套件未安裝，執行：
    ```
    sudo apt-get install -f
    ```

4. 再重新安裝： 
    ```
    sudo dpkg -i google-chrome-stable_current_amd64.deb
    ```

> 參考：[如何下指令安裝Google Chrome - Ubuntu 問答集](http://samwhelp.github.io/book-ubuntu-qna/read/case/app/google-chrome/install)


## LINE
開啟Google Chrome瀏覽器，用Chrome webstore安裝LINE：
> [LINE - Chrome 線上應用程式商店 - Google](https://chrome.google.com/webstore/detail/line/menkifleemblimdogmoihpfopnplikde)

安裝完成後，就可以直接使用了。
但和android版本、windows版本，比起來還是少了許多功能，只能勉強用囉。
另一個方法是安裝wine，或許就可以安裝windows版本的LINE了。

## 瀏覽PTT
在Ubuntu瀏覽PTT有很多方法，例如：PCManX、BBSFox、PttChrome...
先試了最陽春的，直接用termial上PTT，執行:
```
ssh bbsu@ptt.cc
```
意外發現也滿好用的，畫面也算好看，那就先用這個就好XD

> 參考：
> [Re: [問題\] ubuntu連ptt - 看板Linux - 批踢踢實業坊](https://www.ptt.cc/bbs/Linux/M.1420257790.A.C74.html)
> [Ubuntu 上瀏覽ptt | Tseng C. T.'s blog](https://cttseng.wordpress.com/2015/11/05/ubuntu-%E4%B8%8A%E7%80%8F%E8%A6%BD-ptt/)
