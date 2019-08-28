---
description: Adobe Mobile 和 Adobe Mobile SDK 允许您将推送消息发送给用户。该 SDK 还允许您轻松报告在点进推送消息后打开您的应用程序的用户。
seo-description: Adobe Mobile 和 Adobe Mobile SDK 允许您将推送消息发送给用户。该 SDK 还允许您轻松报告在点进推送消息后打开您的应用程序的用户。
seo-title: 推送消息
solution: Marketing Cloud，Analytics
title: 推送消息
topic: 开发人员和实施
uuid: 729d4010-3733-4dff-b188 ad45 bd3 e7 cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile 和 Adobe Mobile SDK 允许您将推送消息发送给用户。该 SDK 还允许您轻松报告在点进推送消息后打开您的应用程序的用户。

要使用推送消息，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.6 或更高版本。

>[!IMPORTANT]
>
>请勿在应用程序中手动设置Experience Cloud ID。这会导致创建一个新的独特用户，该用户将由于其选择启用状态而不接受推送消息。例如，某个已选择接收推送消息的用户登录到您的应用程序。登录后，如果您在应用程序中手动设置 ID，则会创建一个未选择接收推送消息的新独特用户。该新用户将不会接收您的推送消息。
>
>不支持将应用程序移至新的报表包。如果迁移到新报表包，则推送配置可能会中断，并且可能无法发送消息。

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>如果您的应用程序已经设置为通过Firebase Cloud Messaging(FCM)使用消息传递，则可能已经完成以下一些步骤。

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   `"marketingCloud"` 对象必须为推送消息配置其 `"org"` 属性。

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

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. 通过在 `collectLifecycleData` 方法中传递您的活动来启用报表。

   以下是启用推送点进报表的要求：

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. 这可以使用 `putExtras` 该方法完成。有关详细信息，请参阅 [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle)))。
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 在点进的目标活动中，必须通过 `collectLifecycleData` 调用将该活动传递到 SDK 中。

      请牢记以下信息：

      * 使用 `Config.collectLifecycleData(this)``Config.collectLifecycleData(this, contextData)`或。

      * ****`Config.collectLifecycleData()`不要使用。



