---
title: "消息监听"
linkTitle: "消息监听"
date: 2020-02-06
weight: 1030
---

#### 收到消息监听
```java
LiMaoIm.getInstance().getMessageManager().addNewMsgListener(liMMsgList -> {
    //liMMsgList 为收到的消息集合
    //... todo
}
```
#### 发送消息返回监听
```java
LiMaoIm.getInstance().getMessageManager().addSendMsgCallback(new ISendMsgCallBackListener() {
    @Override
    public void onInsertMsg(LiMMsg liMMsg) {
        //判断是否为当前会话再显示到UI
        if (liMMsg.channel_type == channelType && liMMsg.channel_id.equals(channelId)) {
            //...
        }
    }
});
```

#### 消息刷新监听
```java
LiMaoIm.getInstance().getMessageManager().addRefreshMsgListener(liMMsg -> {
            List<UIChatMsgItemEntity> list = chatAdapter.getData();
            for (int i = 0, size = list.size(); i < size; i++) {
                if (list.get(i).liMMsg != null && list.get(i).liMMsg.client_seq == liMMsg.client_seq) {
                    //消息状态
                    list.get(i).liMMsg.status = liMMsg.status;
                    //语音是否已读（pc同步状态）
                    list.get(i).liMMsg.voice_readed = liMMsg.voice_readed;
                    //发送消息返回的服务器message_id
                    list.get(i).liMMsg.message_id = liMMsg.message_id;
                    //消息扩展字段
                    list.get(i).liMMsg.extraMap = liMMsg.extraMap;
                    //消息model
                    list.get(i).liMMsg.baseContentMsgModel = liMMsg.baseContentMsgModel;
                    chatAdapter.notifyItemChanged(i);
                    break;
                }
            }
        });
```
#### 消息附件监听
```java
LiMaoIm.getInstance().getMessageManager().addUploadAttachListener(new IUploadAttachmentListener() {
    @Override
    public void onUploadAttachmentListener(LiMMsg liMMsg, IUploadAttacResultListener iUploadAttacResultListener) {
        // ... 上传附件
        iUploadAttacResultListener.onUploadResult(true, liMMediaMessageContent);
    }
    });
```
说明：
如果自定义消息model继承LiMMediaMessageContent附件model就会回调附件监听。
详细信息查看com.limao.im.limkit.chat.msgmodel.LiMLocationContent 和com.limao.im.limkit.chat.manager.LiMaoSendMsgUtils文件
#### 删除消息监听
```java
LiMaoIm.getInstance().getMessageManager().addDeleteMsgListener(liMMsg ->{
    //...
});
```

#### 对方正在输入
```java
LiMaoIm.getInstance().getMessageManager().addTypingListener((channelID,channelType,liMChannel)){
    //channelID 频道ID
    //channelType 频道类型
    //liMChannel [channelID|channelType]这个频道中的某个人正在输入
    //注意 正在输入支持群聊和单聊
}
```

更多的消息监听可查看demo中com.limao.im.limkit.chat.ChatActivity文件