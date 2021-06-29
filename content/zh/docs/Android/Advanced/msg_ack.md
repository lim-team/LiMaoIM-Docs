---
title: "消息回执"
linkTitle: "消息回执"
weight: 2050 
---
消息回执是指在发送消息到个人或群后，对方或群是否已读或已读数量的显示。消息回执在企业通讯软件中特别重要，狸猫IM也设计自己的消息回执功能。实现效果如下

<img src='../msg_unread.jpg' width=220 height=150/>
<img src='../msg_part_read.jpg' width=220 height=150/>
<img src='../msg_all_read.jpg' width=220 height=150/>

如上图显示的效果，消息回执分为三个阶段。未读、部分已读、全部已读。下面说明下狸猫demo的实现步骤

* 开启消息回执开关
* 点开某个会话时，或在停止滑动消息列表时将当前可见消息ID(`message_id`)提交后端接口通知服务器对应消息已读，并调用`LiMMsgManager`中的`updateMsgReadWithMsgIds()`方法更改本地字段（`LiMMsg`中的`readed`）标记消息已读避免重复提交
* 收到狸猫sdk中命令消息(cmd)中同步扩张消息的类型（`LiMCMDKeys.lim_sync_message_extra`）后同步扩张消息，更改本地扩张消息完成对消息的已读数量，未读数量的更改
* 收到狸猫sdk刷新消息监听返回，刷新UI已读未读效果
对此消息回执功能已完成
><font color='#999' size=2>以上实现步骤是狸猫demo实现方式，仅提供参考。具体实现需根据自己业务配合后端完成该功能。</font>