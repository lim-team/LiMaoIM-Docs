---
title: "离线消息对接"
linkTitle: "离线消息对接"
date: 2020-02-06 
weight: 1070
---

如果没有设置离线消息监听，狸猫sdk只会收取在线消息。离线消息监听如下：
```java
LiMaoIm.getInstance().getMessageManager().addSyncOfflineMsgListener(new ISyncOfflineMsgListener() {
    @Override
    public void getOfflineMsgs(int max_message_seq, ISyncOfflineMsgBack iSyncOfflineMsgBack) {
        //获取离线
        MsgModel.getInstance().syncMsg((max_message_seq,500 ),list->{
            if (list != null && list.size() > 0) {
                List<LiMSyncMsg> liMMsgList = new ArrayList<>();
                for (int i = 0, size = list.size(); i < size; i++) {
                    liMMsgList.add(getLiMSyncMsg(list.get(i)));
                }
                iSyncOfflineMsgBack.onBack(false,liMMsgList);
            } else {
                iSyncOfflineMsgBack.onBack(true,null);
                //需将消息中的最大last_message_seq传递给服务器
                // ... 
                ackMsg(last_message_seq);
            }
        });
    }
});
```

详细操作请查看demo中com.limao.im.limkit.message.MsgModel文件