---
description: 以下说明可帮助您通过Android设备上的营销链接来回访问客户赢取活动。
keywords: android；库；移动；sdk
seo-description: 以下说明可帮助您通过Android设备上的营销链接来回访问客户赢取活动。
seo-title: 测试营销链接客户获取
solution: Marketing Cloud，Analytics
title: 测试营销链接客户获取
topic: 开发人员和实施
uuid: d0933dcc-8fc6-4f60-987f-7a54559aacf5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

以下说明可帮助您通过Android设备上的营销链接来回访问客户赢取活动。

如果您的移动应用程序尚未在Google Play中，您可以在创建营销链接时选择任何移动应用程序作为目标。这只会影响在您单击客户获取链接后客户获取服务器将您重定向到的应用程序，而不会影响测试客户获取链接的功能。查询字符串参数将传递到 Google Play 商店，进而作为促销活动广播的一部分在安装时传递到应用程序。移动设备应用程序客户获取往返测试需要模拟此类型的广播。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. 这可以确保在首次启动应用程序时发送与促销活动查询字符串参数关联的初始生命周期量度。

1. 完成 [移动应用程序获取](/help/android/acquisition-main/acquisition.md) 中的入门任务，确保您正确实施了广播接收器 `INSTALL_REFERRER`。
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   有关更多信息，请参阅[营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。

   例如：

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 在 Android 设备上打开生成的链接。

   您应会被重定向到 URL 与以下示例类似的页面：

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   在上一个示例中，ID为 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

   如果您无法在设备上获取唯一 ID，请在您的桌面上运行以下 `CURL` 命令，以从响应字符串中获取唯一 ID。

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   例如：

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 使用步骤 3 中的唯一 ID 通过以下格式构建客户获取结束链接：

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   For example, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 在浏览器中打开该链接。

   您应会在 JSON 响应中看到 `contextData`：

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. 重复步骤 3 以获取新的唯一 ID。
1. 确认配置文件中的以下设置准确无误：

   | 设置 | 值 |
   |--- |--- |
   | acquisition | 服务器应为 `c00.adobe.com`，并且 *`appid`* 应等于您的赢取链接 `appid` 中的内容。 |
   | analytics | 出于测试目的，请设置反向链接超时以允许有足够的时间（60 秒或更多）手动发送广播。您可以在测试后恢复原始超时设置。 |

1. 将设备连接到计算机，然后卸载并重新安装应用程序。
1. 启动 ADB Shell，然后在设备上启动应用程序。

   ```
   adb shell
   ```

1. 使用以下 `adb` 命令发送广播：

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. 将 `com.adobe.android` 替换为您的应用程序包名称，使用您的应用程序中的促销活动跟踪接收器位置引用更新接收器引用，并替换与 `utm_content` 关联的值。

   如果广播成功，您应会看到与以下示例类似的响应：

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. （可选）您可以启用 SDK 的调试日志记录以获取其他信息。

   如果一切工作正常，您应会看到以下日志：

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   如果您没有看到这些日志，请确认您已执行完步骤 6 到 10。

   下表包含其他可能出现的错误相关信息：

   | 错误 | 描述 |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | 响应的格式错误。 |
   | Analytics - Unable to parse response (`a JSON Response`). | JSON 字符串的格式错误。 |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | 响应中没有 `contextData` 参数。 |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` 不包含在ContextData中。 |
   | Analytics - Acquisition referrer timed out. | 无法在 `referrerTimeout` 定义的时间内获取响应。请增加值，然后重试。您还应该确保在安装应用程序之前，已经打开客户获取链接。 |

请牢记以下信息：

* 可以使用 HTTP 监控工具监控从应用程序发送的点击，以验证客户获取归因。
* 有关如何广播 `INSTALL_REFERRER` 的更多信息，请参阅《Google 开发人员指南》中的 [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns)（测试 Google Play 促销活动测量）。
* 您可以使用提供的 `acquisitionTest.jar` Java 工具来帮助获取唯一 ID 和广播安装反向链接，这反过来也可以帮助您获取步骤 3 至 10 中的信息。

**安装Java工具**

要安装 Java 工具，请执行以下操作：

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. 提取 .jar 文件。

   您可以在命令行中运行该 .jar 文件。

例如：

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

营销链接在服务器端缓存，期限为10分钟。如果对营销链接进行更改，再次使用这些链接之前需等待约 10 分钟，所做的更改才会生效。
