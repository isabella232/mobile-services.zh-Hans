---
description: 使用 Android SDK 实施第三方延期深层链接跟踪。
seo-description: 使用 Android SDK 实施第三方延期深层链接跟踪。
seo-title: 跟踪第三方延期深层链接
title: 跟踪第三方延期深层链接
uuid: 4c798e478-798-4a06-a191-6c4 d05 f6 ee61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 跟踪第三方延迟深层链接{#tracking-third-party-deferred-deep-links}

使用 Android SDK 实施第三方延期深层链接跟踪。

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

Adobe Mobile SDK 当前支持深层链接，应用程序开发人员应在该链接中使用来自深层链接活动的 `collectLifecycleData` SDK API。该 SDK 会附加来自深层链接 URL 参数的深层链接数据。有关深层链接在 Adobe Mobile SDK 中的工作方式的更多信息，请参阅 [跟踪深层链接](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

广告创建者可在 Facebook 上创建一个广告作为深层链接。当用户点击广告时，该广告会直接转到应用程序中用户感兴趣的信息。深层链接&#x200B;**不是**&#x200B;指纹 URL。但是，在广告配置期间，有一个选项可提供第三方深层链接 URL。使用 Adobe Mobile SDK 和服务的应用程序开发人员应在此字段中输入 Adobe Mobile Service 配置的指纹 URL。如果一切设置正确，在安装或启动应用程序时，Facebook SDK 便会将此 URL 传递到应用程序。

## 设置 SDK {#section_834CD3109175432B8173ECB6EA7DE315}

要准备通过 Adobe Mobile SDK 添加 Facebook 深层链接支持，应用程序开发人员需完成以下任务：

* 开始使用Android SDK

   For more information, see [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) .

* 设置深层链接

   有关详细信息，请参阅 [深层链接设置](https://developers.facebook.com/docs/app-ads/deep-linking#os)。

If the application is set up correctly, the `trackAdobeDeepLink()` API should enable collecting the deep link information from the Facebook acquisition campaign and send it to Adobe Mobile Service. 如果安装点击未在首次启动时发送至 Adobe Mobile Service，此信息将被添加到生命周期点击。否则，它将作为 Adobe 深层链接点击发送。

>[!TIP]
>
>Ensure that the deep link URL has a key called `a.deeplink.id`. 如果 URL 缺少深层链接 ID 参数，则不会将 URL 参数附加到上下文数据中。

如果链接可以归因于客户获取，Adobe Mobile SDK 将存储用于调用 `trackAdobeDeepLink()` () 的 Facebook 深层链接中的客户获取数据。该数据可在以后的启动中供 Adobe Mobile SDK 使用。如果已注册回调，Adobe 回调也将用于向客户端发回数据。

## Enable deep linking in an Android application {#section_64C15E269E89424B8E3D029F88094620}

1. 注册应用程序以处理深层链接。

   有关更多信息，请参阅 [Allowing Other Apps to Start your Activity](https://developer.android.com/training/basics/intents/filters.html)（允许其他应用程序启动您的活动）。

1. 关联 Facebook SDK。

   要在应用程序中添加 Facebook Gradle 依赖关系，请完成 [Android SDK 快速入门](https://developers.facebook.com/docs/android/getting-started)中的步骤。

1. 要初始化 Facebook SDK，请完成 *Android Studio 设置*&#x200B;部分中的说明。
1. Call `trackAdobeDeepLink()` from the main activity.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

