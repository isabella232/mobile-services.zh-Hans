---
description: 以下说明可帮助您通过基于设备指纹的营销链接来回访问客户赢取活动。
keywords: android；库；移动；sdk
seo-description: 以下说明可帮助您通过基于设备指纹的营销链接来回访问客户赢取活动。
seo-title: Testing Marketing Link获取
solution: Marketing Cloud，Analytics
title: Testing Marketing Link获取
topic: 开发人员和实施
uuid: 69503e01-182d-44c6-b0 fb-e1 c012 ffa3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

以下说明可帮助您通过基于设备指纹的营销链接来回访问客户赢取活动。

1. 完成 [移动App获取中的入门任务](/help/ios/acquisition-main/acquisition.md)。
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   例如：

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   有关更多信息，请参阅[营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   您应会在 JSON 响应中看到 contextData：

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 确认配置文件中的以下设置准确无误：

   | 设置 | 值 |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` 应与您的 *`appid`* 客户赢取链接相同。 |
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

   如果看不到这些日志，请确认已完成步骤和5。

   下面是一些有关可能出错的信息：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`：

      出现网络错误。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      响应的格式错误。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      响应中没有 `contextData` 参数。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` 未包含 `contextData`在内。

   * `Analytics - Acquisition referrer timed out`

      无法在 `referrerTimeout` 定义的时间内获取响应。请增加值，然后重试。您还应确保在安装应用程序之前打开客户获取链接，并且在单击 URL 和打开应用程序时，使用的是同一个网络。

请牢记以下信息：

* 客户获取服务器提供基于 IP 地址和用户代理信息的归因匹配，这些信息会在链接点击中（步骤 6）以及应用程序启动时（步骤 7）进行记录。

   在单击 URL 和打开应用程序时，您应该使用同一个网络。

* 通过使用 HTTP 监控工具，可以监控从应用程序发送的点击，以提供客户获取归因验证。

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* 发送的用户代理中的变量可能会导致归因失败。

   确保并 `https://c00.adobe.com/v3/<appid>/start``https://c00.adobe.com/v3/<appid>/end` 具有相同的用户代理值。

* 客户获取链接和来自 SDK 的点击应使用相同的 HTTP/HTTPS 协议。

   如果链接和点击使用不同协议，例如，链接使用HTTP，而SDK使用HTTPS，则每个请求上的IP地址可能在某些运营商上有所不同。这可能导致归因失败。

* 营销链接在服务器端缓存，期限为10分钟。

   当您更改营销链接时，您应等待大约10分钟才能使用链接。