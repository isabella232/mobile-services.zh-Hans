---
description: 此信息可帮助您使用 App Transport Security (ATS)，这是 iOS 9 的一组新安全要求。
seo-description: 此信息可帮助您使用 App Transport Security (ATS)，这是 iOS 9 的一组新安全要求。
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: 开发人员和实施
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

此信息可帮助您使用 App Transport Security (ATS)，这是 iOS 9 的一组新安全要求。

从 iOS 9 开始，Apple 推出了 App Transport Security，这是一组符合安全连接最佳实践的要求。For more information, see NSAppTransportSecurity in Information Property List Key Reference.**[](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)

要使 Adobe Mobile SDK 版本 4.7 或更高版本能够与 ATS 无缝配合使用，请使用“管理应用程序设置”页面中的“启用 SSL”选项。For more information, see Manage App Settings or ADBMobile JSON Config.[](/help/using/c-manage-app-settings/c-manage-app-settings.md)[](/help/ios/configuration/json-config/json-config.md)

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

作为替代方法，您可以将以下服务器列入白名单：

| 产品 | 说明 |
|--- |--- |
| Analytics | 要将 Analytics 服务器添加到白名单，请将您的跟踪服务器域作为 ATS 的例外域添加到 info.plist 文件中。可以在 `ADBMobileConfig.json` 文件的 Analytics 部分或“管理应用程序设置”页面的 Analytics 部分找到跟踪服务器域。 |
| Audience Manager | 可以在 `ADBMobileConfig.json` 文件中 audienceManager 对象的服务器属性中找到 Audience Manager 域。如果您的应用程序中使用了 Audience Manager，但未启用 SSL，请将此服务器作为 ATS 的例外域添加到 `Info.plist` 文件中。 |
| Target | 您可以将 Target 端点作为 ATS 的例外域添加到 Info.plist 文件中。要查找 Target 端点，请在 `clientCodeproperty` 文件的目标对象中找到 `ADBMobileConfig.json`。Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | 您可以将 Experience Cloud 服务器作为 ATS 的例外域添加到 `Info.plist` 文件中。This domain is `dpm.demdex.net`. |
| Mobile Services：客户获取 | 将客户获取服务器作为 ATS 的例外域添加到 `Info.plist` 文件的白名单中。This domain is `c00.adobe.com`. |
| Mobile Services：应用程序内消息 | 如果要使用应用程序内消息，可能需要在 ATS 的例外域中为您使用的每个非 HTTPS URL 添加相应的条目。此列表包含托管的图像以及嵌入到自定义全屏消息 HTML 中的任何 URL。For more detail on setting up exceptions domain in an  file, see the NSExceptionDomains row in Table 2: App Transport Security dictionary primary keys. `info.plist`**** Also see Table 3  Exception domains dictionary keys in Information Property List Key Reference.**[](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/) |

>[!TIP]
>
>这些注意事项会影响Adobe Mobile SDK建立的连接，不会影响Web视图或应用程序建立的其他连接。

