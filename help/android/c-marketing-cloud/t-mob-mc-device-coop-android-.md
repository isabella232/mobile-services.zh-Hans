---
description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-title: Experience Cloud 设备协作
title: Experience Cloud 设备协作
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud 设备协作 {#experience-cloud-device-co-op}

要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。

要使您的移动设备应用程序能够使用 Experience Cloud 设备协作，请完成以下适用于 Experience Cloud Android SDK 的步骤：

>[!IMPORTANT]
>
>This functionality requires Android SDK version 4.8.3 or later.

从 SDK 版本 4.16.1 开始，设备协作成员可以选择将自己的移动设备数据退出 Experience Cloud 设备协作。有关更多信息，请参阅[ADBMobile JSON 配置](/help/android/configuration/json-config/json-config.md)和适用于 `visitorAPI.js`isCoopSafe[ 的 ](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html) 方法。

1. 实施 Adobe Mobile SDK。

   For more information, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)
1. 启用您的 Experience Cloud ID。

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. 使用一种同步方法，传递经过验证的身份（如 CRM ID）或经过哈希处理的电子邮件。

   For more information, see Adobe Experience Platform Identity Service Methods.[](/help/android/c-marketing-cloud/mc-methods.md)

## `coopUnsafe` 标志

以下是关于 `coopUnsafe` 标记的其他信息：

* 最低 SDK 版本：4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* 默认值为 `false`.
* 这项设置&#x200B;**仅**&#x200B;适用于已配置设备协作的客户。

对于要求将该值设置为 `true` 的设备协作成员，您需要与相应的协作团队合作，以申请关于您的设备协作帐户上的黑名单标记。不存在启用这些标记的自助途径。

请牢记以下信息：

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.