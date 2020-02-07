---
title: "概要"
linkTitle: "概要"
date: 2017-01-05
weight: 999
---

## LiMaoIMSDK分为如下几部分

***连接管理(LIMConnectionManager)*** 

* 与IM建立连接或断开连接
* 监听IM连接状态

***聊天管理(LIMChatManager)*** 

* 消息相关的增删改查操作
* 聊天消息的监听


***最近会话管理(LIMConversationManager)***

* 最近会话列表的增删改查操作
* 最近会话列表数据监听

***多媒体文件管理(LIMMediaManager)***

* 消息文件的上传下载
* 消息文件的上传下载监听

***频道管理(LIMChannelManager)***

* 频道数据的增删改操作
* 频道数据变化监听

## [LIMSDK shared]点出一切

所有的管理者都可以通过LiMaoIMSDK提供的[LIMSDK shared]单例对象获取到

```Objective-C
// 连接管理者实例
[LIMSDK shared].connectionManager
// 聊天管理者实例
[LIMSDK shared].chatManager
// 最近会话管理者实例
[LIMSDK shared].conversationManager
// 消息多媒体管理者实例
[LIMSDK shared].mediaManager
// 频道管理者实例
[LIMSDK shared].channelManager
```

## 几乎每个管理者都有委托协议，用于SDK的数据变化通知到UI层

```Objective-C
// 添加委托
[[LIMSDK shared].xxxManager addDelegate:self];
// 移除委托
[[LIMSDK shared].xxxManager removeDelegate:self];

```

UI层与SDK的数据交互流程图

{{<figure src ="../ui-sdk.png" title ="UI层与SDK的数据交互流程图">}}