---
title: "频道资料对接"
linkTitle: "频道资料对接"
date: 2020-02-06
weight: 1060
---

LiMaoIMSDK会判断是否有频道资料，如果SDK没有频道资料 会调用上层设置的ChannelInfoUpdate的block来告知上层需要提供指定channel的频道资料，例子代码如下

```Objective-C
 [[LIMSDK shared] setChannelInfoUpdate:^(LIMChannel * _Nonnull channel,LIMChannelInfoCallback callback) {
        if(channel.channelType == LIM_PERSON) { // 更新个人信息
            // 请求API获取频道资料
            [[LIMAPIClient sharedClient] GET:[NSString stringWithFormat:@"users/%@",channel.channelId] parameters:nil].then(^(NSDictionary* resultDict){
                // 构建LIMChannelInfo
                LIMChannelInfo *channelInfo  = [LIMChannelInfo new];
                channelInfo.channel = [[LIMChannel alloc] initWith:resultDict[@"uid"] channelType:LIM_PERSON]; // 个人频道
                channelInfo.name = resultDict[@"name"]; // 频道名称
                channelInfo.mute = resultDict[@"mute"]?[resultDict[@"mute"] boolValue]:false; // 频道是否免打扰
                channelInfo.stick = resultDict[@"top"]?[resultDict[@"top"] boolValue]:false; // 频道是否置顶
                channelInfo.logo = [NSString stringWithFormat:@"%@%@",[LIMApp shared].config.apiBaseUrl,resultDict[@"avatar"]]; // 频道的logo（头像）

                // 添加或更新频道（调用此方法会触发LIMChannelManagerDelegate的channelInfoUpdate，在此方法里可以做具体UI刷新操作）
                [[LIMSDK shared].channelManager addOrUpdateChannelInfo:channelInfo];
                if(callback) {
                    callback(nil);
                }
            }).catch(^(NSError *error){
                LIMLogError(@"获取频道信息失败！-> %@",error);
                if(callback) {
                    callback(error);
                }
            });
        } else  if(channel.channelType == LIM_GROUP) { //  同步群信息
            
            ...
        }
 }];
```