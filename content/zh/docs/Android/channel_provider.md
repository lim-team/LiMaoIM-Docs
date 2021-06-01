---
title: "频道资料对接"
linkTitle: "频道资料对接"
date: 2020-02-06
weight: 1060
---
LiMaoIm SDK中会判断本地是否有频道资料。如果sdk中没有频道资料会调用上层设置的```addGetChannelInfoListener```监听来获取指定的频道信息。
```java
   LiMaoIM.getInstance().getLiMChannelManager().addOnGetChannelInfoListener(new IGetChannelInfo() {
            @Override
            public LiMChannel onGetChannelInfo(String channelID, byte channelType, IChannelInfoListener iChannelInfoListener) {
                // 如果UI层有该用户或群信息就直接返回对于数据。如果没有需从网络请求后再回掉给sdk，这里就直接返回null
                 if (channelType == LiMChannelType.PERSONAL) {
                     // todo 获取个人信息
                    UserModel.getInstance().getUserInfo(channelId, (code, msg, userInfo) -> {
                    });
                } else {
                    // todo 获取群信息
                   
                }
                return null;
            }
        });
```