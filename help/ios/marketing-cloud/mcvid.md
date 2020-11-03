---
description: Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-description: Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。

>[!TIP]
>
>除非使用 Adobe Experience Platform Identity Service，否则无需填充 Experience Cloud ID。有关更多信息，请参阅 [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html)。

**需要 SDK 版本 4.3 或更高版本**

## 启用 Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 确认 `ADBMobileConfig.json` 文件包含 `marketingCloud` `org`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 组织 ID 唯一标识 Adobe Experience Cloud 中的每个客户公司，它类似于以下值：`016D5C175213CCA80A490D05@AdobeOrg`。

   >[!IMPORTANT]
   >
   >您必须包含 `@AdobeOrg`。

   如果不存在这些值，请从 Adobe Mobile Services 下载更新的 `ADBMobileConfig.json` 文件。有关更多信息，请参阅 [ADBMobile JSON 配置](/help/ios/getting-started/requirements.md)。

配置完成后，将生成一个 Experience Cloud ID，并将其包含在所有点击中。其他访客 ID（如自定义和自动生成的访客 ID）将继续随每次点击一起发送。
