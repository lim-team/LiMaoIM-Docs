---
title: "最近会话"
linkTitle: "最近会话"
date: 2020-02-06
weight: 1040
---

{{% pageinfo %}}
最近会话表示最近聊天记录的数据。用户发送，收取或删除消息时，都会修改最近会话。

当收到一条消息时，会自动生成该消息对应的最近会话。值得注意的是最近会话不等同于会话，删除最近会话并不会影响会话
{{% /pageinfo %}}

**查询最近会话**
```java
LiMaoIM.getInstance().getLiMConversationManager().queryMsgList();
```

**标记某个最近会话为已读/未读**
```java
LiMaoIM.getInstance().getLiMConversationManager().updateMsgRedDotCount(channelID, channelType, unreadCount);
```
参数说明:

| 参数        | 类型   | 说明         |
| ----------- | ------ | ------------ |
| channelID   | string | 频道ID       |
| channelType | byte   | 频道类型     |
| unreadCount | int    | 未读消息数量 |


**删除某个最近会话*
```java
LiMaoIM.getInstance().getLiMConversationManager().deleteMsg(channelID, channelType);
```

参数说明:

| 参数        | 类型   | 说明     |
| ----------- | ------ | -------- |
| channelID   | string | 频道ID   |
| channelType | byte   | 频道类型 |

**清空最近会话**
```java
LiMaoIM.getInstance().getLiMConversationManager().clearAll();
```