---
title: "显示提醒"
linkTitle: "显示提醒"
date: 2020-02-06
weight: 1044
---


在即时通讯软件中有诸多需要显示提醒的内容，如果下图，在狸猫IM中，我们统一抽象为 “提醒”功能。
<img src='./reminder.png' width="400" height="200" />

**最近会话提醒对象结构**
```java
public class LiMMention {
   //提醒类型
    public int type;
    //提醒文本 如：[有人@我]
    public String text;
    //提醒包含的数据 大部分提醒无需数据 所以该字段非必填
    public Object data;
}
```
><font color='#999' size=2>注：狸猫IM SDK 目前已经定义了 `LiMMentionType.liMReminderTypeMentionMe`（[有人@我]），`LiMMentionType.liMReminderTypeDraft` （[草稿]） 两个类型。 用户可以根据自己的需求自定义类型，相同的类型在最近会话中只会保存最新的提醒</font>

**获取频道里指定类型的提醒**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().getReminder(channelId, channelType, limReminderType);
```

参数说明:

| 参数            | 类型   | 说明     |
| --------------- | ------ | -------- |
| channelID       | string | 频道ID   |
| channelType     | byte   | 频道类型 |
| limReminderType | int    | 提醒类型 |

**追加某个频道的提醒内容**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().appendReminder(channelId, channelType, liMReminder);
```

参数说明:

| 参数        | 类型        | 说明     |
| ----------- | ----------- | -------- |
| channelID   | string      | 频道ID   |
| channelType | byte        | 频道类型 |
| liMReminder | LiMReminder | 提醒项   |


**清除某个频道所有提醒项**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().clearAllReminder(channelId, channelType);
```