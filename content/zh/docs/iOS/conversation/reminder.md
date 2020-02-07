---
title: "显示提醒"
linkTitle: "显示提醒"
date: 2020-02-06
weight: 1044
---

在即时通讯软件中有许多提醒字眼的内容显示，如果下图，在狸猫IM中，我们统一抽象为了 “提醒”功能。

{{<figure src ="../reminder.png" title ="">}}

最近会话对象里包含提醒管理者 提醒管理者可以操作当前最近会话的提醒

```Objective-C


@interface LIMConversation : NSObject

... 

/**
 提醒管理 可以获取到 LIMReminder的集合 和操作LIMReminder的增删改 但是都是临时的不存数据库。
 */
@property(nonatomic,strong) LIMReminderManager *reminderManager;

... 

@end
```

最近会话提醒对象

```Objective-C


@interface LIMReminder : NSObject
/**
 提醒的类型 目前SDK中已声明了   LIMReminderTypeMentionMe 有人@我 LIMReminderTypeDraft 草稿 两个类型
 用户可以根据自己的需求自定义类型 ，一个种类型在一个最近会话里只保留最新的，比如两个人@了我，则只保留最新的@我的信息
 */
@property(nonatomic,assign) LIMReminderType type;
/**
 提醒文本 比如有人@我  则 文本就是 “有人@我”
 */
@property(nonatomic,copy) NSString *text;
/**
 提醒包含的数据 有一些提醒需要用到一些数据，但是大部分提醒都不需要数据，所以此字段非必填
 */
@property(nonatomic,strong) NSDictionary *data;

@end

```

最近会话管理者(LIMConversationManager)可以对提醒进行本地数据库存储

```Objective-C
@interface LIMConversationManager : NSObject
/**
 追加提醒,同时触发最近会话更新的委托
 
 @param reminder 提醒项
 @param channel 频道
 @return 追加后的最近会话
 */
-(LIMConversation*)  appendReminder:(LIMReminder*) reminder channel:(LIMChannel*)channel;


/**
 获取频道里指定类型的提醒

 @param type 提醒类型
 @param channel 频道
 @return <#return value description#>
 */
-(LIMReminder*) getReminder:(LIMReminderType)type channel:(LIMChannel*)channel;


/**
 清除指定频道的所有提醒，同时触发最近会话更新的委托

 @param channel 频道
 */
-(void) clearAllReminder:(LIMChannel*)channel;

@end

```

举例：假设在某个最近会话上显示“[红包]”字眼的提醒  只需要一句代码即可

流程: 监听红包消息 -> 执行下面的代码 （执行下面代码因为会触发最近会话更新的委托，会自动刷新UI显示）

```Objective-C
[[LIMSDK shared].conversationManager appendReminder:[LIMReminder initWithType:LIMReminderTypeRedPacket text:@"[红包]" data:nil] channel:CHANNEL]
```