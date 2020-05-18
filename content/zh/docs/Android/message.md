---
title: "消息监听"
linkTitle: "消息监听"
date: 2020-02-06
weight: 1030
---

#### 收到消息监听
```java
LiMaoIm.getInstance().getMessageManager().addNewMsgListener(liMMsgList -> {
    //liMMsgList 为收到的消息集合
    //... todo
}
```

#### 消息更改
```java
LiMaoIm.getInstance().getMessageManager().addSendMsgResultListener((clientSeq, messageID, sendStatus) -> {
            // clientSeq 消息本地ID
            // messageID 服务器ID
            // sendStatus 发送结果 返回结果可查看 com.limao.im.limaoimlib.message.type.LiMSendMsgResult
            // ... todo
        });
```