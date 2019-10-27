+++ 
draft = true
date = 2019-10-27T15:42:47+08:00
title = "design of malice"
description = "malice 设计记录"
slug = "" 
tags = ["malice"]
categories = []
externalLink = ""
series = []
+++

event是对struct epoll_event的简单包装。<br>
## 对象关系
#### event和channel的关系
一个channel会接管一个fd的生命周期,构造channel的时候交给它的fd必须是valid的fd，channel在析构的时候负责close fd。
event和fd属于一个channel，channel析构的时候会先清理(unregist)掉fd相关的event,然后close掉fd, 这个时候自然也就不会有event发生了,channel是fd和fd对应的event的拥有者，控制它们的生命周期。<br>
#### event和event_loop的关系
event_loop和event是关联关系,类似于observer模式，fd的event regist到event_loop当中，当event_loop发现底层fd关注的event发生的时候，会调用该event的回调函数来notify。当不在关注fd的事件的时候就要从event_loop中unregist,这样event_loop就不会再notify该event了。<br>
event_loop里面只保存了event的row ptr,所以event不能在event_loop之前析构掉，或者event析构的时候一定要先从event_loop中unregist，所以event_loop不能比注册到它这里的event早析构，所以event应该持有event_loop的shared_ptr。


