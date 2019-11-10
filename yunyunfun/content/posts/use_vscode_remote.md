+++ 
draft = true
date = 2019-11-09T17:36:36+08:00
title = "use vscode remote"
description = ""
slug = "" 
tags = []
categories = []
externalLink = ""
series = []
+++
### 1.windows上使用power shell安装openssh
#### 查看是否安装
    Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'
#### Install the OpenSSH Client
    Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
#### Install the OpenSSH Server
    Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
### 2.本地window上生成ssh key
使用power shell运行 `ssh-keygen -t rsa -b 4096`命令，会在本地生成id_rsa私钥和id_rsa.pub公钥<br>
### 3.将本地生成的公钥拷贝到远程的服务器上
我这里的路径是/root/tmp/id_rsa.pub
### 4.将本地的公钥保存到远程服务器的~/.ssh/authorized_keys当中
执行命令:<br>
`cat /root/tmp/id_rsa.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f /root/tmp/id_rsa.pub`<br>
### 5.通过vscode 的remote-ssh插件配置要链接的远程服务器的ip,port
