---
description: 您可以提交由任何分析数据或事件触发的应用程序内消息。实施后，消息会被动态提交到应用程序并且不需要更新代码。
seo-description: 您可以提交由任何分析数据或事件触发的应用程序内消息。实施后，消息会被动态提交到应用程序并且不需要更新代码。
seo-title: 应用程序内消息传送
solution: Marketing Cloud,Analytics
title: 应用程序内消息传送
topic: 开发人员和实施
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 应用程序内消息传送 {#in-app-messaging}

您可以提交由任何分析数据或事件触发的应用程序内消息。实施后，消息会被动态提交到应用程序并且不需要更新代码。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

>[!IMPORTANT]
>
>在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 [Launch](https://launch.adobe.com/)。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>要使用应用程序内消息传送，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.2 或更高版本。

您可以在 Adobe Mobile Services 中创建消息以及定义消息何时显示的规则。有关更多信息，请参阅[创建应用程序内消息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。要显示应用程序内消息，必须对 SDK 进行更新。即使您尚未定义任何消息，也可以完成这些步骤。在定义消息后，这些消息会被动态提交到您的应用程序，并且无需应用商店更新即可显示出来。

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参 *阅将SDK和配置文件添加到IntelliJ IDEA或Eclipse Project* (在核心实施和生命 [周期中)中](/help/android/getting-started/dev-qs.md)。

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   如果您选择了模态布局，请为消息选择以下主题之一：

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   例如：

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 在每个 `collectLifecycleData` 调用中，传递 `this` 以提供对当前活动的引用：

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` 或 `remotes` 必填。

   对于要在启动时动态更新的应用程序内消息，`remotes` 对象必须存在且进行了正确配置：

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

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 有关更多信息，请参阅[开始之前](/help/android/getting-started/requirements.md)。

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Android Mobile SDK 可跟踪应用内消息的以下量度：

* 对于全屏和警告样式的应用程序内消息：

   * **展示次数**：用户触发应用程序内消息时。
   * **点进次数**:当用户按 **[!UICONTROL 点进时]**。
   * **取消**:当用户按 **[!UICONTROL 取消时]**。

* 对于自定义的全屏应用程序内消息，消息中的 HTML 内容需要包含正确的代码以通知 SDK 跟踪以下按钮：

   * **点进率** （重定向）示例跟踪：

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **取消** （关闭）示例跟踪：

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

在创建全屏消息时，您可以选择指定一个替代图像。如果您的消息无法从 Web 中检索其预定图像，SDK 会尝试从应用程序的 assets 文件夹中加载具有相同名称的图像。这允许您显示原始格式的消息，即使用户处于离线状态或预定图像不可访问也是如此。

>[!IMPORTANT]
>
>The fallback image asset name is specified when you configure the message in Adobe Mobile services, and you need to ensure that the specified resource is available.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

以下方法允许您配置在通知区域显示的小图标和大图标，以及当通知出现在通知抽屉中时显示的大图标。

* **Config.setSmallIconResourceId(int resourceId)**

   设置将用于 SDK 创建的通知的小图标。此图标显示在状态栏中，是用户在通知中心查看完整通知时显示的辅助图像。

   * 下面是这种方法对应的语法：

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Here is the code example for this method:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   设置将用于 SDK 创建的通知的大图标。This icon is the primary image that is displayed when the user sees the complete notification in the notification center.

   * 下面是这种方法对应的语法：

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
