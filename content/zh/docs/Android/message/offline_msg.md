---
title: "离线消息对接"
linkTitle: "离线消息对接"
date: 2020-02-06 
weight: 1070
---

**<font color='#2196F3'>同步最近会话</font>**
如果没有设置离线消息监听，狸猫sdk只会收取在线消息。
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnSyncConversationListener(new ISyncConversationChat() {
            @Override
            public void syncConversationChat(String last_msg_seqs, int msg_count, long version,  ISyncConversationChatBack iSyncConversationChatBack) {
                // last_msg_seqs     最近会话列表msg_seq集合
                // msg_count         会话里面消息同步数量
                // version           最大版本号
            }
        });
```


**<font color='#2196F3'>同步频道消息</font>**

在离线消息很多的时候，同步最近会话只会同步一部分消息下来。这时点击某个会话消息时下拉查看更多可能存在本地没消息，而服务器存在消息。这时需监听以下方法：
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnSyncChannelMsgListener(new ISyncChannelMsgListener() {
            @Override
            public void syncChannelMsgs(String channelID, byte channelType, long minMessageSeq, long maxMesageSeq, int limit, boolean reverse, ISyncChannelMsgBack iSyncChannelMsgBack) {
            }
        });
```

参数说明:


| 参数          | 类型    | 说明               |
| ------------- | ------- | ------------------ |
| channelID     | String  | 频道ID             |
| channelType   | byte    | 频道类型           |
| minMessageSeq | long    | 最小消息seq        |
| maxMessageSeq | long    | 最大消息seq        |
| limit         | int     | 同步数量           |
| reverse       | boolean | 是否是从大往小获取 |