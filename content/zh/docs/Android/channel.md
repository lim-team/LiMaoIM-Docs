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

## 频道信息改变监听
```java
LiMaoIm.getInstance().getLiMChannelManager().addOnRefreshChannelInfo(liMChannel ->{
    //回调是在主线程，刷新UI等。
    .....
});
```
## 频道成员信息改变监听
```java
LiMaoIm.getInstance().getLiMChannelMemberManager().addOnRefreshChannelMemberInfo(liMChannelMember -> {
    //todo
});
```
## 移除频道成员监听
```java
LiMaoIm.getInstance().getLiMChannelMemberManager().addOnRemoveChannelMemberListener(list -> {
    //这里可用于监听群成员被移除等
});
```
## 添加频道成员监听
```java
LiMaoIm.getInstance().getLiMChannelMemberManager().addOnAddChannelMemberListener(list -> {
    //这里可用于监听添加群成员等
});
```
更多频道设置请查看demo中 com.limao.im.limkit.group.GroupDetailActivity 文件

