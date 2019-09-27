---
description: 在应用程序中配置推送消息之前，您必须先完成这些任务。
keywords: mobile
seo-description: 在应用程序中配置推送消息之前，您必须先完成这些任务。
seo-title: 启用推送消息的先决条件
solution: Marketing Cloud,Analytics
title: 启用推送消息的先决条件
topic: 量度
uuid: 194e6e07-b794-4152-a838-a4125c3292d4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Prerequisites to enable push messaging {#prerequisites-to-enable-push-messaging}

You must complete these tasks before configuring push messaging in your applications.

## 为您的公司启用Experience Cloud

您的 Adobe Analytics 公司必须已启用 Experience Cloud。您可以验证您的Adobe客户经理的状态。

## 安装和配置Mobile SDK

* **安装 Mobile SDK**

   要配置推送消息，您必须下载并安装至少4.6版或更高版本的Mobile SDK。 For more information, see [Download the SDKs](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **配置推送服务**

   您必须在 Mobile SDK 中配置推送服务。有关更多信息，请参阅以下内容：

   * [Android中的推送消息](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [iOS中的推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md)

## 使用您的Adobe ID登录到Mobile Core Service

>[!IMPORTANT]
>
>要使用推送服务功能，用户必须使用Adobe ID登录Mobile Core Service，并且其Analytics帐户必须链接到其Adobe ID。 如果用户使用他们现有的 Adobe Analytics 帐户登录，将无法使用推送服务功能。

如果用户没有 Adobe ID，请完成以下步骤：

1. (**Experience Cloud Administrator**) Invite users to the Experience Cloud.

1. (**User**) Create a personal Adobe ID using the instructions that you received from the Experience Cloud administrator.

   管理员完成上一步骤后，系统会自动向每个用户发送电子邮件消息。

1. (**Users**) Log in to Mobile using their Adobe ID.

## 在Experience Cloud中关联用户帐户

每个用户必须关联 Experience Cloud 组织内的 Analytics 解决方案帐户。

1. 要使用 Adobe ID 登录到 Experience Cloud，请在浏览器中键入 [https://marketing.adobe.com](https://marketing.adobe.com)。

1. 选择位于右上角的 Analytics 公司名称。

1. 单击&#x200B;**[!UICONTROL 添加组织]**，然后从下拉列表中选择 **Adobe SiteCatalyst/Adobe Social[!UICONTROL 。]**

1. Type the company name, your legacy credentials for the specified company, and click **[!UICONTROL Link Account]**.

   Adobe ID 现在已关联到您的 Analytics 帐户、公司和登录凭据。

有关详细信息，请参阅[排查帐户关联问题](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)。

## Configure push services and the SDK ID service in the Mobile User Interface

在为您的应用程序启用 ID 服务之前，**[!UICONTROL 推送服务]部分处于禁用状态。**&#x200B;但是，在启用ID服务后，“推送服务”部分即会启用。 有关启用推送服务的详细信息，请参 [阅配置SDK ID服务选项](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)。

>[!IMPORTANT]:必须单击“ **[!UICONTROL 保存]** ”以保存更改并刷新推送服务。
>
>您可以在每个报表包中为 Apple 和 Google 各配置一个应用商店应用程序。如果您需要更多的应用程序，例如用于生产环境的应用程序和用于开发环境的应用程序，您可以为每个环境设置一个新的应用商店应用程序和一个新报表包。

* 对于 **Apple**：拖放您的私钥和/或证书。如果您的私钥是用密码加密的，请键入其密码。

   * 对于&#x200B;**私钥**：将您的私钥拖放到框中。

      您还可以单击&#x200B;**[!UICONTROL 浏览]以选择该文件。**&#x200B;此文件包含私钥。The certificate might also be included in this file (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * 对于&#x200B;**私钥密码**：如果您的私钥文件已加密，请键入密码。

      （可选）对于&#x200B;**证书**：将您的证书文件拖放到框中。您还可以单击&#x200B;**[!UICONTROL 浏览]以选择该文件。** This field is not required if the private-key file also contains the certificate ( `.cert`, `.cer`, `.crt`, `.pem`).

* 对于 **Google**：指定应用程序的 API 密钥。

   单击&#x200B;**[!UICONTROL 测试]以验证是否已正确配置应用程序和 Mobile Services。**&#x200B;此选项在进行调试和疑难解答时非常有用。

   键入要接收消息的设备推送令牌。您可以在一个以逗号分隔的列表中指定令牌，以便向多个设备发送消息。

   ![推送测试消息](assets/push_test_list.png)
