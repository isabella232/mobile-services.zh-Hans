---
title: AdobeMobile服务生命周期终止常见问题解答
description: 获取有关AdobeMobile服务生命周期终止公告的常见问题解答。
source-git-commit: a0f834247c328b40d0f47fdf515c239cf66b7566
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 2%

---

# AdobeMobile服务生命周期终止常见问题解答

AdobeMobile服务的终止日期为 **2022年12月31日**.

## What is happening?

Mobile Services reaches end-of-life on December 31, 2022. Mobile Services在此日期之后不再支持以移动设备为中心的UI、客户获取、深层链接、应用程序内消息传送、推送通知和地理位置。

## What is included, and what is not included?

此生命周期终止仅包括AdobeMobile Services，它是位于 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 依赖此界面的Mobile版本4 SDK已于2021年8月31日停用。

This end-of-life does NOT include Adobe Analytics for mobile apps, part of the Adobe Experience Platform Mobile SDKs. 这些功能（包括应用程序内行为、生命周期分析、消息交互跟踪和受众配置文件）将继续从Adobe获得支持。

## Why is the capability being retired?

随着Adobe继续扩展其移动营销能力，以前在Mobile Services中提供的功能将在Adobe Experience Cloud解决方案中发布，或通过AdobeExchange Premier合作伙伴提供。 此过渡可为您提供更强大、更灵活的移动营销功能。

## 在Mobile服务中创建的现有处理规则有何变化？

[Processing rules](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) created or generated in the Mobile Services UI will be automatically migrated to Adobe Analytics in H2 2022, prior to the Mobile Services end-of-life date. Migrated processing rules behave similarly to other processing rules in Adobe Analytics, where you can freely view or edit them. No user action is required for this migration.

Mobile服务停用后，所有处理规则逻辑将仅在Adobe Analytics内处理，通常包括使用 [上下文数据变量](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=zh-Hans).

## 提供了哪些过渡选项？

Adobe根据贵组织的用例提供了三个过渡路径。

1. **应用程序内消息传送和推送通知**:Adobe可以将消息传递工作流转换为Adobe Journey Optimizer。 此产品可帮助组织在整个客户历程中优化和个性化体验，包括移动消息传送。
1. **客户获取和深层链接**:通过AdobeExchange Premier Partners计划提供客户获取和深层链接。 These partners include Adjust, AppsFlyer, and Branch, who offer extensive acquisition capabilities. Adobe的合作伙伴团队可以进行适当的介绍，以确保您找到最适合自己需求的解决方案。
1. **Places Service**:Places Service提供免费的地理位置功能。 请参阅 [Places Service文档](https://experienceleague.adobe.com/docs/places/using/home.html).

## Where can I go if I have questions?

请参阅 [AdobeMobile服务生命周期终止Spark页面](https://spark.adobe.com/page/C6D30y09zaRpD/) 以了解更多信息。 Contact your Adobe representative with any additional questions.
