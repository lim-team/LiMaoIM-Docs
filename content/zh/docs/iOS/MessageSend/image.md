---
title: "图片消息"
linkTitle: "图片消息"
date: 2020-02-06
weight: 1010
---

示例:
```Objective-C
// 构建正文
 LIMImageContent *content = [LIMImageContent initWithImage:image];
 // 发送
 [[LIMSDK shared].chatManager sendMessage:content channel:[[LIMChannel alloc] initWith:@"uid" channelType:LIM_PERSON]];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
image | UIImage | 图片对象