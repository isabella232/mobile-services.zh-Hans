---
description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
keywords: android；库；移动；sdk
seo-description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
seo-title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
solution: Marketing Cloud，Analytics
title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
topic: 开发人员和实施
uuid: 56f1ff41-0365-41dd-bdde-245c823 dff07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。

>[!IMPORTANT]
>
>需要Adobe Analytics Mobile Marketing Add-on SKU才能使Mobile Services能够访问移动获取、深层链接、地理位置和移动消息功能。有关更多信息，请与您的Adobe CSM联系。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

>[!IMPORTANT]
>
>在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 [Launch](https://launch.adobe.com/)。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

>[!IMPORTANT]
>
>虽然您可以在UI中配置功能，但直到下载生成的配置文件并将此文件添加到SDK，这些功能才会起作用。有关下载和配置SDK的信息，请参阅 [核心实施和生命周期](/help/android/getting-started/dev-qs.md)。

SDK 支持以下 Android 版本：

* SDK 版本 4.6.0 或更低版本支持 Android 2.2 (API 8) - Android 5.1.1 (API 22)
* SDK 版本 4.6.1 或更高版本支持 Android 2.3 (API 9) 或更高版本

请牢记以下信息：

* 在版本 4.2 及更高版本中，现在使用 HTTP POST 发送所有点击。

   这不会影响收集或报告的数据，但您需要使用数据包分析器来支持检查POST数据以查看点击次数。

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供了一个用户界面，以整合 Adobe Experience Cloud 中针对移动设备应用程序的移动营销功能。要了解有关该用户界面的更多信息并阅读用户文档，请参阅 [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/)。

## 发行说明 {#section_F8181DC052D44DD2A99AB40A41F6792C}

有关 Experience Cloud 发行版本的最新信息，请参阅 [Experience Cloud 发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 从 2017 年 5 月 1 日开始，将不再提供其他增强功能以及额外的工程部或 Adobe Expert Care 团队支持。
