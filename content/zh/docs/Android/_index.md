---
title: "Android端集成与开发"
linkTitle: "Android端集成与开发"
weight: 2
---

### <font color='#2196F3'>sdk流程</font>

<img src='./sdk_technological_process.png' />
如上图所示。sdk和app直接关系及流程：app初始化sdk和添加事件监听，sdk在收到消息或发送消息都会先存库后在通知到app更新到UI。


### <font color='#2196F3'>重要的管理类</font>
* `LiMConnectionManager` 连接管理。sdk中所有的连接监听，退出，连接im均是该类处理。
* `LiMMsgManager` 消息管理。处理消息某个会话的历史记录，查询某条消息，搜索消息记录等。
* `LiMConversationManager` 会话管理。处理修改某个会话的未读数量，获取最近最近会话列表等。最近会话管理可获取到`LiMReminderManager` 提醒管理。提醒管理可对最近会话增加强提醒效果，如：[有人@你][草稿][群审核]等。
* `LiMChannelManager` 频道管理。对某个频道的置顶、免打扰、禁言、资料更新等均是该类处理。
* `LiMChannelMembersManager` 频道成员管理。频道成员管理是对应于频道管理，可查询某个频道的所有成员等。
* `LiMCMDManager` cmd命令管理。sdk内部通讯信息不会显示在UI上的消息管理。比如好友修改头像、对方离线在线状态、频道成员更改等，都是通过命令管理处理。

><font color='#999' size=2>注：所有的管理类都是通过`LiMaoIM.getInstance()`获取，不需要单独创建对应的类。如获取消息管理：`LiMaoIM.getInstance().getLiMMsgManager()`</font>

### <font color='#2196F3'>事件监听说明</font>
狸猫SDK中的事件分为两种：
* 需要传递`listener_key`的事件。该类事件支持多个监听，且都会收到监听回掉，并支持移除对应`listener_key`的监听
* 不需要`listener_key`的事件。不支持多个监听，多次监听会将最新的监听覆盖旧的监听。

><font color=#999 size=2>注：sdk所有的事件回掉都在主线程</font>

### <font color='#2196F3'>数据库说明</font>
sdk中的数据库基本上满足了绝大部分的im业务，因此我们不需要也不建议更改数据库设计。如果您有特殊业务需要升级数据时，我们建议您按以下步骤升级数据库
* 在`assets/lim_sql`文件中新建一个当期日期的后缀名为`sql`的文件
如下图
<img src='db_update.jpg' width=400 height=150/>

* 在新建文件中编写sql语句，sql语句中不能包含注释不然会运行报错
* 修改`LiMDBHelper`文件中的`version`字段加一

对此数据库升级就完成了