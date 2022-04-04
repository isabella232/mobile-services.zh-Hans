---
description: 此信息可帮助您使用 App Transport Security (ATS)，这是 iOS 9 的一组新安全要求。
solution: Experience Cloud Services,Analytics
title: App Transport Security
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# App Transport Security {#app-transport-security}

此信息可帮助您使用 App Transport Security (ATS)，这是 iOS 9 的一组新安全要求。

从 iOS 9 开始，Apple 推出了 App Transport Security，这是一组符合安全连接最佳实践的要求。有关更多信息，请参阅[信息属性列表键参考](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)中的 *NSAppTransportSecurity*。

要使 Adobe Mobile SDK 版本 4.7 或更高版本能够与 ATS 无缝配合使用，请使用“管理应用程序设置”页面中的“启用 SSL”选项。有关更多信息，请参阅[管理应用程序设置](/help/using/c-manage-app-settings/c-manage-app-settings.md)或 [ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)。

在 Adobe Mobile Services 中，选择“管理应用程序设置”页面中的&#x200B;**[!UICONTROL 使用 HTTPS]** 选项后，将通过 HTTPS 发送来自 Analytics、Audience Manager、Target 和 Adobe Experience Platform Identity Service 的所有点击。

作为替代方法，您可以将以下服务器放在“允许”列表中：

| 产品 | 说明 |
|--- |--- |
| Analytics | 要允许 Analytics 服务器，请将您的跟踪服务器域作为 ATS 的例外域添加到 info.plist 文件中。可以在 `ADBMobileConfig.json` 文件的 Analytics 部分或“管理应用程序设置”页面的 Analytics 部分找到跟踪服务器域。 |
| Audience Manager | 可以在 `ADBMobileConfig.json` 文件中 audienceManager 对象的服务器属性中找到 Audience Manager 域。如果您的应用程序中使用了 Audience Manager，但未启用 SSL，请将此服务器作为 ATS 的例外域添加到 `Info.plist` 文件中。 |
| Target | 您可以将 Target 端点作为 ATS 的例外域添加到 Info.plist 文件中。要查找 Target 端点，请在 `ADBMobileConfig.json` 文件的目标对象中找到 `clientCodeproperty`。您的端点将为 `https://{clientCode}.tt.omtrdc.net`。例如，如果 `clientCodeproperty` 为 `"myCompany"`，则您的端点将为 `https://myCompany.tt.omtrdc.net`。 |
| Adobe Experience Platform Identity Service | 您可以将 Experience Cloud 服务器作为 ATS 的例外域添加到 `Info.plist` 文件中。此域为 `dpm.demdex.net`。 |
| Mobile Services：客户获取 | 在 `Info.plist` 文件中允许将客户获取服务器作为 ATS 的例外域。此域为 `c00.adobe.com`。 |
| Mobile Services：应用程序内消息 | 如果您使用的是应用程序内消息，则可能需要将您使用的非 HTTPS 的每个 URL 条目添加到 ATS 的例外域中。此列表包含托管的图像以及嵌入到自定义全屏消息 HTML 中的任何 URL。有关在 `info.plist` 文件中设置例外域的更多详细信息，请参阅“表 2：App Transport Security 词典主键”**&#x200B;中的“NSExceptionDomains”**&#x200B;行。另请参阅[信息属性列表键参考](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)中的&#x200B;*表 3：例外域词典键*。 |

>[!TIP]
>
>这些考虑事项会影响 Adobe Mobile SDK 建立的连接，但不会影响 Web 视图或您的应用程序建立的其他连接。
