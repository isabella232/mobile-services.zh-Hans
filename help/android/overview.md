---
description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
keywords: android;library;mobile;sdk
seo-description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
seo-title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
solution: Marketing Cloud,Analytics
title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
topic: 开发人员和实施
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。

## New Adobe Experience Platform Mobile SDK Release

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* To get started, go to Adobe Experience Platform Launch.
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>The Adobe Analytics Mobile Marketing Add-on SKU is required to enable Mobile Services access to mobile acquisition, deep linking, geolocation, and mobile messaging capabilities. For more information, contact your Adobe CSM.

>[!IMPORTANT]
>
>Although you can configure features in the UI, these features will not work until you download the generated configuration file and add this file to the SDK. 有关下载和配置SDK的信息，请参阅核 [心实施和生命周期](/help/android/getting-started/dev-qs.md)。

SDK 支持以下 Android 版本：

* SDK 版本 4.6.0 或更低版本支持 Android 2.2 (API 8) - Android 5.1.1 (API 22)
* SDK 版本 4.6.1 或更高版本支持 Android 2.3 (API 9) 或更高版本

请牢记以下信息：

* 在版本 4.2 及更高版本中，现在使用 HTTP POST 发送所有点击。

   This has no impact on the data that is collected or reported, but you need to use a packet analyzer that supports inspecting POST data to view hits.

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
