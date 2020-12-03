---
description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-title: 隐私和《通用数据保护条例》
title: 隐私和《通用数据保护条例》
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 74%

---


# 隐私和《通用数据保护条例》{#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。

>[!IMPORTANT]
>
>**仅**&#x200B;在 Mobile SDK 版本 4.16.0 或更高版本中支持 GDPR。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

当Adobe向企业提供软件和服务时，Adobe充当数据处理者，处理和存储作为提供这些服务的一部分的任何个人数据。 作为数据处理者，Adobe根据公司的许可和指示(例如，您与Adobe的协议中规定)处理个人数据。

作为Adobe控制者，您可以使用Mobile Services SDK支持GDPR从移动应用程序检索和删除请求。

对于移动应用程序的 Adobe Mobile SDK 部分，您可以使用以下设置和方法：

* 要从 SDK 检索数据，并将该数据发送到您的服务器，请使用 `getAllIdentifiersAsync` 方法。

   有关更多信息，请参阅[检索存储的标识符](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)。

* 要设置选择状态并帮助您处理 GDPR 数据删除请求，请使用以下设置：

   * `privacyDefault`
   * `setPrivacyStatus`

   有关更多信息，请参阅[设置用户的选择状态](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)。

## 其他信息 {#section_7C7124C50D85469C8C8714533FB1A37D}

* 有关GDPR的更多信息，请参 [阅GDPR和您的业务](https://www.adobe.com/cn/privacy/general-data-protection-regulation.html)。
* To see the GDPR API documentation, go to [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html).

