---
description: 此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。
seo-description: 此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。
seo-title: 应用程序内消息传送
solution: Experience Cloud,Analytics
title: 应用程序内消息传送
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 100%

---


# 应用程序内消息传送 {#in-app-messaging}

此信息可帮助您在 iOS 应用程序中使用应用程序内消息传送功能。

要使用应用程序内消息传送，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.2 或更高版本。

请牢记以下信息：

* 在 Adobe Mobile Services 中创建消息用于定义消息显示时间的规则。有关更多信息，请参阅[创建应用程序内消息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。
* 必须对 SDK 进行本节所述的更新才能显示应用程序内消息。

   >[!TIP]
   >
   >即使您未定义任何消息，也可以完成这些步骤。在定义消息后，这些消息会被动态提交到您的应用程序，并且无需应用商店更新即可显示出来。

## 启用应用程序内消息 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/requirements.md)中的“将 SDK 和配置文件添加到您的项目”**。

1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 确认 `ADBMobileConfig.json` 文件中包含应用程序内消息传送所需的设置。
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
   >`messages` 或 `remotes` 是必需的。

   如果未配置这些对象，请从 Adobe Mobile Services 下载更新的 `ADBMobileConfig.json` 文件。有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/requirements.md)。

## 跟踪应用程序内消息 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile Services SDK 会跟踪应用程序内消息的以下量度：

* 对于全屏和警报样式的应用程序内消息：

   * **[!UICONTROL 展示次数]**：用户触发应用程序内消息时。
   * **[!UICONTROL 点进次数]**：用户按下&#x200B;**[!UICONTROL 点进]**&#x200B;按钮时。
   * **[!UICONTROL 取消次数]**：用户按下&#x200B;**[!UICONTROL 取消]**&#x200B;按钮时。

* 对于自定义的全屏应用程序内消息，消息中的 HTML 内容需要包含正确的代码以通知 SDK 跟踪以下按钮：

   * **[!UICONTROL 点进]**（重定向）示例跟踪： `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL 取消]**（关闭）示例跟踪：`adbinapp://cancel`

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

## 本地替代图像 {#section_DEACC1CE549B4573B556A44A52409941}

在 Adobe Mobile Services 中创建全屏消息时，您可以选择指定替代图像。如果消息无法从 Web 检索其预期图像，SDK 将尝试从应用程序包中加载同名图像。这样，即使用户处于脱机状态或预定义的图像不可访问，您也可以以原始形式显示消息。

在 Adobe Mobile Services 中配置消息时，指定替代图像资产名称。

>[!IMPORTANT]
>
>您需要确保指定的资源可用。

