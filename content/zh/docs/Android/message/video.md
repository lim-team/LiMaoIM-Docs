---
title: "视频消息"
linkTitle: "视频消息"
date: 2020-02-06
weight: 1030
---

发送视频消息示例:
```java
// 构建正文
LiMVideoContent videoMsgModel = new LiMVideoContent();
videoMsgModel.coverLocalPath = "";
videoMsgModel.localPath = "";
videoMsgModel.size = 0;
videoMsgModel.second = 0;
// 发送
LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(videoMsgModel, channelID, LiMChannelType.PERSONAL);
```

参数说明:


| 参数           | 类型   | 说明             |
| -------------- | ------ | ---------------- |
| coverLocalPath | String | 视频本地封面地址 |
| localPath      | String | 视频本地地址     |
| size           | long   | 视频文件大小     |
| second         | long   | 视频文件时常     |
