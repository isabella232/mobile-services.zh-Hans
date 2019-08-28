---
description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-title: 隐私和通用数据保护条例
title: 隐私和通用数据保护条例
uuid: 69bb82de-1993-440c-a1 b0-8d37919 b48 b6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 隐私和通用数据保护条例 {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

当 Adobe 向企业提供软件和服务时，作为提供这些服务的一部分，Adobe 将充当数据处理器以处理和存储任何个人数据。作为数据处理器时，Adobe 将根据贵公司的授权和指示处理个人数据（例如您与 Adobe 签订的协议中的规定）。

作为数据控制器时，您可以使用 Adobe Mobile Services SDK 为来自移动设备应用程序的 GDPR 检索和删除请求提供支持。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。


对于移动应用程序的 Adobe Mobile SDK 部分，您可以使用以下设置和方法：

* 要从 SDK 检索数据，并将该数据发送到您的服务器，请使用 `getAllIdentifiersAsync` 方法。

   有关详细信息，请参阅 [检索已存储的标识符](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)。

* 要设置选择状态并帮助您处理 GDPR 数据删除请求，请使用以下设置：

   * `privacyDefault`
   * `setPrivacyStatus`
   有关详细信息，请参阅 [设置用户的Opt状态](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)。

## 其他信息 {#section_7C7124C50D85469C8C8714533FB1A37D}

* 有关 GDPR 的更多信息，请参阅 [GDPR 与您的业务](https://www.adobe.com/privacy/general-data-protection-regulation.html)。
* 要查看 GDPR API 文档，请转到[通用数据保护条例 API](https://adobe.io/apis/cloudplatform/gdpr.html)。

