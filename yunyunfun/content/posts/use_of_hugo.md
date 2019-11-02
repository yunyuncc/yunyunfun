+++ 
draft = true
date = 2019-10-27T14:36:55+08:00
title = "how to use hugo"
description = "hugo的简单使用"
slug = "" 
tags = ["note"]
categories = []
externalLink = ""
series = []
+++
## hugo 的使用
hugo是一个生成静态页面的框架，基于golang实现所以渲染非常快，简单好用<br>
#### 1. 创建一个hugo项目
`hugo new site your_site_name`
#### 2. 给hugo添加一个theme
`git submodule add https://github.com/luizdepra/hugo-coder.git your_site_name/theme`
#### 3. 在content文件夹下添加自己的想写的markdown内容
`hugo new posts/content.md`
#### 4. 启动hugo server 
`hugo server -D --bind 0.0.0.0 --baseURL http://www.wangyunyun.fun/ -p 80 --disableFastRender`

## hugo 的常用概念
#### 1. draft
draft表示草稿，当使用`hugo new xxx.md`创建一个页面的时候会在front matter里面添加一个`draft=true`，表示当前的页面还处于草稿的状态。使用hugo命令渲染页面的时候默认是不会渲染draft的，只有在编写页面内容的时候`hugo server -D`加一个-D参数表示草稿也要渲染。
