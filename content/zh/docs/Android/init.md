---
title: "初始化"
linkTitle: "初始化"
date: 2020-02-06
weight: 1010
---
在application中onCreate方法中执行：
```java
LiMaoIM.getInstance().initIM(context, uid, token);
```

参数说明

| 参数    | 类型    | 说明                           |
| ------- | ------- | ------------------------------ |
| context | Context | 应用上下文                     |
| uid     | String  | 用户连接的唯一ID（由后端提供） |
| token   | String  | 用户连接凭证（由后端提供）     |

如果聊天服务器是支持分布式部署时，这时app需通过接口获取聊天的port和IP。如果是单机的话就直接返回固定的IP和端口。并监听以下方法
### <font color='#2196F3'>获取聊天IP和port</font>
```java
   LiMaoIM.getInstance().getLiMConnectionManager().addOnGetIpAndPortListener(new IGetIpAndPort() {
            @Override
            public void getIP(IGetSocketIpAndPortListener iGetSocketIpAndPortListener) {
                
            }
        });
```
><font color='#999' size=2>注：分布式需请求接口后返回IP和port</font>