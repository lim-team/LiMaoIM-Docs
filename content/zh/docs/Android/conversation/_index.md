---
title: "最近会话"
linkTitle: "最近会话"
date: 2020-02-06
weight: 1040
---
最近会话表示最近聊天记录的数据。用户发送，收取或删除消息时，都会修改最近会话。

当收到一条消息时，会自动生成该消息对应的最近会话。值得注意的是最近会话不等同于会话，删除最近会话并不会影响会话

**<font color='#2196F3'>查询最近会话</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().queryMsgList();
```

**<font color='#2196F3'>标记某个最近会话为已读/未读</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().updateMsgRedDotCount(channelID, channelType, unreadCount);
```
参数说明:

| 参数        | 类型   | 说明         |
| ----------- | ------ | ------------ |
| channelID   | string | 频道ID       |
| channelType | byte   | 频道类型     |
| unreadCount | int    | 未读消息数量 |


**<font color='#2196F3'>删除某个最近会话</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().deleteMsg(channelID, channelType);
```

参数说明:

| 参数        | 类型   | 说明     |
| ----------- | ------ | -------- |
| channelID   | string | 频道ID   |
| channelType | byte   | 频道类型 |

**<font color='#2196F3'>清空最近会话</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().clearAll();
```

### <font color='#2196F3'>事件</font>
**<font color='#2196F3'>刷新最近会话</font>**
```java
 LiMaoIM.getInstance().getLiMConversationManager().addOnRefreshMsg(new IRefreshConversationMsg() {
            @Override
            public void onRefreshConversationMsg(LiMUIConversationMsg liMUIConversationMsg, boolean b) {
                
            }
        });
```
**<font color='#2196F3'>删除最近会话</font>**
```java
 LiMaoIM.getInstance().getLiMConversationManager().addOnDeleteMsgListener(new IDeleteConversationMsg() {
            @Override
            public void onDelete(String channelID, byte channelType) {
                
            }
        });
```

><font color='#999' size=2>注：会话的置顶、免打扰等是属于channel的管理。请查看[channel管理](../channel/index.md)</font>

