---
title: "收/发消息"
linkTitle: "收/发消息"
date: 2020-03-25
weight: 1030
---

## 收消息

```Javascript
lim.addMessageListener((message)=>{
    console.log('收到消息->',message);
});
```


## 发消息

```Javascript
lim.sendMessage(payload,channel) //  lim.sendMessage({type:1,content:this.msg},{channelID:this.to,channelType:1})
```

payload： 消息负载 具体见附件 例如文本消息： {type:1,content:'hello'}

channel: 接受消息的频道， channelType为频道类型 1.个人频道 2.群聊频道 channelID为频道唯一ID 如果channelType=1则channelID为用户uid 如果channelType=2 channelID为群组唯一ID

#### 监听发送的消息

```Javascript
// 发送消息
lim.addSendMessageListener((sendPacket)=>{
    console.log("发送消息！",sendPacket.clientSeq);
});
```

#### 监听发送消息回执
可以通过监听发送消息回执来判断消息有没有发送成功
```Javascript
// 发送消息
lim.addMessageStatusListener((sendackPacket)=>{
    if(sendackPacket.reasonCode == 1) { 
        console.log("发送成功！",sendackPacket.clientSeq);
    }else {
        console.log("发送失败！",sendackPacket.clientSeq);
    }
});
```
