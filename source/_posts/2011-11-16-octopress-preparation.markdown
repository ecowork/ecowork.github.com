---
layout: post
title: "Octopress 環境準備"
date: 2011-11-16 15:26
comments: true
categories: blog
author: WanCW
---
## 環境準備
**安裝 RVM 與 Ruby**
``` sh
bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )

rvm install 1.9.2

rvm use 1.9.2
rvm gemset create octopress # 使用獨立的 gemset
```
**Clone Repository**
``` sh
git clone --branch source git@github.com:ecowork/ecowork.github.com.git ecowork.github.com

cd ecowork.github.com
# rvm use 1.9.2@octopress --create
bundle install
```
**產生 deploy 目錄**
``` sh
rake setup_github_pages # 輸入 "git@github.com:ecowork/ecowork.github.com.git"
```
## 撰寫與發佈文章
**新增文章**
``` sh
rake 'new_post[title-of-post]'
# 編輯 source/_posts/YYYY-MM-DD-title-of-post.markdown
```
**產生靜態頁面**
``` sh
rake generate
```
**在[本地端](http://localhost:4000/)預覽文章**
``` sh
rake preview
# 開啟 http://localhost:4000/
```
**發佈文章至 [GitHub Pages](http://ecowork.github.com)**
``` sh
rake deploy
# 開啟 http://ecowork.github.com/
```
**把文章原始檔 commit 到 GitHub**
``` sh
git push origin source
```

## 更多參考資料
* [Octopress 文件](http://octopress.org/docs/)
* [Markdown 文件](http://daringfireball.net/projects/markdown/syntax)
