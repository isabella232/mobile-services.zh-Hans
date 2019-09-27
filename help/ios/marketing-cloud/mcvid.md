---
description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-description: Adobe Experience Platform Identity service可跨Experience cloud解决方案提供通用访客ID。 Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: 开发人员和实施
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity service可跨Experience cloud解决方案提供通用访客ID。 Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。

>[!TIP]
>
>除非您使用Adobe Experience Platform Identity Service，否则您无需填充Experience Cloud ID。 For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**需要 SDK 版本 4.3 或更高版本**

## 启用Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参 *阅在核心实施和生命周期中将SDK和配置文件添加*[到您的项目中](/help/ios/getting-started/dev-qs.md)。
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 验证文件 `ADBMobileConfig.json` 是否包含 `marketingCloud``org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >您必须包含 `@AdobeOrg`。

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 有关详细信息，请参 [阅ADBMobile JSON配置](/help/ios/getting-started/requirements.md)。

配置后，将生成一个 Experience Cloud ID，并将其包含在所有点击中。其他访客 ID（如自定义和自动生成的访客 ID）将继续随每次点击一起发送。
