---
description: 要使用Experience Cloud Device Co-op进行开始，请与Adobe代表联系。
seo-description: 要使用Experience Cloud Device Co-op进行开始，请与Adobe代表联系。
seo-title: Experience Cloud 设备协作
title: Experience Cloud 设备协作
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud 设备协作 {#experience-cloud-device-co-op}

要使用Experience Cloud Device Co-op进行开始，请与Adobe代表联系。

要为Experience Cloud设备合作社启用移动应用程序，请完成Experience Cloud Android SDK的以下步骤：

>[!IMPORTANT]
>
>此功能需要 Android SDK 版本 4.8.3 或更高版本。

从SDK版本4.16.1开始，设备合作社成员可以从Experience Cloud设备合作社中选择其移动设备数据。 有关详细信息，请 [参阅ADBMobile JSON](/help/android/configuration/json-config/json-config.md) Config和 `visitorAPI.js` isCoopSafe [的方法](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html)。

1. 实施 Adobe Mobile SDK。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)。
1. 启用您的 Experience Cloud ID。

   有关更多信息，请参阅 [Experience Cloud ID 配置](/help/android/c-marketing-cloud/mcvid.md)。
1. 使用一种同步方法，传递经过验证的身份（如 CRM ID）或经过哈希处理的电子邮件。

   有关更多信息，请参阅 [Adobe Experience Platform Identity Service 方法](/help/android/c-marketing-cloud/mc-methods.md)。

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