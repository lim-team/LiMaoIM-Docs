---
title: "LiMaoBase(UI库)使用"
linkTitle: "LiMaoBase(UI库)使用"
date: 2020-02-06
weight: 3000 
---

LiMaoBase集成了IM常用的UI和一些功能。具体使用细节请参考:LiMaoIMDemo

三步使用LiMaoBase

第一步: 引入LiMaoBase

```
 pod 'LiMaoBase',  :path => 'LiMaoBase的所在路径' 

```

第二步: 初始化LIMApp配置

```Objective-C
 // app配置
LIMAppConfig *config = [LIMAppConfig new];
config.connectURL = @""; // IM连接地址 例如: lim://49.235.59.182:6666
config.apiBaseUrl = @""; // api地址 例如: http://49.235.59.182:8080/v1/
config.fileBaseUrl = @""; // 文件上传地址 例如：http://49.235.59.182:8888/
config.fileBrowseUrl = @""; // 文件预览地址 例如: http://49.235.59.182:8082/
[LIMApp shared].config = config;

// app首页设置
[LIMApp shared].getHomeViewController = ^UIViewController * _Nonnull{
    LIMMainTabController *homeViewController =  [LIMMainTabController new];
    homeViewController.viewControllers = [self tabViewControllers];
    return homeViewController;
};

// app初始化
[[LIMApp shared] appInit];
  
```

第三步: 赋值loginInfo（登录信息）

```Objective-C
[LIMApp shared].loginInfo.token = @""; // 用户token
[LIMApp shared].loginInfo.uid = @""; // 用户的UID
[LIMApp shared].loginInfo.extra[@"name"] = @""; // 用户昵称
[LIMApp shared].loginInfo.extra[@"avatar"] = @""; // 用户头像
[[LIMApp shared].loginInfo save]; // 保存登录信息
```