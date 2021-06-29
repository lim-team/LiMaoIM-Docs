---
title: "消息回复"
linkTitle: "消息回复"
weight: 2060 
---

消息回复是指对已经产生过的消息做出回复功能。消息回复会产生一条新的消息。如以下效果

<img src='../msg_reply.jpg' width=300 height=200/>

狸猫sdk中已经内置了消息回复字段，开发者只需提供该字段数据即可实现本功能。具体实现如下

* 发送需要回复的消息时，将消息model（`LiMMessageContent`）中的`reply`字段赋值
* 收到消息时判断消息model中`reply`是否包含数据，如果不为`null`则本条消息包含被回复的消息

对此消息回复就完成了

`LiMReply`字段说明
* `root_mid` 被回复的消息的根消息ID。如果是多级回复则该字段为第一次被回复的消息ID
* `message_id` 当前被回复的消息ID
* `message_seq` 消息服务器序列号
* `from_uid` 被回复消息发送者ID
* `from_name` 被回复消息发送者名称
* `payload` LiMMessageContent 类型。回复的消息内容，直接传递被回复消息对象`LiMMsg`中的`baseContentMsgModel`字段

><font color='#999' size=2>注：被回复消息必须是发送成功的或者是收到的消息，即存在`message_id`,`message_seq`的消息。</font>