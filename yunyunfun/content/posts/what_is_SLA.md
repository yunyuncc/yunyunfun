+++ 
draft = true
date = 2019-11-09T18:19:54+08:00
title = "什么是SLA"
description = ""
slug = "" 
tags = []
categories = []
externalLink = ""
series = []
+++
在最近部门里面在推进各个组件的SLA,定义了一系列的SLA指标，并监控我们的组件产生的运营数据，将数据经过统计分析，实时的将SLA通过ODP组件可视化，以此来监控组件的运行情况，如果发现SLA指标有掉坑，通常是组件发生了异常，可以第一时间进行问题排查，尽快使系统恢复正常。缩短故障恢复时间，提高系统的可用性。
availability=MTTF/(MTTF+MTTR)<br>
MTTF:Mean Time To Failure(平均故障前的时间，系统平均运行多久发生一次故障)<br>
MTTR:Mean Time To Recovery(平均故障恢复时间)<br>
所以想要系统的学习一下SLA，并根据公司里面的实践经历融汇贯通。

SLA符合design for failure,分布式系统当中故障不可避免，那么就把故障处理当中系统的一部分，定义好SLA之后可以监控SLA的重要指标，当判断一个集群的SLA指标异常，服务不可用的时候可以故障自动切换使运行正常的集群顶上，同时告警使相关人员介入排查，尽快恢复故障集群。
