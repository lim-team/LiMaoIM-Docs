---
title: "初始化"
linkTitle: "初始化"
date: 2020-02-06
weight: 1010
---

## 简单配置 （推荐）

一句代码初始化IM服务器

```Objective-C
[LIMSDK shared].connectURL = @"lim://IP:PORT?uid=xxx&token=xxx"; // 例如：@"lim://49.235.59.182:6666?uid=xxx&token=xxx";
```
IP: IM服务器的IP地址

PORT: IM服务器的端口

uid: 用户连接的唯一ID （由服务器提供）

token: 用户连接凭证 （由服务器提供）


------

## 所有配置

```Objective-C
[LIMSDK shared].options.isDebug = true; // 是否开启debug模式
[LIMSDK shared].options.host = @"49.235.59.182"; // IM服务器的IP
[LIMSDK shared].options.port = 6666; // IM服务器的端口
[LIMSDK shared].options.heartbeatInterval = 60; // 心跳间隔 （ 单位秒）
[LIMSDK shared].options.dbDir =  [[NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) lastObject] stringByAppendingPathComponent:@"db"]; //  数据库的存储目录
[LIMSDK shared].options.messageFileRootDir = [[NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) lastObject] stringByAppendingPathComponent:@"files"]; // 消息文件根目录
[LIMSDK shared].options.messageRetryInterval = 5; //  消息重试间隔 (单位秒)
[LIMSDK shared].options.messageRetryCount = 8; //  消息重试次数
[LIMSDK shared].options.offlineMessageLimit = 300; //  离线消息每次拉取数量
[LIMSDK shared].options.connectInfo = nil; // 连接信息
```

```Objective-C
 // 设置IM连接信息回调（当IM需要取连接信息时会调用此方法，如果设置了connectInfo则不会回调）
[LIMSDK shared].options.connectInfoCallback = ^LIMConnectInfo * _Nonnull{
    LIMConnectInfo *connectInfo = [LIMConnectInfo new];
    connectInfo.uid = "xxxx";
    connectInfo.token = "xxxx";
    return  connectInfo;
};
```
