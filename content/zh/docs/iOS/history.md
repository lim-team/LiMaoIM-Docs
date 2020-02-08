---
title: "历史记录"
linkTitle: "历史记录"
date: 2020-02-06
weight: 1050
---

查询指定频道的历史消息记录

```Objective-C
NSArray<LIMMessage*> *messages =[[LIMSDK shared].chatManager getHistoryMessages:channel oldestClientSeq:0 limit:20];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
channel | LIMChannel | 频道对象
oldestClientSeq | uint32_t | 上次查询到的最新数据的客户端编号，第一次查询则为0
limit | int | 查询消息数量限制