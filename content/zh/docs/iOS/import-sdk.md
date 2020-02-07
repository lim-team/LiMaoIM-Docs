---
title: "导入SDK"
linkTitle: "导入SDK"
date: 2017-01-05
weight: 1000
---

## 引入基础SDK模块

通过 CocoaPods 管理依赖, CocoaPods 是目前最流行的 Cocoa 项目库依赖管理工具之一，考虑到便捷与项目的可维护性，我们推荐您使用 CocoaPods 导入并管理 SDK 

```
pod 'LiMaoIMSDK'
```

引入

```Objective-C
import <LiMaoIMSDK/LiMaoIMSDK.h>
```

## 引入UI相关模块

如果你需要用到聊天的UI或在我们提供的UI上进行二次开发，则需要引入 LIMBase项目,下载LiMaoBase path后替换为自己下载的路径

```
pod 'LiMaoBase',  :path => './Modules/LiMaoBase'  
```

引入

```Objective-C
import <LiMaoBase/LiMaoBase.h>
```