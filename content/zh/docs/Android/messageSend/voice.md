---
title: "语音消息"
linkTitle: "语音消息"
date: 2020-02-06
weight: 1020
---

示例:
```java
// 构建正文
 LiMVoiceContent audioMsgModel = new LiMVoiceContent(localPath, timeTrad);
 // 发送
 LiMaoIm.getInstance().getLiMConnectionManager().sendMessage(audioMsgModel, channelID, LiMChannelType.PERSONAL, callBack);
```

参数说明:


参数 | 类型 | 说明
---|--- |---
localPath | NSData | 语音文件本地地址
timeTrad | NSInteger | 秒数