---
title: "连接与断开"
linkTitle: "连接与断开"
date: 2020-02-06
weight: 1020
---
在注册完狸猫sdk后就可以对IM进行连接、断开操作了。

**<font color='#2196F3'>连接</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().connection();
```
**<font color='#2196F3'>断开连接</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().disconnect(false);
```
><font color='#999' size=2>注：isLogout：true[sdk不再重连]，false[sdk会保持重连]。</font>
### <font color='#2196F3'>事件</font>
**<font color='#2196F3'>连接状态监听</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().addOnConnectionStatusListener(new IConnectionStatus() {
            @Override
            public void onStatus(int status) {
               
            }
        });
```
><font color='#999' size=2>注：连接返回状态请查看[状态码](/content/zh/docs/Android/status.md)</font>