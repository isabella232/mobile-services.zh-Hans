---
description: 您可以发送从任何 Analytics 数据或事件触发的应用程序内消息。实施后，消息将动态传送到应用程序，无需代码更新。
seo-description: 您可以发送从任何 Analytics 数据或事件触发的应用程序内消息。实施后，消息将动态传送到应用程序，无需代码更新。
seo-title: 应用程序内消息传送
solution: Experience Cloud,Analytics
title: 应用程序内消息传送
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---

# 应用程序内消息传送 {#in-app-messaging}

您可以发送从任何 Analytics 数据或事件触发的应用程序内消息。实施后，消息将动态传送到应用程序，无需代码更新。

## 新的 Adobe Experience Cloud SDK 版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

>[!IMPORTANT]
>
>在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 [Launch](https://launch.adobe.com/)。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> 如果您要在 Adobe Launch 中使用 Adobe Experience Platform Mobile SDK，则还&#x200B;**必须**&#x200B;安装 Adobe Analytics Mobile Services 扩展才能使用 Adobe Mobile Services 功能，例如应用程序内消息传送和推送通知。有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。有关在 Experience Cloud SDK 中使用推送消息和应用程序内消息传送的更多信息，请参阅[设置推送消息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)和[设置应用程序内消息传送](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)。

>[!IMPORTANT]
>
>要使用应用程序内消息传送，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.2 或更高版本。

您可以在 Adobe Mobile Services 中创建消息，以及定义何时显示消息的规则。有关更多信息，请参阅[创建应用程序内消息](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)。要显示应用程序内消息，必须对 SDK 进行更新。即使尚未定义任何消息，您也可以完成这些步骤。在定义消息后，这些消息将被动态发送到您的应用程序，并且无需应用商店更新即可显示出来。

## 启用应用程序内消息传送 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

1. 更新 `AndroidManifest.xml` 文件以声明全屏活动，并启用消息通知处理程序：

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

1. 确认 `ADBMobileConfig.json` 文件中包含应用程序内消息传送所需的设置。

   >[!IMPORTANT]
   >
   >`messages` 或 `remotes` 是必需的。

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

   如果未配置此对象，请从 Adobe Mobile Services 下载更新的 `ADBMobileConfig.json` 文件。有关更多信息，请参阅[开始之前](/help/android/getting-started/requirements.md)。

## 跟踪应用程序内消息 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Adobe Mobile SDK 会跟踪应用程序内消息的以下量度：

* 对于全屏和警报样式的应用程序内消息：

   * **展示次数**：用户触发应用程序内消息时。
   * **点进次数**：用户按下&#x200B;**[!UICONTROL 点进]**&#x200B;时。
   * **取消次数**：用户按下&#x200B;**[!UICONTROL 取消]**&#x200B;时。

* 对于自定义的全屏应用程序内消息，消息中的 HTML 内容需要包含正确的代码以通知 SDK 跟踪以下按钮：

   * **点进**（重定向）示例跟踪：

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **取消**（关闭）示例跟踪：

      `adbinapp://cancel`

## 本地替代图像 {#section_DEACC1CE549B4573B556A44A52409941}

创建全屏消息时，您可以选择指定一个替代图像。如果信息无法从 Web 检索其预期图像，SDK 会尝试从应用程序的 assets 文件夹加载同名图像。这样，即使用户处于脱机状态或预定义的图像不可访问，您也可以以原始形式显示消息。

>[!IMPORTANT]
>
>在 Adobe Mobile Services 中配置消息时，会指定替代图像资产名称，为此您需要确保指定的资源可用。

## 配置通知图标 {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

以下方法允许您配置在通知区域显示的小图标和大图标，以及当通知出现在通知抽屉中时显示的大图标。

* **Config.setSmallIconResourceId(int resourceId)**

   设置将用于 SDK 创建的通知的小图标。此图标将显示在状态栏中，并且是用户在通知中心查看完整通知时显示的辅助图像。

   * 以下是此方法的语法：

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   设置将用于 SDK 创建的通知的大图标。此图标是用户在通知中心查看完整通知时显示的主要图像。

   * 以下是此方法的语法：

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
