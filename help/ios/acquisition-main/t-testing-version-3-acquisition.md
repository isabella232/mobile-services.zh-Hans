---
description: 此信息可帮助您对基于设备指纹的 V3 客户获取促销活动链接进行往返测试。
seo-description: 此信息可帮助您对基于设备指纹的 V3 客户获取促销活动链接进行往返测试。
seo-title: 测试 V3 客户获取
solution: Marketing Cloud,Analytics
title: 测试 V3 客户获取
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 测试 V3 客户获取{#testing-v-acquisition}

此信息可帮助您对基于设备指纹的 V3 客户获取促销活动链接进行往返测试。

>[!IMPORTANT]
>
>V3 客户获取是指您在 Adobe Mobile Services 用户界面中通过客户获取生成器创建的客户获取链接。要使用此功能，您必须升级到 iOS SDK 版本 4.6.0 或更高版本。

如果应用商店中尚未提供相应的移动设备应用程序，则在创建促销活动链接时，可以选择任何移动设备应用程序作为目标。这只会影响在您单击客户获取链接后客户获取服务器将您重定向到的应用程序，而不会影响测试链接的功能。

1. 完成[移动设备应用程序客户获取](/help/ios/acquisition-main/acquisition.md)中的先决任务。
1. 导航至 Adobe Mobile Services 用户界面中的&#x200B;**[!UICONTROL 客户获取生成器]**，并生成客户获取促销活动 URL。

   例如：

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   如果您在客户获取链接中同时引用 iOS 和 Android 应用程序，请使用 Apple Store 作为默认商店。
1. 在桌面浏览器中打开生成的链接，然后转到 `https://c00.adobe.com/v3/<appid>/end`。

   您应会在 JSON 响应中看到 `contextData`：

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   如果您没有看到 `contextData`，或者缺少某些内容，请确保客户获取 URL 遵循[手动创建客户获取链接](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)中指定的格式。
1. 确认配置文件中的以下设置准确无误：

   | 设置 | 值 |
   |--- |--- |
   | acquisition | 服务器应为 `c00.adobe.com`。*`appid`* 应等于您的客户获取链接中的相应 *`appid`*。 |
   | analytics | `referrerTimeout` 的值应大于 0。 |


1. （有条件）如果您的应用程序配置文件中的 `ssl` 设置为 true，请更新您的客户获取链接以使用 HTTPS 协议。
1. 在要安装应用程序的移动设备上单击生成的链接。

   Adobe 服务器 (`c00.adobe.com`) 将存储指纹并重定向到应用商店。无需下载应用程序进行测试。
1. 从您在步骤 6 中使用的相同移动设备上首次启动应用程序。

   如有必要，您可以删除并重新安装应用程序。
1. （可选）您可以启用 SDK 的调试日志记录以获取其他信息。

   如果一切工作正常，您应会看到以下日志：

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   如果您没有看到以上日志，请确保您完成了步骤 4 和 5。

   以下是关于可能出现的错误的一些信息：

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
出现网络错误。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      响应的格式错误。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      响应中没有 `contextData` 参数。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `contextData` 中未包含 `a.referrer.campaign.name`。

   * `Analytics - Acquisition referrer timed out`

      无法在 `referrerTimeout` 定义的时间内获取响应。请增加值，然后重试。您还应确保在安装应用程序之前打开客户获取链接，并且在单击 URL 和打开应用程序时，使用的是同一个网络。

      请牢记以下信息：

      * 客户获取服务器提供基于 IP 地址和用户代理信息的归因匹配，这些信息会在链接点击中（步骤 6）以及应用程序启动时（步骤 7）进行记录。

         在单击 URL 和打开应用程序时，您应该使用同一个网络。

      * 通过使用 HTTP 监控工具，可以监控从应用程序发送的点击，以提供客户获取归因验证。

         您应该会看到向客户获取服务器发送的一个 `/v3/<appid>/start` 请求和一个 `/v3/<appid>/end` 请求。发送的用户代理中的变量可能会导致归因失败。

         >[!TIP]
         >
         >确保 `https://c00.adobe.com/v3/<appid>/start` 和 `https://c00.adobe.com/v3/<appid>/end` 具有相同的用户代理值。

      * 客户获取链接和来自 SDK 的点击应使用相同的 HTTP/HTTPS 协议。

         如果它们使用的协议不同（例如，链接使用 HTTP，而 SDK 使用 HTTPS），则每个请求的 IP 地址可能会不同（对于某些运营商），从而导致归因失败。
