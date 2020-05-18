---
title: "频道管理"
linkTitle: "频道管理"
date: 2020-02-06
weight: 1060
---
## 获取指定频道信息
```java
LiMaoIm.getInstance().getLiMChannelManager().getLiMChannel(channelID, channelType);
```

参数说明:

参数 | 类型 | 说明
---|--- |---
channelID | String | 频道ID
channelType | byte | 频道类型

## 添加或修改频道
```java
//单个操作
LiMaoIm.getInstance().getLiMChannelManager().addOrUpdateChannel(LiMChannel liMChannel);
//批量操作
LiMaoIm.getInstance().getLiMChannelManager().addOrUpdateChannels(List<LiMChannel> list);
```

## 获取指定频道的成员列表 
```java
List<LiMChannelMember> list = LiMaoIm.getInstance().getLiMChannelMemberManager().getLiMChannelMembers(channelID,channelType);
```

参数 | 类型 | 说明
---|--- |---
channelID | String | 频道ID
channelType | byte | 频道类型

## 设置频道置顶
```java
LiMaoIm.getInstance().getLiMChannelManager().updateChannelTop(channelID,channelType, isTop);
```
## 设置频道免打扰
```java
LiMaoIm.getInstance().getLiMChannelManager().updateChannelMute(channelID,channelType, isMute);
```

更多频道设置请查看demo中 com.limao.im.limkit.group.GroupDetailActivity 文件

