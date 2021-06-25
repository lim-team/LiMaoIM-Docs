---
title: "自定义消息"
linkTitle: "自定义消息"
weight: 2010 
---

**普通消息**
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

// 如果需要被搜索到需重写该方法
@Override
public String getSearchableWord() {
    return "位置";
}
```

3、注册消息
```java
LiMaoIM.getInstance().getLiMMsgManager().registerContentMsg(LiMCardContent.class);
```

>注：自定义消息必须提供无参构造方法。如果定义的消息对象需要进行intent页面传递参数需实现Parcelable的方法。如果需要在搜索聊天记录时，能搜索到该类型的消息，则需重写`getSearchableWord()`方法并返回搜索关键字。

**附件消息**
我们都知道，有些消息不只是纯文本消息。可能需要发送图片，语音，文件等。这时就需要带附件消息，对此狸猫IM提供了`LiMMediaMessageContent`来解决消息附件问题。并且狸猫IM sdk也内置了图片、文件、语音、视频等常用的消息model。这里自定义一个地理位置消息举例
```java
public class LiMLocationContent extends LiMMediaMessageContent {
    public LiMLocationContent(double longitude, double latitude, String title, String address) {
        type = LiMMsgContentType.LIMAO_LOCATION;
        this.longitude = longitude;
        this.latitude = latitude;
        this.address = address;
        this.title = title;
    }

    public LiMLocationContent() {
        type = LiMMsgContentType.LIMAO_LOCATION;
    }

    public double longitude;
    public double latitude;
    public String address;
    public String title;


    @Override
    public JSONObject encodeMsg() {
        JSONObject jsonObject = new JSONObject();
        try {
            jsonObject.put("title", title);
            jsonObject.put("address", address);
            jsonObject.put("lat", latitude);
            jsonObject.put("lng", longitude);
            jsonObject.put("img", url);
            jsonObject.put("localPath", localPath);
        } catch (JSONException e) {
            e.printStackTrace();
        }
        return jsonObject;
    }

    @Override
    public LiMMessageContent decodeMsg(JSONObject jsonObject) {
        if (jsonObject.has("lat"))
            latitude = jsonObject.optDouble("lat");
        if (jsonObject.has("lng"))
            longitude = jsonObject.optDouble("lng");
        if (jsonObject.has("address"))
            address = jsonObject.optString("address");
        if (jsonObject.has("title"))
            title = jsonObject.optString("title");
        if (jsonObject.has("img"))
            url = jsonObject.optString("img");
        if (jsonObject.has("localPath"))
            localPath = jsonObject.optString("localPath");
        return this;
    }


    protected LiMLocationContent(Parcel in) {
        super(in);
        latitude = in.readDouble();
        longitude = in.readDouble();
        address = in.readString();
        title = in.readString();
        url = in.readString();
        localPath = in.readString();
    }

    @Override
    public void writeToParcel(Parcel dest, int flags) {
        super.writeToParcel(dest, flags);
        dest.writeDouble(latitude);
        dest.writeDouble(longitude);
        dest.writeString(address);
        dest.writeString(title);
        dest.writeString(url);
        dest.writeString(localPath);
    }


    public static final Creator<LiMLocationContent> CREATOR = new Creator<LiMLocationContent>() {
        @Override
        public LiMLocationContent createFromParcel(Parcel in) {
            return new LiMLocationContent(in);
        }

        @Override
        public LiMLocationContent[] newArray(int size) {
            return new LiMLocationContent[size];
        }
    };

    @Override
    public int describeContents() {
        return 0;
    }

    @Override
    public String getDisplayContent() {
        return "[位置]";
    }

}

```
><font color='#999' size=2>注：发送附件消息sdk判断该消息是否已上传附件，如果未上传附件sdk会回掉到UI，UI需上传完附件后将附件的信息返回给sdk。并添加附件上传监听
</font>

**消息附件监听**
```java
LiMaoIM.getInstance().getLiMMsgManager().addOnUploadAttachListener(new IUploadAttachmentListener() {
    @Override
    public void onUploadAttachmentListener(LiMMsg liMMsg, IUploadAttacResultListener iUploadAttacResultListener) {
        // ... 上传附件
        iUploadAttacResultListener.onUploadResult(true, liMMediaMessageContent);
    }
    });
```
至此自定义消息已完成。