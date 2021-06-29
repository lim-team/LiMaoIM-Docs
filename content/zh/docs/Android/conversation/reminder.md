---
title: "显示提醒"
linkTitle: "显示提醒"
date: 2020-02-06
weight: 1044
---


在即时通讯软件中有诸多需要显示提醒的内容，如果下图，在狸猫IM中，我们统一抽象为 “提醒”功能。

<img src='../reminder.png' width="400" height="200" />

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
><font color='#999' size=2>注：狸猫IM SDK 目前已经定义了 `LiMMentionType.liMReminderTypeMentionMe`（[有人@我]），`LiMMentionType.liMReminderTypeDraft` （[草稿]） 两个类型。 用户可以根据自己的需求自定义类型，相同的类型在最近会话中只会保存最新的提醒。值得注意的是提醒管理属于最近会话管理范畴，他的获取方式是`LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager()`</font>

如果我们要查询某个会话的固定的某个提醒，比如获取一个会话的[草稿]信息就需使用以下方法

**<font color='#2196F3' size=3>获取频道里指定类型的提醒</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().getReminder(channelId, channelType, limReminderType);
```

参数说明:

| 参数            | 类型   | 说明     |
| --------------- | ------ | -------- |
| channelID       | string | 频道ID   |
| channelType     | byte   | 频道类型 |
| limReminderType | int    | 提醒类型 |

如果在聊天中输入的信息并没有点击发送，这时我们需将编辑的内容存入草稿，并更新显示到最近会话对应的会话项，这时需追加会话的提醒内容

**<font color='#2196F3' size=3>追加某个频道的提醒内容</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().appendReminder(channelId, channelType, liMReminder);
```

参数说明:

| 参数        | 类型        | 说明     |
| ----------- | ----------- | -------- |
| channelID   | string      | 频道ID   |
| channelType | byte        | 频道类型 |
| liMReminder | LiMReminder | 提醒项   |

当点击某个会话进入到聊天中时，需将对应会话的提醒删除。

**<font color='#2196F3' size=3>清除某个频道所有提醒项</font>**
```java
LiMaoIM.getInstance().getLiMConversationManager().getLiMReminderManager().clearAllReminder(channelId, channelType);
```