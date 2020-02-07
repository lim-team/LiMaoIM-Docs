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

最近会话在LiMaoIMSDK中用LIMConversation类表示,下面展示最近会话的一些关键字段

```Objective-C

@interface LIMConversation : NSObject
...
/**
 最近会话对应的频道，一个最近会话一定对应一个频道。
 */
@property(nonatomic,strong) LIMChannel *channel;
/**
 最近会话的标题（个人频道则为用户昵称，群频道为群名字）
 */
@property(nonatomic,copy) NSString *title;
/**
 最近会话显示的头像（个人频道则为用户头像，群频道为群头像）
 */
@property(nonatomic,copy) NSString *avatar;

/**
 最后一条消息
 */
@property(nonatomic,strong) LIMMessage *lastMessage;


/**
 未读消息数量
 */
@property(nonatomic,assign) NSInteger unreadCount;

/**
 扩展数据（仅本地有效） 
 */
@property(nonatomic,strong) NSDictionary *extra;

...

@end

```