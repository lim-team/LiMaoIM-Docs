---
title: "连接与断开"
linkTitle: "连接与断开"
date: 2020-02-06
weight: 1020
---

**连接**
```java
LiMaoIM.getInstance().getLiMConnectionManager().connection();
```
**断开连接**
```java
// 断开连接 isLogout：true[sdk不再重连]，false[sdk会保持重连]
LiMaoIM.getInstance().getLiMConnectionManager().disconnect(false);
```
连接状态监听
```java
LiMaoIM.getInstance().getLiMConnectionManager().addOnConnectionStatusListener(new IConnectionStatus() {
            @Override
            public void onStatus(int status) {
                // 0 失败
                // 1 成功
                // 2 被踢（其他设备登录）
                // 3 同步消息中
                // 4 连接中
                // 5 无网络
            }
        });
```