---
title: "搜索消息"
linkTitle: "搜索消息"
date: 2020-02-06
weight: 1050
---

当聊天消息很多时，如果想查看某天的聊天信息，滑动查看消息记录就特别麻烦。这时我们需要通过搜索来查找我们需要的消息。狸猫IM提供了丰富的查询方法。

我们在做聊天时，需要搜索本地包含某个字符的所有聊天记录，如下图效果

<img src='../search_all_msg.jpg' width=200 height=300>

对此狸猫IM提供了一个全局搜索的方法，可搜索本地所有包含某个关键词的方法

**<font color='#2196F3' size=3>全局搜索</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().search(searchKey);
```
返回结果`List<LiMMessageSearchResult>`中`LiMMessageSearchResult`的参数说明

| 参数           | 类型       | 说明               |
| -------------- | ---------- | ------------------ |
| liMChannel     | LiMChannel | 消息对应的频道信息 |
| searchableWord | string     | 包含关键字的信息   |
| messageCount   | int        | 消息条数           |


**<font color='#2196F3' size=3>查询某个频道的消息</font>**
```java
LiMaoIM.getInstance().getLiMMsgManager().searchWithChannel(channelID,channelType,searchKey);
```

参数说明:

| 参数        | 类型   | 说明     |
| ----------- | ------ | -------- |
| channelID   | string | 频道ID   |
| channelType | byte   | 频道类型 |
| searchKey   | string | 关键字   |

><font color='#999' size=2>注：自定义消息如果需要被查询到。需重写自定义消息的`getSearchableWord()`方法，并返回需要搜索的提示文字。</font>

我们在做消息搜索时，如果需要通过日期查询某个会话的聊天记录。这时需要查询到该会话的所有产生聊天记录的日期，如以下效果：

<img src='../chat_history_date.jpg' width="200" height="400" alt="聊天记录日期"/>

这时需调用以下方法获取到对应的消息日期

**<font color='#2196F3' size=3>查询频道聊天日期</font>**

```java
LiMaoIM.getInstance().getLiMMsgManager().getMessageGroupByDateWithChannel(channelID, channelType);
```

当消息类型很多时，这时就需要通过消息类型来搜索聊天记录。对此狸猫sdk提供来以下方法

**<font color='#2196F3' size=3>搜索某些类型消息</font>**
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
