---
title: "搜索消息"
linkTitle: "搜索消息"
date: 2020-02-06
weight: 1050
---

当聊天消息很多时，滑动查看消息记录就特别麻烦，这时我们需要通过搜索来查找我们需要的消息。狸猫IM提供了丰富的查询丰富。

**全局搜索**
```java
LiMaoIM.getInstance().getLiMMsgManager().search(searchKey);
```
返回结果`List<LiMMessageSearchResult>`中`LiMMessageSearchResult`的参数说明

| 参数           | 类型       | 说明               |
| -------------- | ---------- | ------------------ |
| liMChannel     | LiMChannel | 消息对应的频道信息 |
| searchableWord | string     | 包含关键字的信息   |
| messageCount   | int        | 消息条数           |


**查询某个频道的消息**
```java
LiMaoIM.getInstance().getLiMMsgManager().searchWithChannel(channelID,channelType,searchKey);
```

参数说明:

| 参数        | 类型   | 说明     |
| ----------- | ------ | -------- |
| channelID   | string | 频道ID   |
| channelType | byte   | 频道类型 |
| searchKey   | string | 关键字   |

>注：自定义消息如果需要被查询到。需重写自定义消息的`getSearchableWord()`方法，并返回需要搜索的提示文字。

**查询频道聊天日期**
通过该方法能够获取对应频道所有的本地产生聊天记录的日期信息
```java
LiMaoIM.getInstance().getLiMMsgManager().getMessageGroupByDateWithChannel(channelID, channelType);
```

**搜索某些类型消息**
```java
LiMaoIM.getInstance().getLiMMsgManager().searchMsgWithChannelAndContentTypes(channelID, channelType, oldestOrderSeq, 20, types);
```

参数说明:

| 参数           | 类型   | 说明                                |
| -------------- | ------ | ----------------------------------- |
| channelID      | string | 频道ID                              |
| channelType    | byte   | 频道类型                            |
| oldestOrderSeq | long   | 上次查询最大orderSeq，第一次查询为0 |
| limit          | int    | 每次获取数量                        |
| contentTypes   | int[]  | 消息内容类型                        |
