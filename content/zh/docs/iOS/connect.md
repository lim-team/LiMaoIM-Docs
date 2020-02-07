---
title: "连接与断开"
linkTitle: "连接与断开"
date: 2020-02-06
weight: 1020
---



```Objective-C
// 开始连接 
 [[LIMSDK shared].connectionManager connect];

 // 断开连接 NO: SDK保持重连机制  YES: SDK将不再进行重连
 [[LIMSDK shared].connectionManager disconnect:NO];
```

需要监听连接状态的页面实现委托 LIMConnectionManagerDelegate

```Objective-C
// 添加委托
[[LIMSDK shared].connectionManager addDelegate:self];
```



```Objective-C
/**
 连接状态监听
 */
-(void) onConnectStatus:(LIMConnectStatus)status;


/**
  连接被踢出

 @param reasonCode 踢出原因代号 可有第三方服务器提供代号
 @param reason 踢出原因字符串 可由第三方服务器提供踢出原因 实现类似微信的效果 比如：账号设备xxx上登录，登录地点为xxx
 */
-(void) onKick:(uint8_t)reasonCode reason:(NSString*)reason;

```