---
title: "离线消息对接"
linkTitle: "离线消息对接"
date: 2020-02-06 
weight: 1070
---

如果没有设置离线提供者时，SDK只或收到在线消息。离线消息提供者设置如下:

```Objective-C
 // 离线消息提供者
    [[LIMSDK shared] setOfflineMessageProvider:^(int limit, uint32_t messageSeq, LIMOfflineMessageCallback  _Nonnull callback) {

        // 请求服务器同步消息  
        // max_message_seq: 为当前客户端的最大消息序列号, 接口只会返回大于此序列号的消息 
        // limit:每次同步的消息数量
        [[LIMAPIClient sharedClient] POST:[NSString stringWithFormat:@"message/sync"] parameters:@{@"max_message_seq":@(messageSeq),@"limit":@(limit)}].then(^(NSArray<NSDictionary*>* messageDicts){
            NSMutableArray *messages = [[NSMutableArray alloc] init];
            if(messageDicts && messageDicts.count>0) {
                for (NSDictionary *messageDict  in messageDicts) {
                    [messages addObject:[self toMessage:messageDict]];
                }
                callback(messages,true,nil); // 这里不能判断返回数据小于limit(count>=limit)就没有更多了, 因为有可能服务器遇到解析不出消息里的payload而服务器会丢掉此消息 这样返回数据小于limit但是服务器还有离线消息
            }else {
                callback(messages,false,nil);
            }
        }).catch(^(NSError *err){
            LIMLogError(@"拉去离线消息失败！-> %@",err);
            callback(nil,false,err);
        });

    } offlineMessagesAck:^(uint32_t messageSeq, void (^ _Nonnull complete)(NSError *error)) { // 离线消息ACk回执

        // 告诉服务器客户端最后一次同步到的消息序列号 messageSeq
        [[LIMAPIClient sharedClient] POST:[NSString stringWithFormat:@"message/syncack/%d",messageSeq] parameters:nil].then(^{
            if(complete) {
                complete(nil);
            }
        }).catch(^(NSError *err){
            LIMLogError(@"离线消息回执失败！-> %@",err);
            if(complete) {
                complete(err);
            }
        });

    }];
```