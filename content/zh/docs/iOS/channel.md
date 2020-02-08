---
title: "频道管理"
linkTitle: "频道管理"
date: 2020-02-06
weight: 1060
---

## 获取指定频道信息

```Objective-C
LIMChannelInfo *channelInfo = [[LIMSDK shared].channelManager getChannelInfo:channel];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
channel | LIMChannel | 频道对象

## 提取频道信息（走网络）

提取频道信息会调用第三方提供的获取频道信息的方法，更新对应本地数据库的频道数据。调用此方法会触发 LIMChannelManagerDelegate的 channelInfoUpdate 方法通知到UI，UI可获得最新的频道信息数据更新对应界面

```Objective-C
[[LIMSDK shared].channelManager fetchChannelInfo:channel completion:(_Nullable LIMChannelInfoBlock)channelInfoBlock];
```

## 获取指定频道的成员列表

```Objective-C
NSArray<LIMChannelMember*> *members = [[LIMSDK shared].channelManager getMembersWithChannel:channel];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
channel | LIMChannel | 频道对象

## 添加或更新频道信息

```Objective-C
// 单个增加
[[LIMSDK shared].channelManager addOrUpdateChannelInfo:channelInfo];
// 批量增加
[[LIMSDK shared].channelManager addOrUpdateChannelInfos:(NSArray<LIMChannelInfo*>*) channelInfos];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
channelInfo | LIMChannelInfo | 频道信息对象


## 添加或修改频道成员

```Objective-C
[[LIMSDK shared].channelManager addOrUpdateMembers:members];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
members | NSArray<LIMChannelMember*> | 频道成员数组



## 更新频道的设置

***触发LIMChannelManagerDelegate的 channelInfoUpdate***

```Objective-C
[[LIMSDK shared].channelManager updateChannelSetting:channel setting:settingDict];

```

参数说明:


参数 | 类型 | 说明
---|--- |---
channel | LIMChannel | 频道对象
settingDict | NSDictory | 设置的字典 比例设置免打扰 则传 @{@"mute":@(true)} 设置多个 @{@"mute":@(true),@"stick":@(true)}


