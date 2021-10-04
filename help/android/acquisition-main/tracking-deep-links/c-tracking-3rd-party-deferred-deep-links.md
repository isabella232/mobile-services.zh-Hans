---
description: 使用 Android SDK 实施第三方延期深层链接跟踪。
title: 跟踪第三方延期深层链接
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
exl-id: d8cbc679-a512-44db-8c30-6a029ff738ae
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 81%

---

# 跟踪第三方延期深层链接{#tracking-third-party-deferred-deep-links}

使用 Android SDK 实施第三方延期深层链接跟踪。

## 经典 Adobe Mobile SDK 深层链接 {#section_D114FA1EB9664EAA82E036A990694B26}

Adobe Mobile SDK 当前支持深层链接，应用程序开发人员应在该链接中使用来自深层链接活动的 `collectLifecycleData` SDK API。该 SDK 会附加来自深层链接 URL 参数的深层链接数据。有关深层链接在AdobeMobile SDK中如何工作的更多信息，请参阅[跟踪深层链接](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md)。

## Facebook 深层链接 {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

广告创建者可在 Facebook 上创建一个广告作为深层链接。当用户单击该广告时，将会直接转到应用程序中他们感兴趣的信息。深层链接&#x200B;**不是**&#x200B;指纹 URL。但是，在广告配置期间，有一个选项可提供第三方深层链接 URL。使用 Adobe Mobile SDK 和服务的应用程序开发人员需在此字段中输入 Adobe Mobile Services 配置的指纹 URL。如果一切设置正确，在安装或启动应用程序时，Facebook SDK 便会将此 URL 传递到应用程序。

## 设置 SDK {#section_834CD3109175432B8173ECB6EA7DE315}

要准备通过 Adobe Mobile SDK 添加 Facebook 深层链接支持，应用程序开发人员需完成以下任务：

* 开始使用 Android SDK

   有关更多信息，请参阅 [Android SDK 快速入门](https://developers.facebook.com/docs/android/getting-started)。

* 设置深层链接

   有关更多信息，请参阅[深层链接设置](https://developers.facebook.com/docs/app-ads/deep-linking#os)。

如果应用程序设置正确，`trackAdobeDeepLink()` API 应当能够从 Facebook 客户获取促销活动中收集深层链接信息，并将收集到的信息发送至 Adobe Mobile Service。如果安装点击未在首次启动时发送到AdobeMobile Service，则此信息将添加到生命周期点击。 否则，它将作为Adobe深层链接点击发送。

>[!TIP]
>
>请确保深层链接 URL 具有一个名为 `a.deeplink.id` 的键。如果 URL 缺少深层链接 ID 参数，则不会将 URL 参数附加到上下文数据中。

如果链接可以归因于客户获取，Adobe Mobile SDK 将存储用于调用 `trackAdobeDeepLink()` 的 Facebook 深层链接中的客户获取数据。此数据将在以后的启动中可供AdobeMobile SDK使用。 如果已注册回调，则还将使用Adobe回调将数据发送回客户端。

## 在 Android 应用程序中启用深层链接 {#section_64C15E269E89424B8E3D029F88094620}

1. 注册应用程序以处理深层链接。

   有关更多信息，请参阅[允许其他应用程序启动您的活动](https://developer.android.com/training/basics/intents/filters.html)。

1. 关联 Facebook SDK。

   要在应用程序中添加 Facebook Gradle 依赖关系，请完成 [Android SDK 快速入门](https://developers.facebook.com/docs/android/getting-started)中的步骤。

1. 要初始化 Facebook SDK，请完成 *Android Studio 设置*&#x200B;部分中的说明。
1. 从主活动中调用 `trackAdobeDeepLink()`。

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
