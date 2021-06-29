---
title: "频道成员信息"
linkTitle: "频道成员信息"
date: 2020-02-06
weight: 1055
---

频道成员是对应于频道信息

### <font color='#2196F3' size=4>常用方法</font>
**<font color='#2196F3' size=3>获取指定频道的成员列表</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().getLiMChannelMembers(channelID, channelType);
```
**<font color='#2196F3' size=3>获取频道成员数量</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().getMembersCount(channelID, channelType);
```
### <font color='#2196F3' size=4>事件</font>

**<font color='#2196F3' size=3>频道成员信息改变监听</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnRefreshChannelMemberInfo("listener_key",liMChannelMember -> {
    //todo
});
```
**<font color='#2196F3' size=3>移除频道成员监听</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnRemoveChannelMemberListener("listener_key",list -> {
   
});
```

**<font color='#2196F3' size=3>添加频道成员监听</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnAddChannelMemberListener("listener_key",list -> {
   
});
```

**<font color='#2196F3' size=3>刷新频道成员监听</font>**
```java
LiMaoIM.getInstance().getLiMChannelMembersManager().addOnRefreshChannelMemberInfo("listener_key",liMChannelMember -> {
   
});
```