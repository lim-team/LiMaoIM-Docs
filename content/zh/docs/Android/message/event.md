---
title: "消息事件与监听"
linkTitle: "消息事件与监听"
date: 2020-02-06
weight: 1020
---

为了让用户更加精确的了解收发消息进度，狸猫IM提供了丰富的消息监听。

**<font color='#2196F3'>发送消息入库返回</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnSendMsgCallback("listener_key", new ISendMsgCallBackListener() {
            @Override
            public void onInsertMsg(LiMMsg liMMsg) {
                
            }
        });
```
><font size=2 color='#999'>注：该监听只是消息已存库回掉，并非发送返回。在该事件返回中可将消息展示在UI上</font>

**<font color='#2196F3'>发送消息结果返回监听</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().addSendMsgAckListener("listener_key", new ISendACK() {
            @Override
            public void msgACK(long clientSeq, String messageID, long messageSeq, byte reasonCode) {
            }
        })
```
返回字段说明
* `clientSeq` 客户端序列号，可通过该字段判断本地消息唯一性
* `messageID` 服务器消息ID
* `messageSeq` 服务器序列号
* `reasonCode` 消息状态码。发送消息返回状态说明请查看状态码中的[发送消息返回状态码](./../status.md)

><font size=2 color='#999'>注：该监听是指某条消息的发送结果状态，可通过该监听刷新发送消息状态等。</font>

**<font color='#2196F3'>刷新消息监听</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnRefreshMsgListener("listener_key", new IRefreshMsg() {
            @Override
            public void onRefresh(LiMMsg liMMsg, boolean left) {
                // left： true 最后一条消息
            }
        });
```

**<font color='#2196F3'>删除消息监听</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnDeleteMsgListener("listener_key", new IDeleteMsgListener() {
            @Override
            public void onDeleteMsg(LiMMsg liMMsg) {
                // todo
            }
        });
```

**<font color='#2196F3'>上传消息附件监听</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnUploadAttachListener(new IUploadAttachmentListener() {
    @Override
    public void onUploadAttachmentListener(LiMMsg liMMsg, IUploadAttacResultListener iUploadAttacResultListener) {
        // ... 上传附件后返回上传结果
        iUploadAttacResultListener.onUploadResult(true, liMMediaMessageContent);
    }
    });
```

><font size=2 color='#999'>注：如果自定义消息model带附件需继承`LiMMediaMessageContent`，并监听以上方法。</font>




