---
title: "@消息"
linkTitle: "@消息"
weight: 2030 
---

```java
LiMTextContent textMsgModel = new LiMTextContent("我是@消息");
//@指定用户
List<LiMUserInfo> list = new ArrayList<>();
list.add(new LiMUserInfo("uid","张三"));
textMsgModel.mentionInfo = list;

//@所有人
textMsgModel.mention_all = 1;
```