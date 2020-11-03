---
description: 此信息可帮助您将 iOS SDK 与 Adobe Analytics 结合使用。
seo-description: 此信息可帮助您将 iOS SDK 与 Adobe Analytics 结合使用。
seo-title: Analytics 概述
solution: Experience Cloud,Analytics
title: Analytics 概述
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 100%

---


# Analytics 概述 {#analytics}

此部分中的信息可帮助您将 iOS SDK 与 Adobe Analytics 结合使用。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 生成 Analytics 跟踪标识符

在 SDK 中，使用标识符来跟踪用户，下面是标识符的层次结构：

1. 自定义访客标识符 (VID)
1. Analytics 跟踪标识符 (AID)
1. Experience Cloud 标识符 (MID)

>[!TIP]
>
>Experience Cloud 标识符的正确首字母缩略词是 ECID。尽管 SDK 仍然使用 MID，但它用的是旧名称。

AID 有时候也被称为“跟踪标识符”，当应用程序未配置为使用 MID 时，SDK 会生成 AID。在应用程序启动和升级过程中，该值会保留在 `NSUserDefaults` 中。如果用户从其设备中删除应用程序，然后重新安装该应用程序，或者如果应用程序开发人员清除 `NSUserDefaults`，则 SDK 会生成一个新的标识符。此流程会导致在 Analytics 报表中创建新用户。

对于引入了 Identity 服务支持 (MID) 的应用程序中的用户，现有 AID 值会随 Analytics 点击一起发送，并且 Analytics 点击包含 AID 和 MID。对于具有 Identity 服务支持的应用程序中的新用户，Analytics 请求仅包含 MID。有关识别访客的更多信息，请参阅[识别访客](https://docs.adobe.com/content/help/zh-Hans/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)。
