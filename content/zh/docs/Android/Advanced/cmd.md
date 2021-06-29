---
title: "命令消息"
linkTitle: "命令消息"
weight: 2020 
---

我们都知道有些消息不需要呈现在UI，只需在应用内部消化（如：头像修改，对于好友需及时修改但用不需显示在UI上的消息）。狸猫IM对此设计了cmd消息。

**<font color='#2196F3' size=3>监听cmd消息</font>**
```java
LiMaoIM.getInstance().getLiMCMDManager().addCmdListener("listener_key", new ICMDListener() {
            @Override
            public void onMsg(LiMCMD liMCMD) {
            }
        });
```
`LiMCMD` 说明
* cmdKey 命令类型。可通过该字段判断做不同业务操作
* paramJsonObject 命令参数。不同命令对应的参数数据不同
* 
**<font color='#2196F3' size=3>移除监听</font>**
```java
LiMaoIM.getInstance().getLiMCMDManager().removeCmdListener("listener_key");
```
><font size=2 color='#999'>注：app不能发送cmd类消息，cmd消息只能是服务器代发。
sdk中内置了常用的`liMCMD.cmdKey`可查看`com.xinbida.limaoim.entity.LiMCMDKeys`文件</font>