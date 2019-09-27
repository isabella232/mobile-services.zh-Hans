---
description: 创建新应用程序或编辑现有应用程序时，您可以使用此帮助信息在“管理应用程序设置”页面上配置“推送服务”选项。
keywords: mobile
seo-description: 创建新应用程序或编辑现有应用程序时，您可以使用此帮助信息在“管理应用程序设置”页面上配置“推送服务”选项。
seo-title: 配置推送消息
solution: Marketing Cloud,Analytics
title: 配置推送消息
topic: 量度
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

您可以使用此信息来帮助您在创建新应用程序或编辑现有应用程序时，在“管理应用程序设置”页面上配置“推送服务”选项。

在配置推送消息之前，请完成“启用推送消息的先决条件” [中的入门项目任务](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)。

* **报表包注意事项**

   您可以在每个报表包中为 Apple 和 Google 各配置一个应用商店应用程序。如果您需要更多的应用程序，例如用于生产环境的应用程序和用于开发环境的应用程序，您可以为每个环境设置一个新的应用商店应用程序和一个新报表包。

>[!IMPORTANT]
>
>不支持将应用程序移至新的报表包。 如果迁移到新报表包，则推送配置可能会中断，并且可能无法发送消息。

1. Type information in the following fields under **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL 私钥]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL 证书]**

      指定有效的证书。仅当输入的&#x200B;**[!UICONTROL 私钥]****不**&#x200B;含证书时，才需要使用此选项。For more information about obtaining the SSL certificate and private key, see Configure App to use APNS or FCM.[](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)

   * Google

      **[!UICONTROL API 密钥]**

      指定有效的 API 密钥。For more information about obtaining the API key, see Configure App to use APNS or FCM.[](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)

      有关更多信息，请参阅以下主题：

      * [Android中的推送消息](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOS中的推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. 单击&#x200B;**[!UICONTROL 保存]**。
