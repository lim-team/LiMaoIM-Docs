---
title: "@消息"
linkTitle: "@消息"
weight: 2030 
---
### 消息提醒

狸猫IM所有消息都支持@指定用户或@所有人功能。以下以文本消息举例：

```java
LiMTextContent textMsgModel = new LiMTextContent("我是@消息");
//@指定用户
List<LiMUserInfo> list = new ArrayList<>();
list.add(new LiMUserInfo("uid","张三"));
textMsgModel.mentionInfo = list;

//@所有人
textMsgModel.mention_all = 1;
```