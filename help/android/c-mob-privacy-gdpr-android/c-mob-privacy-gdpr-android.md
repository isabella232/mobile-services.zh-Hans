---
description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-description: Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。
seo-title: 隐私和一般数据保护规定概述
title: Privacy and General Data Protection Regulation overview
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK 为控制器提供了已准备好遵守《通用数据保护条例》(GDPR) 的 API，它允许用户检索本地存储的身份和设置用于数据收集和传输的选择状态标记。

## New Adobe Experience Platform Mobile SDK Release

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始使用，请转到Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

当 Adobe 向企业提供软件和服务时，作为提供这些服务的一部分，Adobe 将充当数据处理器以处理和存储任何个人数据。作为数据处理器时，Adobe 将根据贵公司的授权和指示处理个人数据（例如您与 Adobe 签订的协议中的规定）。

作为数据控制器时，您可以使用 Adobe Mobile Services SDK 为来自移动设备应用程序的 GDPR 检索和删除请求提供支持。

对于移动应用程序的 Adobe Mobile SDK 部分，您可以使用以下设置和方法：

* 要从 SDK 检索数据，并将该数据发送到您的服务器，请使用 `getAllIdentifiersAsync` 方法。

   For more information, see Retrieving Stored Identifiers.[](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)

* 要设置选择状态并帮助您处理 GDPR 数据删除请求，请使用以下设置：

   * `privacyDefault`
   * `setPrivacyStatus`
   有关详细信息，请 [参阅设置用户的选择状态](/help/android/c-mob-privacy-gdpr-android/privacy.md)。