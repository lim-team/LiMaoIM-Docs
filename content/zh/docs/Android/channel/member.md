---
title: "频道成员信息"
linkTitle: "频道成员信息"
date: 2020-02-06
weight: 1060
---

**获取指定频道的成员列表**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().getLiMChannelMembers(channelID, channelType);
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
