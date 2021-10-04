---
description: Adobe SDK 利用 Apple 的搜索广告应用程序归因 API，让开发人员和营销人员能够跟踪源自 Apple App Store 中搜索广告促销活动的应用程序下载，并分析这些应用程序下载的归因。
solution: Experience Cloud,Analytics
title: Apple 搜索广告
topic-fix: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
exl-id: efcdd430-f08d-4ee2-85f3-2697c3bd72db
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Apple 搜索广告 {#apple-search-ads}

Adobe SDK 利用 Apple 的搜索广告应用程序归因 API，让开发人员和营销人员能够跟踪源自 Apple App Store 中搜索广告促销活动的应用程序下载，并分析这些应用程序下载的归因。有关搜索广告促销活动的更多信息，请参阅 [Apple 搜索广告](https://searchads.apple.com)。

## 优点 {#section_CEA30C652AC8470784B8054E299B80FA}

使用 Apple 广告具有以下好处：

* 通过向应用程序添加几行代码，轻松衡量搜索广告应用程序下载促销活动的有效性。
* 开发人员可以访问下载日期/时间和促进转化的竞价关键词。

## 实施 Apple 广告 {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>要实施 Apple 广告，您必须具有 iOS SDK 版本 4.13.2 或更高版本。

要对您的应用程序启用搜索广告归因，请执行以下操作：

1. 实施 Adobe SDK 版本 4.13.2 或更高版本。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)。

1. 将 iAd 框架添加到应用程序的 Xcode 项目文件中。

## 报告搜索广告归因 {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. 客户获取名称、来源和搜索词值中提供了 Apple 搜索广告归因数据。

   如果归因为 `true`，则所有 `iad-*` 字段都将包含在生命周期点击中。

   此外，以下值将从 `"iad"` 字典映射到我们典型的客户获取上下文数据字段：

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` —>  `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` —>  `"a.referrer.campaign.content"`
   * `"iad-keyword"` —>  `"a.referrer.campaign.term"`
   此映射将确保这些值可用在我们的标准报表中。
