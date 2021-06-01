---
title: "历史记录"
linkTitle: "历史记录"
date: 2020-02-06
weight: 1050
---

查询指定频道的历史消息记录

```java
LiMaoIM.getInstance().getLiMMsgManager().getOrSyncHistoryMessages(channelId, channelType, oldestOrderSeq, contain, dropDown, pageSize, new IGetOrSyncHistoryMsgBack() {
            @Override
            public void onResult(List<LiMMsg> list) {
                
            }
        });
```

参数说明:


参数 | 类型 | 说明
---|--- |---
channelId | String | 频道ID
channelType | byte | 频道类型
oldestClientSeq | long | 上次查询到的最新数据的客户端编号，第一次查询则为0
contain | boolean | 是否包含最后一条消息clientseq
dropDown | boolean | true：下拉false：上拉
pageSize | int | 查询消息数量
