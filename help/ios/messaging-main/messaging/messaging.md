---
description: 此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。
seo-description: 此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。
seo-title: 应用程序内消息传送
solution: Marketing Cloud,Analytics
title: 应用程序内消息传送
topic: 开发人员和实施
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 应用程序内消息传送 {#in-app-messaging}

此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。

要使用应用程序内消息传送，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.2 或更高版本。

请牢记以下信息：

* 消息以及定义消息何时显示的规则在 Adobe Mobile Services 中创建。有关更多信息，请参阅[创建应用程序内消息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。
* 必须对 SDK 进行此部分中所述的更新，才能显示应用程序内消息。

   >[!TIP]
   >
   >即使您没有定义任何消息，也可以完成这些步骤。 After you define messages, they are delivered dynamically to your app and displayed without an app store update.

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 将库添加到您的项目并实施生命周期。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/requirements.md)

1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for In-App messaging.
1. 对于要在启动时动态更新的应用程序内消息，`remotes` 对象必须存在且进行了正确配置：

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` 或 `remotes` 必填。

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. For more information, see Core Implementation and Lifecycle.[](/help/ios/getting-started/requirements.md)

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile SDK 可跟踪应用内消息的以下量度：

* 对于全屏和警告样式的应用程序内消息：

   * **[!UICONTROL 展示]**:用户触发应用程序内消息时。
   * **[!UICONTROL Click throughs]**: when the user pushes the **[!UICONTROL Click-through]** button.
   * **[!UICONTROL 取消]**:当用户按下“取消” **[!UICONTROL 按钮]** 时。

* 对于自定义的全屏应用程序内消息，消息中的 HTML 内容需要包含正确的代码以通知 SDK 跟踪以下按钮：

   * **[!UICONTROL 点进率]** （重定向）示例跟踪： `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL 取消]** （关闭）示例跟踪： `adbinapp://cancel`

* 对于本地（远程）通知：

   * **[!UICONTROL 展示次数]**：用户触发通知时。
   * **[!UICONTROL 打开次数]**：用户从通知中打开应用程序时。
   以下是有关如何包含“打开次数”跟踪的示例：

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

在 Adobe Mobile Services 中创建全屏消息时，您可以选择指定替代图像。如果您的消息无法从 Web 中检索其预定图像，SDK 会尝试从应用程序包中加载具有相同名称的图像。这允许您显示原始格式的消息，即使用户处于离线状态或预定图像不可访问也是如此。

在 Adobe Mobile Services 中配置消息时，会指定替代图像资源名称。

>[!IMPORTANT]
>
>您需要确保指定的资源可用。

