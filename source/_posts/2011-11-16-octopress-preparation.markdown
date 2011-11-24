---
layout: post
title: "Octopress 環境準備"
date: 2011-11-16 15:26
comments: true
categories: blog
author: WanCW
---
## 安裝工具

### 安裝 RVM

{% codeblock lang:sh %}
bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )
echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.zshrc

# 重新登入
{% endcodeblock %}

### 安裝 Ruby 並建立 Gemset

{% codeblock lang:sh %}
rvm install 1.9.2

rvm use 1.9.2
rvm gemset create octopress # 使用獨立的 gemset
{% endcodeblock %}

## 環境設定

### Clone Repository

{% codeblock lang:sh %}
git clone --branch source git@github.com:ecowork/ecowork.github.com.git ecowork.github.com

cd ecowork.github.com
# rvm use 1.9.2@octopress --create

bundle install
{% endcodeblock %}

### 產生 deploy 目錄
{% codeblock lang:sh %}
rake setup_github_pages # 輸入 "git@github.com:ecowork/ecowork.github.com.git"
{% endcodeblock %}

## 撰寫與發佈文章

### 新增文章
{% codeblock lang:sh %}
rake 'new_post[title-of-post]'
# 編輯 source/_posts/YYYY-MM-DD-title-of-post.markdown
{% endcodeblock %}

### 產生靜態頁面
{% codeblock lang:sh %}
rake generate
{% endcodeblock %}

### 在[本地端](http://localhost:4000/)預覽文章
{% codeblock lang:sh %}
rake preview
# 開啟 http://localhost:4000/
{% endcodeblock %}

### 發佈文章至 [GitHub Pages](http://ecowork.github.com)
{% codeblock lang:sh %}
rake deploy
# 開啟 http://ecowork.github.com/
{% endcodeblock %}

### 把文章原始檔 commit 到 GitHub
{% codeblock lang:sh %}
git push origin source
{% endcodeblock %}

## 更多參考資料
* [Octopress 文件](http://octopress.org/docs/)
* [Markdown 文件](http://daringfireball.net/projects/markdown/syntax)
