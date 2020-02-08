---
title: "@消息"
linkTitle: "@消息"
weight: 2030 
---


```Objective-C
// @指定用户
mentionedInfo =  [[LIMMentionedInfo alloc] initWithMentionedType:LIM_Mentioned_Users uids:@[@"uid1",@"uid2"]];
// @所有用户
//mentionedInfo =  [[LIMMentionedInfo alloc] initWithMentionedType:LIM_Mentioned_ALL];

LIMTextContent *content = [[LIMTextContent alloc] initWithContent:text];
content.mentionedInfo =  mentionedInfo;
```