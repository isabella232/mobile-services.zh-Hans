---
description: Adobe移动和Adobe移动SDK允许您向用户发送推送消息。 SDK还允许您轻松报告在点击推送消息后已打开您的应用程序的用户。
seo-description: Adobe移动和Adobe移动SDK允许您向用户发送推送消息。 SDK还允许您轻松报告在点击推送消息后已打开您的应用程序的用户。
seo-title: 推送消息
solution: Experience Cloud,Analytics
title: 推送消息
topic: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 61%

---


# 推送消息 {#push-messaging}

Adobe移动和Adobe移动SDK允许您向用户发送推送消息。 SDK还允许您轻松报告在点击推送消息后已打开您的应用程序的用户。

要使用推送消息，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.6 或更高版本。

>[!IMPORTANT]
>
>请不要在您的应用程序中手动设置 Experience Cloud ID。这会导致创建一个新的唯一用户，该用户由于选择加入状态而无法接收推送消息。 例如，用户已选择接收登录到您的应用程序的推送消息。 登录后，如果您在应用程序中手动设置ID，则会创建一个未选择接收推送消息的新唯一用户。 该新用户将不会接收您的推送消息。
>
>不支持将应用程序移动到新的报表包。如果迁移到新报表包，则推送配置可能会中断，并且可能无法发送消息。

## 启用推送消息 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>如果您的应用程序已设置为使用通过 Firebase Cloud Messaging (FCM) 的消息传送，下面有些步骤可能已经完成。

1. 确认 `ADBMobileConfig.json` 文件中包含推送消息所需的设置。

   `"marketingCloud"` 对象必须为推送消息配置了其 `"org"` 属性。

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. 使用 Firebase Cloud Messaging (FCM) API 获取注册 ID /令牌。

   * 有关设置 FCM 的更多信息，请参阅 [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client)（在 Android 上设置 Firebase Cloud Messaging 客户端应用程序）。

   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. 必须使用 `Config.setPushIdentifier(final String registrationId)` 方法将注册 ID/令牌传递到 SDK。

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. 通过在 `collectLifecycleData` 方法中传递您的活动来启用报表。

   以下是启用推送点进报表的要求：

   * 在 `FireBaseMessageService` 的实现中，必须将包含消息数据（将与 RemoteMessage 对象一起被传递到 `onMessageReceived` 方法中）的包对象添加到用于在点进时打开目标活动的意图中。可以使用 `putExtras` 方法来完成此操作。有关更多信息，请参阅 [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))）。

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 在点进的目标活动中，必须通过 `collectLifecycleData` 调用将该活动传递到 SDK 中。

      请牢记以下信息：

      * 使用 `Config.collectLifecycleData(this)` 或 `Config.collectLifecycleData(this, contextData)`。

      * **不要**&#x200B;使用 `Config.collectLifecycleData()`。



