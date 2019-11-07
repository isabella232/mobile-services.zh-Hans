---
description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-title: Experience Cloud 设备协作
title: Experience Cloud 设备协作
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud 设备协作 {#experience-cloud-device-co-op}

要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。

要使您的移动设备应用程序能够使用 Experience Cloud 设备协作，请完成以下适用于 Experience Cloud iOS SDK 的步骤。

>[!IMPORTANT]
>
>此功能需要 iOS SDK 版本 4.8.5 或更高版本。

从 SDK 版本 4.16.1 开始，设备协作成员可以选择将自己的移动设备数据退出 Experience Cloud 设备协作。有关更多信息，请参阅 [ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)和适用于 `visitorAPI.js`isCoopSafe[ 的 ](https://marketing.adobe.com/resources/help/zh_CN/mcvid/mcvid-coopsafe.html) 方法。

1. 实施 Adobe Mobile SDK。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)。
1. 启用您的 Experience Cloud ID。

   有关更多信息，请参阅 [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。
1. 使用此处包含的同步方法之一传递经过验证的身份（如 CRM ID）或经过哈希处理的电子邮件。

   有关更多信息，请参阅 [Adobe Experience Platform Identity Service 方法](/help/ios/marketing-cloud/mc-methods.md)。

## `coopUnsafe` 标记

以下是关于 `coopUnsafe` 标记的其他信息：

* 最低 SDK 版本：4.16.1
* `marketingCloud` 对象的布尔属性，将该属性设置为 `true` 后，会导致设备退出 Experience Cloud 设备协作。
* 默认值为 `false`。
* 这项设置&#x200B;**仅**&#x200B;适用于已配置设备协作的客户。

对于要求将该值设置为 `true` 的设备协作成员，您需要与相应的协作团队合作，以申请关于您的设备协作帐户上的黑名单标记。不存在启用这些标记的自助途径。

请牢记以下信息：

* 如果将 `coopUnsafe` 设置为 `true`，则会始终将 `coop_unsafe=1` 附加到 Audience Manager 和访客 ID 点击中。
* 如果启用到 Audience Manager 的 Analytics 服务器端转发，则还将会在 Analytics 点击中看到 `coop_unsafe=1`。


