---
title: "消息收发"
linkTitle: "消息收发"
date: 2020-02-06
weight: 1033
---

**发送消息**
```java
LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(liMBaseContentMsgModel, channelID, channelType);
```

参数说明:

| 参数                   | 类型              | 说明      |
| ---------------------- | ----------------- | --------- |
| liMBaseContentMsgModel | LiMMessageContent | 消息model |
| channelID              | string            | 频道ID    |
| channelType            | byte              | 频道类型  |

为了满足更多的业务情况，我们有时需要发送一条不需要存储的消息给对方。这个时候就需要用以下方法
```java
LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(liMMsg);
```
>注：`LiMMsg`中的`no_persist`字段设置为true，标识本条消息发送方和接收方都不会存储。`red_dot`设置为`false`接收方收到消息不会显示红点。

**新消息监听**

```java
LiMaoIM.getInstance().getLiMMsgManager().addOnNewMsgListener("listener_key", new INewMsgListener() {
            @Override
            public void newMsg(List<LiMMsg> list) {
                // todo ...
            }
        });
```
