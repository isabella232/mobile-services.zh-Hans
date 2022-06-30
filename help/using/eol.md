---
title: AdobeMobile Services生命周期终止常见问题解答
description: 获取有关AdobeMobile Services生命周期终止公告的常见问题解答。
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: c349c0f83df9d42b61a419ae71d6d2b67c5f7819
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# AdobeMobile Services生命周期终止常见问题解答

AdobeMobile Service的生命周期终止日期为 **2022年12月31日**.

## 发生了什么？

Mobile Services于2022年12月31日终止使用。 此日期之后，将不再支持以移动设备为中心的UI、客户获取、深层链接、应用程序内消息传送、推送通知和地理位置的Mobile Services。

## 包含哪些内容，以及未包含哪些内容？

此生命周期终止仅包括AdobeMobile Services，它是位于 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 依赖此界面的Mobile版本4 SDK已于2021年8月31日停用。

此生命周期终止不包括适用于移动设备应用程序的Adobe Analytics，它是Adobe Experience Platform Mobile SDK的一部分。 这些功能（包括应用程序内行为、生命周期分析、消息交互跟踪和受众配置文件）将继续从Adobe获得支持。

## 为什么该功能要停用？

随着Adobe继续扩展其移动营销能力，Mobile Services中以前提供的功能将在Adobe Experience Cloud解决方案中发布，或通过AdobeExchange Premier合作伙伴提供。 此过渡可为您提供更强大、更灵活的移动营销功能。

## 在Mobile Services中创建的现有处理规则有何变化？

[处理规则](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) 在Mobile Services UI中创建或生成的ID将在Mobile Services生命周期终止之前自动迁移到Adobe Analytics。 迁移的处理规则的行为与Adobe Analytics中其他处理规则类似，您可以在其中自由查看或编辑这些规则。 此迁移无需用户操作。

Mobile Services停用后，所有处理规则逻辑将仅在Adobe Analytics内处理，通常包括使用 [上下文数据变量](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=zh-Hans).

## 提供了哪些过渡选项？

Adobe根据贵组织的用例提供了三个过渡路径。

1. **应用程序内消息传送和推送通知**:Adobe可以将消息传递工作流转换为Adobe Journey Optimizer。 此产品可帮助组织在整个客户历程中优化和个性化体验，包括移动消息传送。
1. **客户获取和深层链接**:通过AdobeExchange Premier Partners计划提供客户获取和深层链接。 Adobe的合作伙伴团队可以进行适当的介绍，以确保您找到最适合自己需求的解决方案。
1. **Places Service**:Places Service提供免费的地理位置功能。 请参阅 [Places Service文档](https://experienceleague.adobe.com/docs/places/using/home.html).

## 如果有问题，我该去哪里？

请参阅 [AdobeMobile Services生命周期终止Spark页面](https://spark.adobe.com/page/C6D30y09zaRpD/) 以了解更多信息。 如有任何其他问题，请联系您的Adobe代表。
