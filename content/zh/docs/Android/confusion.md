---
title: "混淆打包"
linkTitle: "混淆打包"
weight: 1000
---

默认混淆
```java
-keep class org.whispersystems.curve25519.**{*;}
```

如果UI使用sdk中部分实体需添加以下混淆
```java
-keep class com.xinbida.limaoim.entity.* { *; }
```