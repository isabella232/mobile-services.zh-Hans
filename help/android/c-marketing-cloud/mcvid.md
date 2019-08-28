---
description: Adobe Experience Platform Identity Service跨Experience Cloud解决方案提供通用访客ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-description: Adobe Experience Platform Identity Service跨Experience Cloud解决方案提供通用访客ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-title: Experience Cloud ID配置
solution: Marketing Cloud，Analytics
title: Experience Cloud ID配置
topic: 开发人员和实施
uuid: 8ebdf2bf-c581-448f-9542-f99 a19784 fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service跨Experience Cloud解决方案提供通用访客ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。

>[!TIP]
>
>除非使用Adobe Experience Platform Identity Service，否则无需填充此ID。For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>此功能需要SDK4.3或更高版本。

要启用 Experience Cloud ID，请执行以下操作：

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *在核心实施和生命周期* 中 [将SDK和Config文件添加到IntelliJ IDEA或Eclipse项目](/help/android/getting-started/dev-qs.md)。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 验证 `ADBMobileConfig.json` 文件是否包含 `marketingCloudorg`：

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 组织 ID 唯一标识 Adobe Experience Cloud 中的每个客户公司，它类似于以下值：

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >您必须包含 `@AdobeOrg`。

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 有关更多信息，请参阅[开始之前](/help/android/getting-started/requirements.md)。

配置完成后，将生成一个 Experience Cloud ID，并将其包含在所有点击中。其他 ID（如自定义和自动生成的 ID）将继续随每次点击一起发送。
