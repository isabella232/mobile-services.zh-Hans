---
description: You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.
keywords: mobile
seo-description: 您可以通过手动配置URL参数来创建营销链接以立即获取新的移动应用程序用户。
seo-title: Manually create Acquisition links
solution: Marketing Cloud,Analytics
title: Manually create Acquisition links
topic: 量度
uuid: d7709203-f793-4982-adaa-9c3c914aca2b
translation-type: tm+mt
source-git-commit: 54e3b2d673356a616987537d20758bef8b044db4

---


# 手动创建客户获取链接 {#create-acquisition-link-manually}

You can create Marketing Links to acquire new mobile app users on-the-fly by manually configuring the URL parameters.

>[!IMPORTANT]
>
>此功能需要SDK版本4.6或更高版本。 有关详细信息，请参阅客 [户获取先决条件](/help/using/acquisition-main/c-acquisition-prerequisites.md)。

下图说明了手动构建的跟踪链接的组件，并显示了在手动创建客户获取链接时必须正确配置的不同URL参数。

![](assets/acquisition_url.png)

此链接被配置为执行特定于平台的重定向至 Google Play 商店或 Apple App Store，以获取移动设备应用程序。如果无法确定目标，则前往默认的商店 Apple App Store。安装应用程序后，`my.custom.key:test` 自定义上下文键会附加到“Analytics 安装点击”。

要手动创建链接，请使用下面的 URL 格式：

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>您使用的Android SDK版本对此过程没有影响。

对于 iOS，请确保使用正确的协议：

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** if you are using iOS SDK 4.7.0 or later and **[!UICONTROL Use HTTPS]** **is** selected on the Manage App Settings page.

在满足下列条件的情况下：

* `{mobile-services-app-hash}` 与配置文件中的应用程序标识符 `acquisition:appid ` 匹配。

   You can locate `{mobile-services-app-hash}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` 是专门指定的标准 URL 查询参数列表.

以下是参数列表：

* **`a_g_id`**

   Google Play Store 应用程序标识符.

   * 示例值：`com.adobe.beardcons`

* **`a_g_lo`**

   Google Play Store 区域覆盖.

   * 示例值：`ko`

* **`a_i_id`**

   iTunes 应用程序标识符.

   * 示例值：`835196493`

* **`a_i_lo`**

   iTunes 区域覆盖.

   * 示例值：`jp`

* **`a_dd`**

   自动重定向的默认商店.

   * 示例值：`i | g`

* **`a_cid`**

   自定义ID覆盖（通常为iOS的IDFA或Android的ADID）。

   * 示例值：`Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * 示例值：`ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   客户获取促销活动名称.

   如果要比较不同客户获取链接的性能，此参数是报告所必需的。

   * 示例值：2015年首脑会议

* **`ctxa.referrer.campaign.trackingcode`**

   跟踪代码

   如果要比较不同客户获取链接的性能，此参数是报告所必需的。

   * 示例值：`lexsxouj`

* **`ctxa.referrer.campaign.source`**

   源。

   * 示例值：广告网络

* **`ctxa.referrer.campaign.medium`**

   媒介

   * 示例值：电子邮件

* **`ctxa.referrer.campaign.content`**

   内容

   * 示例值：图325689

* **`ctxa.referrer.campaign.term`**

   术语

   * 示例值：远足和靴子


手动创建客户获取链接时，请记住以下信息：

* 与表中参数不匹配的所有参数都将作为应用商店重定向的一部分传递。
* 从技术上讲，所有参数都是可选的，但如果至少指定了一个存储ID，则链接将不起作用。

   An example of a store ID is `a_g_id`/ `a_i_id`.

* 如果不能自动确定目标商店，并且没有提供默认值，则会返回 404 错误。

