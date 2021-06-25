---
title: "连接与断开"
linkTitle: "连接与断开"
date: 2020-02-06
weight: 1020
---

**<font color='#2196F3'>连接</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().connection();
```
**<font color='#2196F3'>断开连接</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().disconnect(false);
```
><font color='#999' size=2>注：isLogout：true[sdk不再重连]，false[sdk会保持重连]</font>

**<font color='#2196F3'>连接状态监听</font>**
```java
LiMaoIM.getInstance().getLiMConnectionManager().addOnConnectionStatusListener(new IConnectionStatus() {
            @Override
            public void onStatus(int status) {
               
            }
        });
```
status返回状态说明：
* 0 失败
* 1 成功
* 2 被踢（其他设备登录）需清除token退出到登录页面
* 3 同步消息中
* 4 连接中
* 5 无网络