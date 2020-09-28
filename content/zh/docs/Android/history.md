---
title: "历史记录"
linkTitle: "历史记录"
date: 2020-02-06
weight: 1050
---

查询指定频道的历史消息记录

```java
LiMaoIm.getInstance().getMessageManager().getHistoryMsgs(channelId, channelType, maxClientSeq, false, false, pageSize);
```

参数说明:


参数 | 类型 | 说明
---|--- |---
channelId | String | 频道ID
channelType | byte | 频道类型
oldestClientSeq | long | 上次查询到的最新数据的客户端编号，第一次查询则为0
contain | boolean | 是否包含最后一条消息clientseq
desc | boolean | 查询方式 desc或asc
limit | int | 查询消息数量限制

使用场景查看demo中com.limao.im.limkit.chat.ChatActivity文件