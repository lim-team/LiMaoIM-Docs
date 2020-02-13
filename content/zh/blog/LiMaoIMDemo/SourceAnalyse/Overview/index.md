
---
date: 2020-02-12
title: "概要说明"
linkTitle: "概要说明"
author: tangtao 
weight: 900
resources:
- src: "**.{png,jpg}"
  title: "Image #:counter"
---

 
## 设计理念 
LiMaoIMDemo是基于[LiMaoIMSDK](/docs)和LiMaoBase设计

LiMaoIMDemo的设计全围绕一个中心思想 “一个模块一个功能，一句配置安装模块”，比如开发了一个“红包模块”，如果LiMaoIMDemo需要引入红包功能，理论上LiMaoIMDemo开发者只需要引入一句配置 `pod 'LiMaoRedpacket'`后，聊天面板里就可以发红包了和也支持红包的消息了，红包的相关功能都可以正常使用，后面将会详细说为了达到这个目的我们做了那些开发。


## 架构

{{< imgproc structure1 Resize "800x640" >}}
 LiMaoDemo由许多模块组合而成
{{< /imgproc >}}

## 模块引入配置

{{< imgproc podfile Resize "1316x440" >}}
{{< /imgproc >}}
