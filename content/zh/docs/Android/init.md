---
title: "初始化"
linkTitle: "初始化"
date: 2020-02-06
weight: 1010
---
在application中onCreate方法中执行：
```java
LiMaoIm.getInstance().initIm(context, uid, token, isProcess);
```
context：应用上下文

uid：用户连接的唯一ID（由后端提供）

token：用户连接凭证（由后端提供）

isProcess：是否需要后台进程（service）建议传false

## 其他配置
```java
 LiMaoIm.getInstance().getLiMEventManager().addGetIpAndPortListener(andPortListener -> {
            //如果是后端是分布式需通过接口获取后台分配的IP和port
            andPortListener.onGetSocketIpAndPort(ip, port);
        });
```