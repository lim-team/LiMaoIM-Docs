---
title: "导入SDK"
linkTitle: "导入SDK"
date: 2017-01-05
weight: 99
---

## 引入通讯SDK模块
下载 limaoimlib-release.aar 资源包，将文件包放入到自己的app工程的libs文件下
配置app的Gradle文件，配置如下：

```
android{
        .......
}
 repositories{
        flatDir {
                dirs'libs'
        }
}

dependencies {
    implementation(name: 'limaoimlib-release', ext: 'aar')
}
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
LimKitApplication.getInstance().initContext(this);
```
