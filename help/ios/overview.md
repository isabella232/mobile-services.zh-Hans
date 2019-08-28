---
description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。
seo-description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。
seo-title: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x
solution: Marketing Cloud，Analytics
title: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x
topic: 开发人员和实施
uuid: 8b374Cee-1432-460b-aac2-70623dd80 a04
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 适用于 Experience Cloud 解决方案的 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。

>[!IMPORTANT]
>
>需要Adobe Analytics Mobile Marketing Add-on SKU才能使Mobile Services能够访问移动获取、深层链接、地理位置和移动消息功能。有关更多信息，请与您的Adobe CSM联系。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

请牢记以下信息：

* 支持 iOS 5 或更高版本

   对于 iOS 11 或更高版本，**必须**&#x200B;安装 SDK 版本 4.13.8 或更高版本。

* 在此 SDK 的版本 4.2 及更高版本中，现在使用 HTTP POST 发送所有点击。

   这不会影响收集或报告的数据，但您需要使用数据包分析器来支持检查POST数据以查看点击次数。

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile 用户文档 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供了新的用户界面，以整合 Adobe Experience Cloud 中针对移动设备应用程序的移动营销功能。最初，Mobile服务可无缝集成Adobe Analytics、Adobe Audience Manager和Adobe Target解决方案以及Adobe Experience Platform Identity Service中的应用分析和定位功能。

要了解有关 Mobile Services 用户界面的更多信息并阅读用户文档，请参阅 [Adobe Mobile Services](/help/using/home.md)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 从 2017 年 5 月 1 日开始，将不再提供其他增强功能以及额外的工程部或 Adobe Expert Care 团队支持。
