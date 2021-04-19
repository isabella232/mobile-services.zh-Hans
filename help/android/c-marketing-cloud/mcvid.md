---
description: Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-description: Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。
seo-title: Experience Cloud ID 配置
solution: Experience Cloud,Analytics
title: Experience Cloud ID 配置
topic-fix: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
exl-id: 97dc6768-bf31-4a0d-a460-9caf9ecda5fb
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 100%

---

# Experience Cloud ID 配置 {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service 可以跨多个 Experience Cloud 解决方案提供一个通用的访客 ID。Analytics 需要 ID 服务来实现 Target、视频心率和未来的 Experience Cloud 集成。

>[!TIP]
>
>除非使用 Adobe Experience Platform Identity Service，否则无需填充此 ID。有关更多信息，请参阅 [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/zh-Hans/id-service/using/home.html)。

>[!IMPORTANT]
>
>此功能需要 SDK 版本 4.3 或更高版本。

要启用 Experience Cloud ID，请执行以下操作：

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 确认 `ADBMobileConfig.json` 文件包含 `marketingCloudorg`：

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

   如果未配置这些 ID，请从 Adobe Mobile Services 下载更新的 `ADBMobileConfig.json` 文件。有关更多信息，请参阅[开始之前](/help/android/getting-started/requirements.md)。

配置完成后，将生成一个 Experience Cloud ID，并将其包含在所有点击中。其他 ID（如自定义 ID 和自动生成的 ID）将继续随每次点击一起发送。
