---
title: AdobeMobile Services生命周期结束常见问题解答
description: 获取有关AdobeMobile Services生命周期结束公告的常见问题解答。
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: c349c0f83df9d42b61a419ae71d6d2b67c5f7819
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 4%

---

# AdobeMobile Services生命周期结束常见问题解答

AdobeMobile Service的生命周期结束日期为 **2022年12月31日**.

## 发生什么事了？

Mobile Services将于2022年12月31日到达其生命周期结束日期。 在此日期之后，将不再支持支持以移动设备为中心的UI、客户获取、深层链接、应用程序内消息传送、推送通知和地理位置的Mobile Services。

## 包括哪些内容，未包括哪些内容？

此生命周期终止仅包括AdobeMobile Services，这是位于 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 依赖此界面的Mobile版本4 SDK已于2021年8月31日停用。

此生命周期终止不包含适用于移动设备应用程序的Adobe Analytics，它是Adobe Experience Platform Mobile SDK的一部分。 这些功能（包括应用程序内行为、生命周期分析、消息传递交互跟踪和受众配置文件）将继续获得Adobe的支持。

## 为何要弃用此功能？

随着Adobe不断扩展其移动营销功能，以前在Mobile Services中提供的功能将在Adobe Experience Cloud解决方案中发布或通过AdobeExchange Premier合作伙伴提供。 此过渡为您提供了更强大且更灵活的移动营销功能。

## 在Mobile Services中创建的现有处理规则会发生什么情况？

[处理规则](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html?lang=zh-Hans) 在Mobile Services UI中创建或生成的服务将在Mobile Services生命周期终止日期之前自动迁移到Adobe Analytics。 迁移的处理规则的行为与Adobe Analytics中的其他处理规则类似，您可以在其中自由查看或编辑这些规则。 此迁移无需用户执行任何操作。

Mobile Services失效后，所有处理规则逻辑都将在Adobe Analytics中专门处理，通常包括使用 [上下文数据变量](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=zh-Hans).

## 有哪些过渡选项可用？

Adobe根据贵组织的用例提供三种过渡路径。

1. **应用程序内消息传送和推送通知**：Adobe可将您的消息传送工作流转变为Adobe Journey Optimizer。 本产品可帮助组织优化和个性化整个客户历程中的体验，包括移动消息传递。
1. **客户获取和深层链接**：通过AdobeExchange Premier Partners计划提供客户获取和深层链接。 Adobe的合作伙伴团队可以作适当的介绍，以确保您找到最符合自己需求的解决方案。
1. **Places Service**：Places Service提供免费的地理位置功能。 请参阅 [Places Service文档](https://experienceleague.adobe.com/docs/places/using/home.html).

## 如果我有任何问题，可以去哪里？

请参阅 [AdobeMobile Services生命周期结束Spark页面](https://spark.adobe.com/page/C6D30y09zaRpD/) 了解更多信息。 如有任何其他问题，请联系您的Adobe代表。
