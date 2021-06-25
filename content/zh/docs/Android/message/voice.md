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
 LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(audioMsgModel, channelID, LiMChannelType.PERSONAL);
```

参数说明:


| 参数      | 类型   | 说明             |
| --------- | ------ | ---------------- |
| localPath | String | 语音文件本地地址 |
| timeTrad  | int    | 时常             |