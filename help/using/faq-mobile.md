---
description: Adobe Mobile Services 的常见问题和解答及各项功能的一般性描述。
keywords: mobile
seo-description: Adobe Mobile Services 的常见问题和解答及各项功能的一般性描述。
seo-title: 常见问题解答
solution: Experience Cloud,Analytics
title: 常见问题解答
topic: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 54%

---


# 常见问题解答 {#frequently-asked-questions}

下表包含 Adobe Mobile Services 的常见问题解答列表：

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### 您是否经常使用SDK进行更新？

是的，我们不断进行更新，以期为您提供功能最丰富、符合标准、最安全的SDK。 我们通常每月发布一个新版本。 这些SDK更新是直接替换（用于版本4x），以便于实施。 有关我们的更新的更多信息，请参阅我们 [的发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html)。

### 我应当采用哪个 SDK 版本？

我们当前的SDK版本为4.11。有关详细信息，请参阅我们的 [发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html)。

### 我可从那里下载 SDK？

可通过访问[管理应用程序设置](/help/using/c-manage-app-settings/c-manage-app-settings.md)部分来下载适用于各个移动平台的 SDK。

### 如何配置 SDK？

创建新应用程序报表包之后，导航到“管理应用程序设置”并在应用程序信息页面上配置所有必需选项。在保存了配置之后，请从“管理应用程序设置”页面底部下载所需的 SDK。这些 SDK 将预配置您保存的选项，并且可以在 SDK 包内的 `ADBMobileConfig.json` 文件中找到。如果您要在“管理应用程序设置”页面中更改任何 SDK 设置，请确保重新下载 SDK 文件，或更新 `ADBMobileConfig.json` 文件以对其进行必要的更改。

### Adobe移动SDK是否支持iOS的IPv6?

Adobe移动SDK使用标准iOS和Android网络堆栈。 对于 iOS，SDK 使用与 IPv6 完全兼容的 NSURLSession（iOS 版本 7 及以上版本）和 NSURLConnection（iOS 版本 7 及更高版本）。已构建或使用其自身网络堆栈的开发人员可能希望检查是否还存在其他缓解注意事项。以下是 Apple 提供的一些其他信息：

*如果您正在使用 NSURLSession 和 CFNetwork 框架之类的高级别网络 API 编写客户端应用程序并且按名称进行连接，则您应当不需要更改应用程序的任何内容即可使用 IPv6 地址。*&#x200B;有关更多信息，请参阅[支持 IPv6 DNS64/NAT64 网络](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 什么是生命周期指标？

生命周期指标是“现成”指标，在您的应用程序中首次实施SDK时自动收集。 有关更多信息，请参阅[生命周期量度 (Android)](/help/android/metrics.md) 和[生命周期量度 (iOS)](/help/ios/metrics.md)。

### 如何排解处理规则问题？

有关详细信息，请参 [阅处理规则提示和技巧](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)。

### 能否将分析数据发送到多个报表包？

可以。SDK提供向多个Adobe Analytics报告套件发送数据的能力。 要通过使用图像请求捕获多个报表包中的数据，请在 **[!UICONTROL 文件中]**&#x200B;分析&#x200B;**[!UICONTROL 部分下的]** rsids`ADBMobileConfig.json` 字段中设置多个报表包 ID，并使用逗号分隔，不留空格。有关更多信息，请参阅 [ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)。

### 移动设备访问与启动项有何不同？

当用户首次打开应用程序或在离开应用程序超过指定超时值后返回应用程序时，启动项由SDK测量。 位于 **[!UICONTROL 文件中的]** lifecycleTimeout`ADBMobileConfig.json` 字段的常规超时是 5 分钟（300 秒）。访问是Adobe Analytics在服务器端计算，它基于SDK发送的第一个和最后一个数据点击，不超过访问超时。 通常，报告套件的会话超时设置为30分钟。 尽管访问量来自传统的Web分析，但这些点击仍可提供宝贵的洞察，了解用户如何进入和退出您的应用程序。

## 消息传送 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 推送通知是否存在大小或其他限制？

推送通知消息的字符数限制为140。 可以发送或计划通知的数量或发送通知的频率没有限制。

### 是否支持推送通知的自定义有效负载？

是，我们提供可能编码为JSON的自定义推送有效负荷。 Android和iOS有效负载分别限制为4KB和2KB。 这些负载通过推送或本地通知发送到应用程序。 有关更多信息，请参阅[体验：推送消息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 应用程序内消息是否存在大小限制？

在AdobeMobile Services中创建的已发布和活动应用程序内消息托管在每个应用程序报告包大小限制为15MB的服务器上。 虽然此限制适用于托管有Adobe的消息内容和资源，但对应用程序内消息在其他主机上或应用程序中引用的资源没有限制。

### 是否可以对应用程序内消息使用我自己的HTML?

是的，我们支持针对您的应用程序内消息的自定义HTML。 有关更多信息，请参阅[体验：应用程序内消息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

### 我可以使用哪些触发器发送推送通知或应用程序内消息？

营销人员可以选择任何作为触发器发送的Analytics数据或事件来显示应用程序内消息。 应用程序内消息使用设备上本地发生的触发器。 如果选择了多个触发器，则所有触发器都必须在同一点击中发生，才能显示消息。 有关更多信息，请参阅[体验：应用程序内消息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

推送消息是使用预先存在的 Adobe Analytics 区段发送的，或是由可能在已收集的历史 Analytics 数据中创建的自定义区段发送的。有关更多信息，请参阅[体验：推送消息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 为何我键入的应用程序内消息名称、推送消息名称或营销链接名称会出现错误？

在使用相同父报表包或 VRS 的多个应用程序中，不能使用相同的应用程序内消息、推送消息或营销链接名称。要解决此问题，请为您的应用程序内消息、推送消息或营销链接输入其他名称。

## 位置 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 我可以拥有的目标点 (POI) 数量存在限制吗？

没有特别的限制，但是为了获取理想的性能以及由于用户设备上的内存限制，我们建议您创建或上传最多 5000 个 POI。

## 客户获取 {#section_B37F1129CD5843E890D0E54179455357}

### 能否将活动归因为应用程序内活动?

可以。AdobeMobile Services可以帮助您构建营销技巧，帮助提升和推动您的App流量，并将客户赢取活动与应用内分析和转化联系起来。 有关更多信息，请参阅[客户获取](/help/using/acquisition-main/acquisition-main.md)。

### 我可以设置链接以获取和跟踪新应用程序用户吗？

您可以创建营销链接，以引导用户从 Apple App Store 和 Google Play 下载应用程序。这些链接允许您将成功事件归因于下载。有关更多信息，请参阅[营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)。