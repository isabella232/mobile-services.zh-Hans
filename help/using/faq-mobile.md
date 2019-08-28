---
description: Adobe Mobile Services 的常见问题和解答及各项功能的一般性描述。
keywords: mobile
seo-description: Adobe Mobile Services 的常见问题和解答及各项功能的一般性描述。
seo-title: 常见问题解答
solution: Marketing Cloud，Analytics
title: 常见问题解答
topic: 量度
uuid: 62a9241c-2ada-483a-a594-b023916 cb0 b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 常见问题解答 {#frequently-asked-questions}

下表包含Adobe Mobile Services常见问题的列表：

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### 你们会经常对 SDK 进行更新吗？

是的，我们将持续不断地进行更新，以便使您获取功能最丰富且与标准格式兼容的安全 SDK。我们通常每月发布一个新版本。这些 SDK 更新（对版本 4.x）是一种直接替换，以帮助简化实施。有关我们更新的更多信息，请参阅我们的[发行说明](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)。

### 我应当采用哪个 SDK 版本？

我们当前的 SDK 为版本 4.11。有关更多信息，请参阅我们的[发行说明](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)。

### 我可从那里下载 SDK？

可通过访问 [“管理应用程序设置](/help/using/c-manage-app-settings/c-manage-app-settings.md) ”部分下载适用于单个移动平台的SDK。

### 如何配置 SDK？

创建新的应用程序报告包后，导航到“管理应用程序设置”，并在应用程序信息页面上配置所有所需的选项。在保存了配置之后，请从“管理应用程序设置”页面底部下载所需的 SDK。The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Adobe Mobile SDK 支持适用于 iOS 的 IPv6 吗？

Adobe Mobile SDK 使用标准的 iOS 和 Android 网络堆栈。对于iOS，SDK使用的NSurlLSession(iOS版本+)和nSurlConnection(iOS版本及更高版本)完全符合IPv6。构建或使用自己的联网书库的开发人员可能需要审阅是否有其他缓解注意事项。下面是Apple的一些附加信息：

*如果您使用高级联网API(如NSurllSession和CFNetwork框架并按姓名连接)编写客户端应用程序，则不需要更改任何使应用程序可使用IPv地址的应用程序。* 有关详细信息，请 [参阅支持IPv DNS64/NAT64Networks](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 什么是生命周期量度？

生命周期量度是一种“开箱即用”的量度，当您在应用程序中首次实施 SDK 时即会自动收集这种量度。有关更多信息，请参阅 [生命周期Metrics(Android)](/help/android/metrics.md) 和 [生命周期Metrics(iOS)](/help/ios/metrics.md)。

### 如何排解处理规则问题？

有关更多信息，请参阅[处理规则提示和技巧](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)。

### 我可以将我的分析数据发送到多个报表包吗？

能。SDK 提供将数据发送到多个 Adobe Analytics 报表包的功能。要通过使用图像请求捕获多个报表包中的数据，请在 文件中&#x200B;**[!UICONTROL 分析]部分下的****rsids[!UICONTROL 字段中设置多个报表包 ID，并使用逗号分隔，不留空格。]**`ADBMobileConfig.json`有关详细信息，请参阅 [AdBMobile JSON配置](/help/ios/configuration/json-config/json-config.md)。

### Mobile 访问次数为何不同于启动次数？

当用户首次打开应用程序或在离开应用程序超过指定的超时值之后又返回应用程序时，则由 SDK 计为一次启动。The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. 根据 SDK 在未超过访问超时的情况下发送的第一个和最后一个数据点击，由 Adobe Analytics 在服务器端计为一次访问。通常，报表包的会话超时设为 30 分钟。虽然访问来自传统的 Web 分析，但这些点击仍可提供有关用户如何进入和退出您的应用程序的重要分析。

## 消息传送 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 推送通知存在大小或其他限制吗？

推送通知消息具有 140 个字符的限制。对于可发送或计划的通知数量或发送通知的频率则不作任何限制。

### 你们支持推送通知的自定义负载吗？

支持，我们提供以 JSON 编码的自定义推送负载。Android 和 iOS 负载分别限制为 4KB 和 2KB。这些负载通过推送或本地通知发送到应用程序。有关更多信息，请参阅 [体验：推送消息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)。

### 应用程序内消息存在大小限制吗？

在 Adobe Mobile Services 中创建的已发布和活动的应用程序内消息托管在仅允许每个应用程序报表包大小为 15MB 的服务器上。虽然这些限制适用于 Adobe 托管的消息内容和资源，但对于应用程序内消息可能在其他主机上引用的资源或应用程序内的这些资源不作任何限制。

### 我可以将我自己的 HTML 用于应用程序内消息吗？

可以，我们支持将自定义 HTML 用于您的应用程序内消息。For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### 我可以使用哪些触发器发送推送通知或应用程序内消息？

营销人员可选择任何 Analytics 数据或事件作为触发器发送，以显示应用程序内消息。应用程序内消息使用在设备上本地发生的触发器。如果选择了多个触发器，则所有触发器必须在同一点击中发生以便使消息显示。有关更多信息，请参阅[体验：应用程序内消息](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)。

推送消息是使用预先存在的 Adobe Analytics 区段发送的，或是由可能在已收集的历史 Analytics 数据中创建的自定义区段发送的。有关更多信息，请参阅 [体验：推送消息](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### 为什么我键入了应用程序内、推送或营销链接名称出现错误？

在使用相同父报表包或 VRS 的多个应用程序中，不能使用相同的应用程序内消息、推送消息或营销链接名称。要解决此问题，请为应用程序内消息、推送消息或营销链接输入其他名称。

## 位置 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 我可以拥有多少种兴趣爱好(Pois)？

没有特别的限制，但是为了获取理想的性能及由于用户设备上的内存限制，我们建议您创建或上载最多 5000 个 POI。

## 客户获取 {#section_B37F1129CD5843E890D0E54179455357}

### 我可以将促销活动归因于应用程序内活动吗？

能。Adobe Mobile Services 可以帮助您生成营销技巧，以协助将更多流量引入到您的应用程序，而且还能将客户获取促销活动关联到应用程序内分析和转化。有关更多信息，请参阅 [](/help/using/acquisition-main/acquisition-main.md)客户赢取。

### 我可以设置链接以获取和跟踪新应用程序用户吗？

您可以创建可引导用户从Apple App Store和Google Play下载应用程序的营销链接。这些链接允许您将成功事件归因于下载。有关更多信息，请参阅 [营销链接生成器](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).