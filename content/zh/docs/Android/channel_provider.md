---
title: "频道资料对接"
linkTitle: "频道资料对接"
date: 2020-02-06
weight: 1060
---
LiMaoIm SDK中会判断本地是否有频道资料。如果sdk中没有频道资料会调用上层设置的```addGetChannelInfoListener```监听来获取指定的频道信息。
```java
/*
    * 设置获取频道信息的监听
    */
    LiMaoIm.getInstance().getLiMEventManager().addGetChannelInfoListener((channelId, channelType, iChannelInfoListenter) -> {
    if (channelType == LiMChannelType.PERSONAL) {
        //获取个人信息
       .....
    } else {
        //如果上层没有该频道信息则通过接口获取
        GroupModel.getInstance().getGroupInfo(channelId, (code, msg, groupEntity) -> {
            if (code == HttpResponseCode.success && groupEntity != null) {
                LiMChannel liMChannel = new LiMChannel();
                liMChannel.channel_name = groupEntity.name;//频道名称
                liMChannel.channel_id = groupEntity.group_no;//频道ID
                liMChannel.channel_type = LiMChannelType.GROUP;//频道类型
                liMChannel.mute = groupEntity.mute;//是否免打扰
                liMChannel.top = groupEntity.top;//是否置顶
                liMChannel.save = groupEntity.save;//是否保存在通讯录
                liMChannel.show_nick = groupEntity.show_nick;//是否显示频道成员名称
                //sdk没有的字段可存在扩展字段中
                HashMap<String, Object> hashMap = new HashMap<>();
                hashMap.put("notice", groupEntity.notice);
                liMChannel.extraMap = hashMap;
                iChannelInfoListenter.onResult(liMChannel);
            }
        });
    }
    //如果上层有该频道资料则直接返回频道信息
    return null;
    });
```