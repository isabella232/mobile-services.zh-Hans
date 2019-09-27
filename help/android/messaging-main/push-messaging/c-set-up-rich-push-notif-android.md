---
description: 您可以将图像文件附加到 Android 通知中。添加可视组件能够显著提高推送通知带来的用户参与度。
seo-description: 您可以将图像文件附加到 Android 通知中。添加可视组件能够显著提高推送通知带来的用户参与度。
seo-title: 接收富推送通知
title: 接收富推送通知
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

您可以将图像文件附加到 Android 通知中。添加可视组件能够显著提高推送通知带来的用户参与度。

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

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
>The class that contains the  implementation handles the data that is received.`onMessageReceived()`

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. 要使用的键为 `attachment-url`，如以下代码示例中所示：

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
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. 要确保始终显示大图像，请设置本机 `Notification.BigPictureStyle`。

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

以下是一个包含图像的富推送通知示例：

![](assets/rich-push-notification_example.png)

有关 Android 富推送通知的更多信息，请参阅 [Engage with Rich Notifications](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html)（使用富通知）。
