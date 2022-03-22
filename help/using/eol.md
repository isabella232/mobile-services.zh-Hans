---
title: AdobeMobile服务生命周期终止常见问题解答
description: 获取有关AdobeMobile服务生命周期终止公告的常见问题解答。
source-git-commit: 7c3886cbc33c155e527a1d77eccbd3d99609c3d1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# AdobeMobile服务生命周期终止常见问题解答

AdobeMobile服务的终止日期为 **2022年12月31日**.

## 发生了什么？

Mobile服务于2022年12月31日终止使用。 Mobile Services在此日期之后不再支持以移动设备为中心的UI、客户获取、深层链接、应用程序内消息传送、推送通知和地理位置。

## 包含哪些内容，以及未包含哪些内容？

此生命周期终止仅包括AdobeMobile Services，它是位于 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 依赖此界面的Mobile版本4 SDK已于2021年8月31日停用。

此生命周期终止不包括适用于移动设备应用程序的Adobe Analytics，它是Adobe Experience Platform Mobile SDK的一部分。 这些功能（包括应用程序内行为、生命周期分析、消息交互跟踪和受众配置文件）将继续从Adobe获得支持。

## 为什么该功能要停用？

随着Adobe继续扩展其移动营销能力，以前在Mobile Services中提供的功能将在Adobe Experience Cloud解决方案中发布，或通过AdobeExchange Premier合作伙伴提供。 此过渡可为您提供更强大、更灵活的移动营销功能。

## 在Mobile服务中创建的现有处理规则有何变化？

[处理规则](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) 在Mobile服务UI中创建或生成的Adobe Analytics将在2022年H2版的Mobile服务生命周期终止之前自动迁移到。 迁移的处理规则的行为与Adobe Analytics中其他处理规则类似，您可以在其中自由查看或编辑这些规则。 此迁移无需用户操作。

Mobile服务停用后，所有处理规则逻辑将仅在Adobe Analytics内处理，通常包括使用 [上下文数据变量](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=en).

## 提供了哪些过渡选项？

Adobe根据贵组织的用例提供了三个过渡路径。

1. **应用程序内消息传送和推送通知**:Adobe可以将消息传递工作流转换为Adobe Journey Optimizer。 此产品可帮助组织在整个客户历程中优化和个性化体验，包括移动消息传送。
1. **客户获取和深层链接**:通过AdobeExchange Premier Partners计划提供客户获取和深层链接。 这些合作伙伴包括Adjust、AppsFlyer和Branch，它们提供广泛的客户获取功能。 Adobe的合作伙伴团队可以进行适当的介绍，以确保您找到最适合自己需求的解决方案。
1. **Places Service**:Places Service提供免费的地理位置功能。 请参阅 [Places Service文档](https://experienceleague.adobe.com/docs/places/using/home.html).

## 如果有问题，我该去哪里？

请参阅 [AdobeMobile服务生命周期终止Spark页面](https://spark.adobe.com/page/C6D30y09zaRpD/) 以了解更多信息。 如有任何其他问题，请联系您的Adobe代表。
