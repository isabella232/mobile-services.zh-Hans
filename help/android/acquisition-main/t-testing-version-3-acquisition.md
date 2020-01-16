---
description: 此信息可帮助您对 Android 设备上的版本 3 客户获取促销活动链接进行往返测试。
keywords: android;library;mobile;sdk
seo-description: 此信息可帮助您对 Android 设备上的版本 3 客户获取促销活动链接进行往返测试。
seo-title: 测试版本 3 客户获取
solution: Marketing Cloud,Analytics
title: 测试版本 3 客户获取
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: 657e8b93d1516690ad21d6cf504f9c8f611747b6

---


# 测试 V3 客户获取 {#testing-version-acquisition}

此信息可帮助您对 Android 设备上的版本 3 客户获取促销活动链接进行往返测试。

>[!IMPORTANT]
>
>V3 中的客户获取是指您在 Adobe Mobile Services 用户界面中通过客户获取生成器创建的客户获取链接。要使用此功能，您必须升级到适用于 Experience Cloud 解决方案 4.6.0 或更高版本的 Android SDK 4.x。

如果 Google Play 中尚未提供相应的移动设备应用程序，则在创建促销活动链接时，可以选择任何移动设备应用程序作为目标。这只会影响在您单击客户获取链接后客户获取服务器将您重定向到的应用程序，而不会影响测试链接的功能。查询字符串参数将传递到 Google Play 商店，进而作为促销活动广播的一部分在安装时传递到应用程序。移动设备应用程序客户获取往返测试需要模拟此类型的广播。

>[!IMPORTANT]
>
>如果您使用Google Play安装引用API来实施，则在应用程序位于Google Play商店之前，无法测试客户获取。

每次运行测试时，必须全新安装应用程序，或清除&#x200B;**[!UICONTROL 设置]**中的数据。这可以确保在首次启动应用程序时发送与促销活动查询字符串参数关联的初始生命周期量度。

1. 完成[移动设备应用程序客户获取](/help/android/acquisition-main/acquisition.md)中的先决任务，并确保已正确实现了 `INSTALL_REFERRER` 的广播接收器。

1. In the Adobe Mobile Services UI, click  **[!UICONTROL Acquisition]**>**[!UICONTROL  Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   有关更多信息，请参阅[营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。

   例如：`https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`。

   >[!TIP]
   >
   >如果您在客户获取链接中同时引用 Android 和 iOS 应用程序，请使用 Google Play 作为默认商店。

1. 在桌面浏览器中打开生成的链接。

   您应会被重定向到 URL 与以下示例类似的页面：
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. 复制 `utm_content%3D` 后面的唯一 ID。

   在上一个示例中，ID 是 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

1. 使用步骤 3 中的唯一 ID 通过以下格式构建客户获取结束链接：

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`。

   例如：`https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

1. 在桌面浏览器中打开该链接。

   您应会在 JSON 响应中看到 `contextData`：

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   如果您没有看到 `contextData`，或者缺少某些字符串，请确保客户获取 URL 遵循[手动创建客户获取链接](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)中的格式。
1. 重复步骤 3 以获取新的唯一 ID。
1. 确认配置文件中的以下设置准确无误：

   | 设置 | 值 |
   |--- |--- |
   | acquisition | 服务器应为 `c00.adobe.com`。*`appid`*应等于您的客户获取链接中的相应`appid`。 |
   | analytics | 出于测试目的，请设置反向链接超时以允许有足够的时间（60 秒或更多）手动发送广播。您可以在测试后恢复原始超时设置。 |

1. 将设备连接到计算机，然后卸载并重新安装应用程序。
1. 启动 ADB Shell，然后在设备上启动应用程序。
1. 使用以下 `adb` 命令发送广播：

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 完成以下步骤：
   1. 将 `com.adobe.android` 替换为您的应用程序包名称。
   1. 使用您的应用程序中的促销活动跟踪接收器位置引用更新接收器引用。
   1. 替换与 `utm_content` 关联的值。
   如果广播成功，您可以看到与以下示例类似的响应：

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. （可选）您可以启用 SDK 的调试日志记录以获取其他信息。

   如果一切工作正常，您应会看到以下日志：

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

如果您没有看到以上日志，请确认您完成了步骤 6 到 12。

下表包含其他可能出现的错误相关信息：

| 错误 | 描述 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 响应的格式错误。 |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 字符串的格式错误。 |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 响应中没有 contextData 参数。 |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | contextData 中未包含 `a.referrer.campaign.name`。 |
| Analytics - Acquisition referrer timed out. | 无法在 `referrerTimeout` 定义的时间内获取响应。请增加值，然后重试。您还应该确保在安装应用程序之前，已经打开客户获取链接。 |

请牢记以下信息：

* 可以使用 HTTP 监控工具监控从应用程序发送的点击，以验证客户获取归因。
* 有关如何广播 `INSTALL_REFERRER` 的更多信息，请参阅《Google 开发人员指南》中的 [Testing Google Play Campaign Measurement](https://developers.google.com/analytics/solutions/testing-play-campaigns)（测试 Google Play 促销活动测量）。

* 针对 Android 4.8.2 中的客户获取发布了一个错误修复。

   在测试之前，请将 SDK 升级到最新版本。

* 您可以使用提供的 `acquisitionTest.jar` Java 工具来帮助获取唯一 ID 和广播安装反向链接，这反过来也可以帮助您获取步骤 3 至 12 中的信息。

   **安装 Java 工具**

要安装 Java 工具，请执行以下操作：

1. 下载 [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) 文件。

1. 提取 .jar 文件。

   您可以在命令行中运行该文件。

   例如：

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
