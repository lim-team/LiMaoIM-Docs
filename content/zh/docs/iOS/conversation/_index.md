---
title: "最近会话"
linkTitle: "最近会话"
date: 2020-02-06
weight: 1040
---

{{% pageinfo %}}
最近会话用于表示会话列表页的数据模型。当用户发送，收取及删除消息时，都会同时去修改最近会话。

当收到或者一条消息时，会自动生成这个消息对应的最近会话。但值得注意的是最近会话和会话并不是一一对应的关系，删除最近会话并不会影响会话
{{% /pageinfo %}}



```Objective-C
// 添加委托
[[LIMSDK shared].conversationManager addDelegate:self];
```

最近会话的委托协议 LIMConversationManagerDelegate 

```Objective-C

...

/**
  当最近会话被新增的时候会调用此方法

 @param conversation 最近会话对象
 @param left 会话剩余数量 UI层可以判断left == 0 的时候才刷新 避免频繁刷新UI导致卡顿
 */
- (void)onConversationAdd:(LIMConversation*)conversation left:(NSInteger)left;


/**
 当最近会话对象更新的时候会调用此方法

 @param conversation 最近会话对象
 @param left 会话剩余数量 UI层可以判断left == 0 的时候才刷新 避免频繁刷新UI导致卡顿
 */
- (void)onConversationUpdate:(LIMConversation*)conversation left:(NSInteger)left;

/**
 最近会话未读数发送改变
 
 @param channel 频道
 @param unreadCount 未读数量
 */
- (void)onConversationUnreadCountUpdate:(LIMChannel*)channel unreadCount:(NSInteger)unreadCount;

...

```

查询所有最近会话数据

```Objective-C
NSArray<LIMConversation*> *conversations =[[LIMSDK shared].conversationManager getConversationList];

```