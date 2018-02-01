---
title: hexo on Github pages
date: 2017-11-23T15:52:30+08:00
tags: []
categories: ['筆記']
topics: ['筆記']
---

在Github Pages使用hexo建立blog
<!--more-->

>hexo官方文件：
>[文件 | Hexo](https://hexo.io/zh-tw/docs/)

>參考教學：
>[使用 Hexo + Github 建立個人網誌 ](http://lodur46.blogspot.tw/2016/04/hexo-github.html)
>[建立個人部落格 ](https://sean.life/2016/09/16/Create-a-personl-blog-website/)
>[Hexo 安裝教學、心得筆記 | printf(" I'm EricWang ")](https://wwssllabcd.github.io/blog/2014/12/22/how-to-install-hexo/)


## 安裝

### 安裝git

```
sudo apt-get install git-core
```

### 安裝 Node.js

先安裝nvm(Node Version Manager)
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```

重啟終端機後執行
```
nvm install stable
```

### 安裝hexo
git、Node.js都安裝完畢後，即可透過 npm 安裝 Hexo

```
npm install -g hexo-cli
```

## 建立Hexo
Hexo 會在指定資料夾中建立所有需要的檔案。 
```
hexo init <folder>
cd <folder>
npm install
```

## 建立Github Pages
[Github Pages官方教學](https://pages.github.com/)
如果要使用hexo，只要做第一步「Create a repository」
建立一個repository，命名為「<username>.github.io」
就可以我的建立Github Page，網址「https://<username>.github.io」

## hexo 配置
要調整~\hexo\_config.yml這個檔案的內容

如果要deploy到Github，以下這裡一定要設定
>deploy: 
>  type: git
>  repo: git@github.com:olycats/olycats.github.io.git

## hexo 佈署

### 安裝Git插件
```
npm install hexo-deployer-git --save
```

### 設定ssh
因為第一次無法成功deploy，設定ssh後才能成功。

```
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen -t rsa -C "your_email@example.com"
```

一路enter
找到~/.ssh/id_rsa.pub這個檔案，複製裡面內容
貼到 https://github.com/settings/keys

設定
```
git config --global user.name "yourusername"
git config --global user.email "your_email@example.com
```

## hexo基本指令

```
cd ~/hexo
```

新增文章(layout： post、page、draft)
```
hexo new [layout] <title>
```

將草稿發布
```
hexo publish [layout] <title>
```

```
hexo g # 產生 blog
hexo s # 讓 blog 可以在 local 端檢視
hexo s --draft # 含草稿
hexo d # 佈署
hexo clean
```

## Github - 刪除多餘的commit紀錄

>參考：
>[將github上的多筆commits合併成為一條commit](http://itspg.github.io/blog/2013/01/13/git-squash-master-commits/)
>[fosshelp: How To GitHub delete a commit](http://fosshelp.blogspot.tw/2015/05/how-to-github-delete-commit.html)

因為是使用hexo，所以目錄要移動到hexo底下的git目錄，以下是我實際操作的步驟。

先cd到hexo底下的git目錄
```
cd ~/hexo/.deploy_git
git log
```

git log 查出來的結果
```
commit af69ef2ccae4e83fd57afbd4cc6b65002ee6ebec

​    Site updated: 2017-11-21 00:06:14

commit b5b379e950729bd54d0b1c18122a0b2a83d39df9

​    First commit
```

將Head退回到First commit，再重新deploy
```
git checkout master
git reset --hard b5b379e950729bd54d0b1c18122a0b2a83d39df9
cd ~/hexo/
hexo d
```

## 套用主題
>[Themes | Hexo](https://hexo.io/themes/)


## Markdown

### Markdown中文介紹
>[Markdown 文件](http://markdown.tw/)

### markdown editor - typora

>[Typora — a minimal markdown editor, markdown reader.](https://typora.io/)
>[Install Typora on Linux](https://typora.io/#linux)

```
\# optional, but recommended
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
\# add Typora's repository
sudo add-apt-repository 'deb http://typora.io linux/'
sudo apt-get update
\# install typora
sudo apt-get install typora
```

### markdown editor - stackedit

>[StackEdit – In-browser markdown editor](https://stackedit.io/)



