---
title: "文本消息"
linkTitle: "文本消息"
date: 2020-02-06
weight: 1000
---

示例:
```Objective-C
// 构建正文
 LIMTextContent *content = [[LIMTextContent alloc] initWithContent:@"这是一条测试消息"];
 // 发送
 [[LIMSDK shared].chatManager sendMessage:content channel:[[LIMChannel alloc] initWith:@"uid" channelType:LIM_PERSON]];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
content | string | 文本内容