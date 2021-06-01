---
title: "频道管理"
linkTitle: "频道管理"
date: 2020-02-06
weight: 1060
---
**获取指定频道信息**
```java
LiMaoIM.getInstance().getLiMChannelManager().getLiMChannel(channelId, channelType);
```

参数说明:

参数 | 类型 | 说明
---|--- |---
channelID | String | 频道ID
channelType | byte | 频道类型

**添加或修改频道**
```java
//单个操作
LiMaoIM.getInstance().getLiMChannelManager().addOrUpdateChannel(LiMChannel liMChannel);
//批量操作
LiMaoIM.getInstance().getLiMChannelManager().addOrUpdateChannels(List<LiMChannel> list);
```

**获取指定频道的成员列表**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().getLiMChannelMembers(channelID, channelType);
```

参数 | 类型 | 说明
---|--- |---
channelID | String | 频道ID
channelType | byte | 频道类型

**设置频道置顶**
```java
LiMaoIM.getInstance().getLiMChannelManager().updateTop(channelID,channelType, isTop);
```
**设置频道免打扰**
```java
LiMaoIM.getInstance().getLiMChannelManager().updateMute(channelID,channelType, isMute);
```
**修改频道扩展信息**
```java
LiMaoIM.getInstance().getLiMChannelManager().updateExtra(channelID,channelType, HashMap)
```
**频道信息改变监听**
```java
LiMaoIM.getInstance().getLiMChannelManager().addOnRefreshChannelInfo("listener_key", new IRefreshChannel() {
            @Override
            public void onRefreshChannel(LiMChannel liMChannel) {
                // 回掉是在主线程
            }
        });
```
**频道成员信息改变监听**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnRefreshChannelMemberInfo("listener_key",liMChannelMember -> {
    //todo
});
```
**移除频道成员监听**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnRemoveChannelMemberListener("listener_key",list -> {
    //这里可用于监听群成员被移除等
});
```
**添加频道成员监听**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnAddChannelMemberListener("listener_key",list -> {
    //这里可用于监听添加群成员等
});
```
每个监听对于都有取消监听方法，退出页面后可取消对于的监听。

