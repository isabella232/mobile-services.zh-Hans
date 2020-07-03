---
description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-description: 要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。
seo-title: Experience Cloud 设备协作
title: Experience Cloud 设备协作
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: ht
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: ht
source-wordcount: '290'
ht-degree: 100%

---


# Experience Cloud 设备协作 {#experience-cloud-device-co-op}

要开始使用 Experience Cloud 设备协作，请联系您的 Adobe 代表。

要为移动设备应用程序启用 Experience Cloud 设备协作，请完成以下适用于 Experience Cloud Android SDK 的步骤：

>[!IMPORTANT]
>
>此功能需要 Android SDK 版本 4.8.3 或更高版本。

从 SDK 版本 4.16.1 开始，设备协作成员可以选择在 Experience Cloud 设备协作中禁用其移动设备数据。有关更多信息，请参阅 [ADBMobile JSON 配置](/help/android/configuration/json-config/json-config.md)和用于 [isCoopSafe](https://docs.adobe.com/content/help/zh-Hans/id-service/using/id-service-api/configurations/coopsafe.html) 的 `visitorAPI.js` 方法。

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

对于要求将该值设置为 `true` 的设备协作成员，您需要与相应的协作团队合作，以申请关于您的设备协作帐户上的阻止列表标记。不存在启用这些标记的自助途径。

请牢记以下信息：

* 如果将 `coopUnsafe` 设置为 `true`，则会始终将 `coop_unsafe=1` 附加到 Audience Manager 和访客 ID 点击中。
* 如果启用到 Audience Manager 的 Analytics 服务器端转发，则还将会在 Analytics 点击中看到 `coop_unsafe=1`。