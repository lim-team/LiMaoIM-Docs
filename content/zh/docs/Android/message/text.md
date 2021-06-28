---
title: "文本消息"
linkTitle: "文本消息"
date: 2020-02-06
weight: 1000
---

发送文本消息示例:
```java
// 构建正文
 LiMTextContent textMsgModel = new LiMTextContent("我是文本消息");
 // 发送
 LiMaoIM.getInstance().getLiMConnectionManager().sendMessage(textMsgModel, channelID, LiMChannelType.PERSONAL);
```

参数说明:
参数 | 类型 | 说明
---|--- |---
content | string | 文本内容