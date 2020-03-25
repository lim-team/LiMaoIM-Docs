---
title: "连接/断开IM"
linkTitle: "连接/断开IM"
date: 2020-03-25
weight: 1020
---

## 连接IM

```Javascript
lim.connect(UID,TOKEN)
```


uid: 服务端返回给客户端的用户唯一ID

token: 服务端返回给客户端的唯一认证凭证

## 断开IM

```Javascript
lim.disconnect()
```

## 监听连接变化

```Javascript
lim.addConnectStatusListener(status => {
    if (status == 1) {
        console.log("连接成功！");
    } else {
        console.log("断开连接！");
    }
});
```