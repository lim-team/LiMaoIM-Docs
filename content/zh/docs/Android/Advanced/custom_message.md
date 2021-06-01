---
title: "自定义消息"
linkTitle: "自定义消息"
weight: 2010 
---

为了满足更多的应用场景，狸猫IM提供自定义消息。自定义消息分为三个步骤，这里自定义一个名片消息举例

1、继承 LiMMessageContent 和定义字段
```java
public class LiMCardContent extends LiMMessageContent {
    //注意无参构造方法必须写
    public LiMCardContent() {
        //指定消息类型
        type = ContentType.card;
    }
    //用户ID
    public String uid;
    //用户名称
    public String name;
    //用户头像
    public String avatar;
}
```

2、解码和编码
```java
 @Override
public JSONObject encodeMsg() {
    JSONObject jsonObject = new JSONObject();
    try {
        jsonObject.put("uid", uid);
        jsonObject.put("name", name);
        jsonObject.put("avatar", avatar);
    } catch (JSONException e) {
        e.printStackTrace();
    }
    return jsonObject;
}

@Override
public LiMMessageContent decodeMsg(JSONObject jsonObject) {
    uid = jsonObject.optString("uid");
    name = jsonObject.optString("name");
    avatar = jsonObject.optString("avatar");
    return this;
}

```

3、注册消息
```java
LiMaoIM.getInstance().getLiMMsgManager().registerContentMsg(LiMCardContent.class);
```

注意：如果定义的消息对象需要进行intent页面传递参数需实现Parcelable的方法

至此自定义消息已完成。详见demo中 com.limao.im.limkit.chat.msgmodel.LiMCardContent 的具体实现