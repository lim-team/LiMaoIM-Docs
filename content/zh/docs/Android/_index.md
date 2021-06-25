---
title: "Android端集成与开发"
linkTitle: "Android端集成与开发"
weight: 2
---

### sdk流程

<img src='./sdk_technological_process.png' />
如上图所示。sdk和app直接关系及流程：app初始化sdk和添加事件监听，sdk在收到消息或发送消息都会先存库后在通知到app更新到UI。

### 事件监听说明
狸猫IM sdk大部分事件都是支持在不同页面不同模块监听同一个事件。比如你可以在朋友圈模块监听新消息，也可以在聊天会话模块监听。支持多个监听的事件需传递一个唯一key，对应取消监听也可以通过传递的key移除监听。但是特殊监听只能存在一个，比如获取channel信息，获取消息离线。
><font color=#999 size=2>注：sdk所有的事件回掉都在主线程</font>