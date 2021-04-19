---
description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
keywords: Android;库;移动;SDK
seo-description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。
seo-title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
solution: Experience Cloud,Analytics
title: 适用于 Experience Cloud 解决方案的 Android SDK 4.x
topic-fix: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
exl-id: c2454e94-a9af-42f3-ab45-14f68531faab
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 100%

---

# 适用于 Experience Cloud 解决方案的 Android SDK 4.x{#android-sdk-x-for-experience-cloud-solutions}

适用于 Experience Cloud 解决方案的 Android SDK 4.x 允许您测量本机 Android 应用程序，在您的应用程序中提供目标内容，以及通过受众管理收集并利用受众数据。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>要允许 Mobile Services 访问移动设备客户获取、深度链接、地理定位和移动设备消息传送功能，需要安装 Adobe Analytics Mobile Marketing Add-on SKU。有关更多信息，请与您的 Adobe CSM 联系。

>[!IMPORTANT]
>
>虽然您可以在 UI 中配置功能，但配置的功能要在下载生成的配置文件并将其添加到 SDK 后才能正常工作。有关下载和配置 SDK 的信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)。

SDK 支持以下 Android 版本：

* SDK 版本 4.6.0 或更低版本支持 Android 2.2 (API 8) - Android 5.1.1 (API 22)
* SDK 版本 4.6.1 或更高版本支持 Android 2.3 (API 9) 或更高版本

请牢记以下信息：

* 在 SDK 版本 4.2 及更高版本中，现在会使用 HTTP POST 发送所有点击。

   这对收集或报告的数据没有影响，但是您将需要使用支持检查 POST 数据的数据包分析器来查看点击。

* 如果您从以前的版本进行升级，请参阅 [4.x 迁移指南](/help/android/getting-started/migration-v3.md)。

## Adobe Mobile 用户文档 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供了一个用户界面，以整合 Adobe Experience Cloud 中针对移动设备应用程序的移动营销功能。要了解有关 用户界面的更多信息并阅读用户文档，请参阅 [Adobe Mobile Services](https://docs.adobe.com/content/help/zh-Hans/mobile-services/using/home.html)。

## 发行说明 {#section_F8181DC052D44DD2A99AB40A41F6792C}

有关 Experience Cloud 发行版本的最新信息，请参阅 [Experience Cloud 发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>从 **2017 年 4 月 30 日**&#x200B;起，Adobe Bloodhound 已废止。从 2017 年 5 月 1 日开始，将不再提供其他增强功能以及额外的工程部或 Adobe Expert Care 团队支持。
