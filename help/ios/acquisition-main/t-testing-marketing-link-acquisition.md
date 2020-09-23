---
description: 以下说明可帮助您对使用基于设备指纹的营销链接的客户获取促销活动进行往返测试。
keywords: android;library;mobile;sdk
seo-description: 以下说明可帮助您对使用基于设备指纹的营销链接的客户获取促销活动进行往返测试。
seo-title: 测试营销链接客户获取
solution: Experience Cloud,Analytics
title: 测试营销链接客户获取
topic: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 100%

---


# 测试营销链接客户获取 {#testing-marketing-link-acquisition}

以下说明可帮助您对使用基于设备指纹的营销链接的客户获取促销活动进行往返测试。

1. 完成[移动设备应用程序客户获取](/help/ios/acquisition-main/acquisition.md)中的先决任务。
1. 在 Adobe Mobile Services 用户界面中，单击&#x200B;**[!UICONTROL 营销链接生成器]**，并生成一个客户获取营销链接 URL，以将应用商店设置为 iOS 设备的目标。

   例如：

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   有关更多信息，请参阅[营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。


1. 在 iOS 设备上打开生成的链接，然后打开 `https://c00.adobe.com/v3/<appid>/end`。

   您应会在 JSON 响应中看到 contextData：

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 确认配置文件中的以下设置准确无误：

   | 设置 | 值 |
   |--- |--- |
   | acquisition | 服务器应为 `c00.adobe.com`。`appid` 应等于您的客户获取链接中的相应 *`appid`*。 |
   | analytics | `referrerTimeout` 的值应大于 0。 |

1. （有条件）如果您的应用程序配置文件中的 SSL 设置为 `false`，请更新您的客户获取链接以使用 HTTP 协议而不是 HTTPS。
1. 在要安装应用程序的移动设备上单击生成的链接。

   Adobe 服务器 (`c00.adobe.com`) 将存储指纹并重定向到应用商店。无需下载应用程序进行测试。
1. 从您在步骤 6 中使用的相同移动设备上首次启动应用程序。

   如有必要，您可以删除并重新安装应用程序。
1. （可选）启用 SDK 的调试日志记录以获取其他信息。

   如果一切工作正常，您应会看到以下日志：

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   如果您没有看到这些日志，请确认您已完成步骤 4 和 5。

   以下是关于可能出现的错误的一些信息：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`：

      出现网络错误。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      响应的格式错误。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      响应中没有 `contextData` 参数。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `contextData` 中未包含 `a.referrer.campaign.name`。

   * `Analytics - Acquisition referrer timed out`

      无法在 `referrerTimeout` 定义的时间内获取响应。请增加值，然后重试。您还应该确保：先打开客户获取链接，然后再安装应用程序；以及在单击 URL 和打开应用程序时，使用的是同一网络。

请牢记以下信息：

* 客户获取服务器提供基于 IP 地址和用户代理信息的归因匹配，这些信息会在链接点击中（步骤 6）以及应用程序启动时（步骤 7）进行记录。

   在单击 URL 和打开应用程序时，您应该使用同一个网络。

* 通过使用 HTTP 监控工具，可以监控从应用程序发送的点击，以提供客户获取归因验证。

   您应该会看到向客户获取服务器发送的一个 `/v3/<appid>/start` 请求和一个 `/v3/<appid>/end` 请求。

* 发送的用户代理中的变量可能会导致归因失败。

   确保 `https://c00.adobe.com/v3/<appid>/start` 和 `https://c00.adobe.com/v3/<appid>/end` 具有相同的用户代理值。

* 客户获取链接和来自 SDK 的点击应使用相同的 HTTP/HTTPS 协议。

   如果该链接和点击使用的协议不同（例如，链接使用 HTTP，而 SDK 使用 HTTPS），则每个请求的 IP 地址可能会不同（对于某些运营商）。这可能导致归因失败。

* 营销链接缓存在服务器端，过期时间为 10 分钟。

   当您对营销链接做出更改时，您应当等待大约 10 分钟后再使用该链接。