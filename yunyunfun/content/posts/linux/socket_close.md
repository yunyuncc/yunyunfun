+++ 
draft = true
date = 2019-10-27T19:22:10+08:00
title = "正确关闭socket"
description = ""
slug = "" 
tags = ["linux"]
categories = []
externalLink = ""
series = []
+++
## 如何正确关闭socket,close&shutdown
#### close
`close(fd);`<br>
关闭读写，如果fd的引用计数降为0，释放掉fd相关的资源。
#### shutdown
> shutdown函数只不在继续发送或接收数据，并不释放fd系统资源，后续不再使用该fd的话还是要close,否则会导致资源泄露。<br>
> ##### shutdown read
> `shutdown(fd,SHUT_RD);`<br>
> 关闭读，还是可以发送数据。
> ##### shutdown write
> `shutdown(fd, SHUT_WR);`<br>
> 关闭写，对端会接收到fin(eof),但是还可以接受对端发送过来的数据。
> ##### shutdown read write
> `shutdown(fd, SHUT_RDWR);`<br>
> 关闭读写。

