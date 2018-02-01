---
title: 在Ubuntu安裝skype
date: 2017-12-06T22:40:49+08:00
tags: []
categories: ['筆記']
topics: ['筆記']
---


在Ubuntu安裝skype

<!--more-->

需要注意的是，網路上查到的大多是舊的文章。
自2017年7月起Skype已經由Canonical’s partner repositories移除，舊的安裝方法已經不適用。

新的方法：
```
wget https://repo.skype.com/latest/skypeforlinux-64.deb
sudo dpkg -i skypeforlinux-64.deb
sudo apt install -f
```

>參考資料：
>[software installation - How do I install Skype? - Ask Ubuntu](https://askubuntu.com/questions/7498/how-do-i-install-skype/932189#932189)

