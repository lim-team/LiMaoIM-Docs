---
title: "频道信息"
linkTitle: "频道信息"
date: 2020-02-06
weight: 1050
---

### 概念
什么叫‘频道’。我们常见的个人、群、公众号等只是对于的聊天ID和聊天类型不同，但他们都是在同一个消息通道中收发消息。因此狸猫IM将这些个人、群或公众号统一称之为：‘频道（Channel）’。

**sdk内置频道类型**
* 1：个人（`LiMChannelType.PERSONAL`）
* 2：群（`LiMChannelType.GROUP`）

**查询某个channel**
```java
LiMaoIM.getInstance().getLiMChannelManager().getLiMChannel(channelId, channelType);
```
**刷新频道缓存信息**
```java
LiMaoIM.getInstance().getLiMChannelManager().refreshChannelCache(liMChannel);
```

**添加或修改频道**
```java
//单个操作
LiMaoIM.getInstance().getLiMChannelManager().addOrUpdateChannel(liMChannel);
//批量操作
```java
LiMaoIM.getInstance().getLiMChannelManager().addOrUpdateChannels(list);
```
>注：用户也可以在初始化sdk完成后，批量导入频道信息。如登录用户的好友等`channel`的`follow`字段可以指定频道关系。

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

### 事件

**获取频道信息**
LiMaoIm SDK中会判断本地是否有频道资料。如果sdk中没有频道资料会调用上层设置的`addGetChannelInfoListener`监听来获取指定的频道信息。
```java
LiMaoIM.getInstance().getLiMChannelManager().addOnGetChannelInfoListener(new IGetChannelInfo() {
            @Override
            public LiMChannel onGetChannelInfo(String channelID, byte channelType, IChannelInfoListener iChannelInfoListener) {
                if (channelType == LiMChannelType.PERSONAL) {
                     // todo 获取个人信息
                } else {
                    // todo 获取群信息
                }
                return null;
            }
        });
```
>注：如果UI层有该用户或群信息就直接返回对于数据。如果没有需从网络请求后再回掉给sdk这里就直接返回null。或从网络获取信息后调用调用`refreshChannelCache`方法刷新频道信息。

**频道信息改变监听**
```java
LiMaoIM.getInstance().getLiMChannelManager().addOnRefreshChannelInfo("listener_key", new IRefreshChannel() {
            @Override
            public void onRefreshChannel(LiMChannel liMChannel) {
                // todo
            }
        });
```

>注：sdk回掉都是在主线程。常用的监听对应都有取消监听方法，退出页面后可取消对应的监听。

