---
title: "消息监听"
linkTitle: "消息监听"
date: 2020-02-06
weight: 1030
---

```Objective-C
// 添加委托
[[LIMSDK shared].chatManager addDelegate:self];
```

消息的委托协议 LIMChatManagerDelegate 

```Objective-C
/**
 收到消息通知
 
 @param message 收到的消息
 @param left 消息剩余数量 ，可当left为0时再刷新UI,避免频繁刷新UI导致卡顿
 */
- (void)onRecvMessages:(LIMMessage*)message left:(NSInteger)left;


/**
 消息更新通知
 
 @param message 变化的消息
 */
-(void) onMessageUpdate:(LIMMessage*) message;

...

```