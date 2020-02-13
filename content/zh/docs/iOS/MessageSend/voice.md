---
title: "语音消息"
linkTitle: "语音消息"
date: 2020-02-06
weight: 1020
---

示例:
```Objective-C
// 构建正文
 LIMVoiceContent *content =[LIMVoiceContent initWithData:voiceData second:second]
 // 发送
 [[LIMSDK shared].chatManager sendMessage:content channel:[[LIMChannel alloc] initWith:@"uid" channelType:LIM_PERSON]];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
voiceData | NSData | 语音数据
second | NSInteger | 秒数