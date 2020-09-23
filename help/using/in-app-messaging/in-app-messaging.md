---
description: 创建、管理和报告应用程序内消息和推送消息。
keywords: mobile
seo-description: 创建、管理和报告应用程序内消息和推送消息。
seo-title: 消息传送
solution: Experience Cloud,Analytics
title: 消息传送
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 77%

---


# 消息传送 {#messaging}

您可以创建、管理和报告应用程序内消息和推送消息。

## 新的 Adobe Experience Cloud SDK 版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* To get started, go to [Launch](https://launch.adobe.com/).
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> 如果您要在 Adobe Launch 中使用 Adobe Experience Platform Mobile SDK，则还&#x200B;**必须**&#x200B;安装 Adobe Analytics Mobile Services 扩展才能使用 Adobe Mobile Services 功能，例如客户获取链接。有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。有关在 Experience Platform SDK 中使用推送消息和应用程序内消息传送的信息，请参阅[设置推送消息](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)和[设置应用程序内消息传送](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)。

## 应用程序内消息 {#section_8984F4568BC24D32A87429FFCB5184A6}

应用程序内消息会根据用户的操作和特征，实时提供给用户。消息会从 SDK 已跟踪的 Analytics 数据触发。

支持以下消息类型：

* 自定义和主题
* 全屏
* 本机警报
* 本地通知消息

为帮助您了解应用程序内消息的工作方式，下面提供了一些其他信息：

* 应用程序内消息需要安装 SDK 版本 4.2 或更高版本。
* 您必须指定谁拥有移动设备应用程序管理员权限。

   这些权限允许访问客户获取链接和应用程序内消息。有关更多信息，请参阅[角色和权限](/help/using/gs/c-mob-roles-and-permissions.md)。
* 消息获得批准后，该消息将自动发布到应用程序。
* SDK在满足消息参数(如特征、触发器和计划)时向用户显示消息。
* 消息可以包含自定义HTML或图像，使用在线URL。

   还可以为脱机时触发的消息指定应用程序包中的备份或备用映像。
* 消息激活并完成后会提供总查看次数、点进率等报表。
* 有些模板可用于自定义消息，您可以使用这些模板轻松地创建自己的应用程序内消息。

## 推送消息 {#section_90555A55BCE7427A90B1577E14BEF51B}

推送消息将发送给选择接收通知的用户。您可以将这些推送消息定位到 Analytics 区段或自定义区段中的用户。推送消息可以在应用程序之外的其他许多地方显示，因此可用于重新吸引消极用户或传达特定于时间的和位置的信息。

在配置推送消息之前，请参阅[启用推送消息的先决条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)。执行这些任务后，必须在应用程序设置中配置推送消息。 For more information, see [Configure push messaging](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
