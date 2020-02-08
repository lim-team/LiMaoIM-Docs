---
title: "自定义消息"
linkTitle: "自定义消息"
weight: 2010 
---

为了更好的满足大部分需求，狸猫IM提供自定义消息。自定义消息分三部走，这里以自定义一个GIF消息举例

1. 继承LIMMessageContent和定义消息的字段

```Objective-C
@interface LIMGIFContent : LIMMessageContent
//GIF的地址
@property(nonatomic,copy) NSString *url;
// GIF图片宽度
@property(nonatomic,assign) NSInteger width;
// GIF图片高度
@property(nonatomic,assign) NSInteger height;
@end
```

2. 实现消息的编码和解码 

```Objective-C
@implementation LIMGIFContent

// 解码消息
- (void)decodeWithJSON:(NSDictionary *)contentDic {
    self.url = contentDic[@"url"];
    self.width = contentDic[@"width"]?[contentDic[@"width"] integerValue]:100;
    self.height = contentDic[@"height"]?[contentDic[@"height"] integerValue]:100;
}

// 编码消息
- (NSDictionary *)encodeWithJSON {
    NSMutableDictionary *dataDict = [NSMutableDictionary dictionary];
    [dataDict setObject:self.url?:@"" forKey:@"url"];
    [dataDict setObject:@(self.width) forKey:@"width"];
    [dataDict setObject:@(self.height) forKey:@"height"];
    return dataDict;
}

// 指定消息的正文类型
+(NSInteger) contentType {
    return LIM_GIF;
}

@end
```

3. 注册消息

```Objective-C
[[LIMSDK shared] registerMessageContent:LIMGIFContent.class];
```

```
如果使用了狸猫IM的UI库，则具体定义消息UI的流程搜索LIMGIFContent和LIMGIFMessageCell查看具体代码
```