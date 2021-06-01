---
title: "消息发送"
linkTitle: "消息发送"
date: 2020-02-06
weight: 1033
---

```java
/**
* 发送消息
*
* @param liMBaseContentMsgModel 消息model
* @param channelID              投递频道ID
* @param channelType            投递频道类型
*/
LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(liMBaseContentMsgModel, channelID, channelType);
```

参数说明:

参数 | 类型 | 说明
---|--- |---
liMBaseContentMsgModel | LiMMessageContent | 消息model
limReminderType | int | 提醒类型
channelID | string | 频道ID
channelType | byte | 频道类型