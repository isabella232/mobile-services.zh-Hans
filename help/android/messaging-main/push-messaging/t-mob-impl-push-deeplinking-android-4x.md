---
description: 在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。
title: 实施包含深层链接的推送消息
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# 实施包含深层链接的推送消息 {#implement-push-messaging-with-deep-linking}

在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。

您可以通过在 `FirebaseMessagingService` 中调用 `remoteMessage.getData().get("adb_deeplink")` 来获取 URL。

>[!TIP]
>
>您可以根据有效负荷中是否含有深层链接 URL 来定义不同的意图。

1. 完成以下任务之一：

   * 如果深层链接 URL **位于**&#x200B;推送有效负荷中，则使用该 URL 创建 `ACTION_VIEW` 意图。

      当用户单击推送消息时，会触发深层链接。

   * 如果深层链接URL **在推送有效负荷中不是**，请创建一个打开您其中一个活动的意图。

## 示例

以下是从 `FirebaseMessagingService` 扩展的类的实现示例：

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
