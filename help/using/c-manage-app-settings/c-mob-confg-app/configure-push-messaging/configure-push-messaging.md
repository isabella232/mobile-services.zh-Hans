---
description: 创建新应用程序或编辑现有应用程序时，您可以使用此帮助信息在“管理应用程序设置”页面上配置“推送服务”选项。
keywords: mobile
seo-description: 创建新应用程序或编辑现有应用程序时，您可以使用此帮助信息在“管理应用程序设置”页面上配置“推送服务”选项。
seo-title: 配置推送消息
solution: Experience Cloud,Analytics
title: 配置推送消息
topic: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---


# 配置推送消息{#configure-push-messaging}

创建新应用程序或编辑现有应用程序时，您可以使用此帮助信息在“管理应用程序设置”页面上配置“推送服务”选项。

在配置推送消息之前，请先完成[启用推送消息的先决条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)中的先决任务。

* **报表包注意事项**

   您可以在每个报表包中配置一个用于 Apple 的应用商店应用程序和一个用于 Google 的应用商店应用程序。如果您需要其他应用商店应用程序，例如，一个用于生产环境的应用商店应用程序和一个用于开发环境的应用商店应用程序，请为每个环境分别设置一个新的应用商店应用程序和一个新的报表包。

>[!IMPORTANT]
>
>不支持将应用程序移动到新的报表包。如果迁移到新报表包，则推送配置可能会中断，并且可能无法发送消息。

1. 在&#x200B;**[!UICONTROL 推送服务]**&#x200B;下的以下字段中键入相应信息：

   * Apple

      **[!UICONTROL 私钥]**

      浏览并选择有效的私钥 `.p12`、`.key` 或 `.pen`。

      >[!IMPORTANT]
      >如果为输入&#x200B;**[!UICONTROL 私钥]**&#x200B;选择的文件还包含证书，则不需要指定证书。

   * **[!UICONTROL 证书]**

      指定有效的证书。仅当输入的&#x200B;**[!UICONTROL 私钥]****不**&#x200B;含证书时，才需要使用此选项。有关获取 SSL 证书和私钥的更多信息，请参阅[配置应用程序以使用 APNS 或 FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

   * Google

      **[!UICONTROL API 密钥]**

      指定有效的 API 密钥。有关获取 API 密钥的更多信息，请参阅[配置应用程序以使用 APNS 或 FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

      有关更多信息，请参阅以下主题：

      * [Android 中的推送消息](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOS 中的推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. 单击&#x200B;**[!UICONTROL 保存]**。
