
## 安装hugo服务

mac安装

```
brew install hugo
```

## 开启hugo服务

进入项目根目录，执行:

```
hugo server
```

## 编写文档

1. 进入content/docs目录

```
文件的目录结构就是左边的菜单结构
文件夹下的_index.md就是文件目录，同级的md就是子菜单
```

创建自己的md文件，头部增加如下样式

```
---
title: "历史记录"
linkTitle: "历史记录"
date: 2020-02-06
weight: 1050
---
```

title: 文章标题
linkTitle: "链接标题"
weight: 权重，数字越小越靠前
