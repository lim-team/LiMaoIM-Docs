---
title: "消息发送"
linkTitle: "消息发送"
date: 2020-02-06
weight: 1033
---

```Objective-C
/**
 发送消息 (发送并保存消息)

 @param content 消息正文
 @param channel 投递的频道
 */
[[LIMSDK shared].chatManager sendMessage:(LIMMessageContent*)content channel:(LIMChannel*)channel];
```