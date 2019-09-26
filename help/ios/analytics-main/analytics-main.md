---
description: 此信息可帮助您将 iOS SDK 与 Adobe Analytics 结合使用。
seo-description: 此信息可帮助您将 iOS SDK 与 Adobe Analytics 结合使用。
seo-title: Analytics overview
solution: Marketing Cloud,Analytics
title: Analytics overview
topic: 开发人员和实施
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Analytics overview {#analytics}

The information in this section helps you use the iOS SDK with Adobe Analytics.

## New Adobe Experience Platform Mobile SDK Release

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始使用，请转到Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 生成分析跟踪标识符

在 SDK 中，标识符用于跟踪用户，标识符的层次结构如下：

1. 自定义访客标识符 (VID)
2. Analytics 跟踪标识符 (AID)
3. Experience Cloud 标识符 (MID)

>[!TIP]
>
>Experience Cloud标识符的正确首字母缩写词是ECID。 尽管 SDK 仍然使用 MID，但它用的是旧名称。AID 有时候也被称为“跟踪标识符”，当应用程序未配置为使用 MID 时，SDK 会生成 AID。在应用程序启动和升级过程中，该值会保留在 `NSUserDefaults` 中。如果用户从其设备中删除应用程序，然后重新安装该应用程序，或者如果应用程序开发人员清除 `NSUserDefaults`，则 SDK 会生成一个新的标识符。这个流程会在 Analytics 报表中生成新用户。

对于引入身份服务支持 (MID) 的应用程序中的用户而言，现有 AID 值会随 Analytics 点击一起发送，并且 Analytics 点击包含 AID 和 MID。对于提供身份服务支持的应用程序中的新用户而言，Analytics 请求仅包含 MID。For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
