---
description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。
seo-description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。
seo-title: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x
solution: Marketing Cloud,Analytics
title: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x
topic: 开发人员和实施
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: ht
source-git-commit: 6d92beff55f359d667b399e66bae4cbffa4a1a0a

---


# 适用于 Experience Cloud 解决方案的 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

适用于 Experience Cloud 解决方案的 iOS SDK 4.x 允许您测量本机 Apple iPhone 和 iPad 应用程序，在您的应用程序内提供目标内容，以及通过 Audience Manager 收集并利用受众数据。

>[!IMPORTANT]
>
>要允许 Mobile Services 访问移动设备客户获取、深度链接、地理定位和移动设备消息传送功能，需要安装 Adobe Analytics Mobile Marketing Add-on SKU。有关更多信息，请与您的 Adobe CSM 联系。

>[!IMPORTANT]
>
>现在，适用于 Experience Cloud 解决方案的 iOS SDK 4.x 支持 [iOS 13 和 Xcode 11](https://developer.apple.com/ios/)。要确保无缝兼容，请使用最新版本的 4.x iOS SDK。有关最新版本的更多信息，请参阅[发行说明](/help/ios/rel-notes.md)。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

请牢记以下信息：

* 支持 iOS 5 或更高版本

   对于 iOS 11 或更高版本，**必须**&#x200B;安装 SDK 版本 4.13.8 或更高版本。

* 在此 SDK 的版本 4.2 及更高版本中，现在使用 HTTP POST 发送所有点击。

   这对收集或报告的数据没有影响，但是您将需要使用支持检查 POST 数据的数据包分析器来查看点击。

* 如果您从以前的版本（2.x 或 3.x）进行升级，请参阅 [4.x 迁移指南](/help/ios/getting-started/migration-v3.md)。

## Adobe Mobile 用户文档 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services 提供了新的用户界面，以整合 Adobe Experience Cloud 中针对移动设备应用程序的移动营销功能。最初，Mobile Services 无缝集成了 Adobe Analytics、Adobe Audience Manager 和 Adobe Target 解决方案以及 Adobe Experience Platform Identity Service 中的应用程序分析功能和定位功能。

要了解有关 Mobile Services 用户界面的更多信息并阅读用户文档，请参阅 [Adobe Mobile Services](/help/using/home.md)。

## 使用 Bloodhound

>[!IMPORTANT]
>
>从 **2017 年 4 月 30 日**&#x200B;起，Adobe Bloodhound 已废止。从 2017 年 5 月 1 日开始，将不再提供其他增强功能以及额外的工程部或 Adobe Expert Care 团队支持。
