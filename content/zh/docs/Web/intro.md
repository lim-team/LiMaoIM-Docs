---
title: "概要"
linkTitle: "概要"
date: 2020-03-25
weight: 999
---

## 集成步骤

第一步：引入SDK，获取lim对象

第二步：初始化连接配置

第三步：连接/断开IM

第四步：收/发消息

参考 [Demo](https://github.com/lim-team/LiMaoIMWebDemo)

## lim对象

狸猫IM JS SDK主要围绕 lim对象做开发, lim对象主要包含如下部分:

#### 配置参数(lim.options)

狸猫IM初始化参数可以通过此属性设置

#### 登录信息(lim.loginInfo)

狸猫IM登录的参数可以通过此属性设置

#### 频道管理(lim.channelManager)

狸猫IM频道相关的数据可以通过此属性获取，例如：频道信息，同步频道成员等等

#### 常用方法

IM连接/断开

IM连接状态监听

收取消息监听

发送消息监听

发送消息回执监听
