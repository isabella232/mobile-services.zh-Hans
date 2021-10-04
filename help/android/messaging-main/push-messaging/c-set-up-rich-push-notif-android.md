---
description: 您可以将图像文件附加到Android通知。 添加可视化组件可以显着提高用户对推送通知的参与度。
title: 接收富推送通知
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
exl-id: 5776411c-aa0e-4e67-83aa-e78f5d1ed4f7
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 68%

---

# 接收富推送通知 {#receive-rich-push-notifications}

您可以将图像文件附加到Android通知。 添加可视化组件可以显着提高用户对推送通知的参与度。

## 处理传入富推送消息 (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

如果应用程序处于前台，推送消息将由扩展 `FirebaseMessagingService` 类的应用程序处理，并通过以下方式在清单文件中声明：

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>包含 `onMessageReceived()` 实现的类用于处理接收到的数据。

如果推送消息包含媒体 URL，则该 URL 将在传递到 `onMessageReceived()` 函数的 `RemoteMessage` 参数中可用。要使用的键为 `attachment-url`，如以下代码示例中所示：

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>设置 `NotificationCompat.BigPictureStyle` 后，大图像可能无法显示。要确保始终显示大图像，请设置本机 `Notification.BigPictureStyle`。

## 富推送通知示例 {#section_6819316BEDDE45108413B541CA2BB2DC}

以下是一个包含图像的富推送通知示例：

![](assets/rich-push-notification_example.png)

有关Android富推送通知的更多信息，请参阅[使用富通知](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html)。
