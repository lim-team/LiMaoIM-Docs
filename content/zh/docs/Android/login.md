---
title: "连接与断开"
linkTitle: "连接与断开"
date: 2020-02-06
weight: 1020
---
```java
//开始连接
LiMaoIm.getInstance().getLiMConnectionManager().startConn(context);

//断开连接 isLogout：true[sdk不再重连]，false[sdk会保持重连]
LiMaoIm.getInstance().getLiMConnectionManager().disconnect(isLogout);
```
连接状态监听
```java
LiMaoIm.getInstance().getLiMEventManager().addConnectionStatusListener(code -> {
        if (code == LiMConnectStatus.kicked) {
            //被踢,在其他设备登录
        }else if(code == LiMConnectStatus.success){
            //连接成功
        }
 });
```