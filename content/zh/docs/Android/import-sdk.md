---
title: "导入SDK"
linkTitle: "导入SDK"
date: 2017-01-05
weight: 99
---

## 引入通讯SDK模块
在主程序的build.gradle文件中添加：

```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
然后在app model中导入
```
implementation 'com.github.lim-team:LiMaoIMAndroidSDK:1.0.0'
```

## 引入UI相关模块
下载limkit model，将文件夹放入到自己的app模块同级目录
配置项目settinigs.gradle文件，如下：
```
include ':app', ':limkit'
```
配置app（主）model，如下：
```
implementation project(':limkit')
```
在application中初始化limkit
```
LimKitApplication.getInstance().initLiMKitModule(this);
```
