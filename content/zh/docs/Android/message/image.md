---
title: "图片消息"
linkTitle: "图片消息"
date: 2020-02-06
weight: 1010
---

发送图片消息示例:
```java
// 构建正文
LiMImageContent imgMsgModel = new LiMImageContent(localPath);
// 发送
LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(imgMsgModel, channelID, LiMChannelType.PERSONAL);
```

参数说明:
| 参数      | 类型   | 说明         |
| --------- | ------ | ------------ |
| localPath | String | 图片本地地址 |