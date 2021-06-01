---
title: "消息监听"
linkTitle: "消息监听"
date: 2020-02-06
weight: 1030
---

**收到消息监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnNewMsgListener("listener_key", new INewMsgListener() {
            @Override
            public void newMsg(List<LiMMsg> list) {
                // todo ...
            }
        });
```
**发送消息返回监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addSendMsgAckListener("listener_key", new ISendACK() {
            @Override
            public void msgACK(long clientSeq, String messageID, long messageSeq, byte reasonCode) {
                // clientSeq 客户端序列号
                // messageID 服务器消息ID
                // messageSeq 服务器序列号
                // reasonCode 消息状态码【0:发送中1:成功2:发送失败3:不是好友或不在群内4:黑名单】
            }
        })
```

**消息刷新监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnRefreshMsgListener("listener_key", new IRefreshMsg() {
            @Override
            public void onRefresh(LiMMsg liMMsg, boolean left) {
                // left： true 最后一条消息
            }
        });
```

**消息附件监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnUploadAttachListener(new IUploadAttachmentListener() {
    @Override
    public void onUploadAttachmentListener(LiMMsg liMMsg, IUploadAttacResultListener iUploadAttacResultListener) {
        // ... 上传附件
        iUploadAttacResultListener.onUploadResult(true, liMMediaMessageContent);
    }
    });
```
说明：
如果自定义消息model带附件需继承LiMMediaMessageContent，并监听以上方法。

**删除消息监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnDeleteMsgListener("listener_key", new IDeleteMsgListener() {
            @Override
            public void onDeleteMsg(LiMMsg liMMsg) {
                // todo
            }
        });
```