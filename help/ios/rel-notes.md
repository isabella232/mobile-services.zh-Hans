---
description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-title: 发行说明
solution: Experience Cloud,Analytics
title: 发行说明
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 53d407056dd89dcf32d1895231999b2d92e879ec
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 97%

---


# 发行说明 {#release-notes}

以下是适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明、已知问题和热修复信息：

**2021年1月13日：版本4.21.1**

* 常规——修复了在应用程序关闭期间可能导致SQLite异常的问题。

**2020 年 12 月 15 日：版本 4.21.0**

* 常规 - SDK 现在使用 XCFramework 进行分发，以支持采用新 Apple M1 架构的硬件，同时保持对现有 Intel 架构的支持。
   * 重要：升级到 AdobeMobile XCFramework 需要 Xcode 12.0 或更高版本
   * 重要：如果使用 Cocoapods，则升级到 AdobeMobile XCFramework 需要 Cocoapods 1.10.0 或更高版本

**2020 年 11 月 4 日：版本 4.20.0**

* 访客 ID 服务 - 添加了 device_convenion 状态参数，在启用/禁用广告跟踪后调用 setAdvertisingIdentifier 时使用。
* Analytics - 修复了在链接 iAd.framework 且设备启用“有限广告跟踪”后，导致 Analytics 点击在安装过程中发送延迟的错误。

**2020 年 7 月 16 日：版本 4.19.3**

* 常规 - 修复了阻止正确处理查询参数中包含多个等号的深层链接 URL 的错误。

**2020 年 3 月 24 日：版本 4.19.2**

* 常规 - 修复了 Target 代码中的一些漏洞。

**2020 年 3 月 12 日：版本 4.19.1**

* 常规 - 解决了在跟踪调用的上下文数据中包含 Swift enum 时导致的潜在崩溃问题。
* Target – Target 会话 ID 现在将作为上下文数据参数“a.target.sessionId”添加到发往 Adobe Analytics 的 Analytics for Target 内部点击中。

**2020 年 2 月 4 日：版本 4.19.0**

* 生命周期 - 添加了一个新的 API pauseCollectingLifecycleData，以缓解某些旧 iOS 设备报告的异常会话长度数据。

**2019 年 11 月 8 日：版本 4.18.9**

* 应用程序内消息 - 修复了在全屏消息中无法加载缓存或捆绑图像的错误。

**2019 年 9 月 20 日：版本 4.18.8**

* 应用程序内消息：

   * 在运行 iOS 10 或更高版本的设备上，`UserNotifications` 框架现在用于为链接到 `UserNotifications.framework` 的应用程序计划本地通知。
   * 现在，全屏消息使用 `WebKit.framework` 中的 WKWebViews，您必须将其链接到 Xcode 项目。
   * 修复了推送点进次数有效负荷无法用作应用程序内消息传送特征的错误。
   * 修复了崩溃问题。

* 常规 - 修复了每次 Analytics 调用时，SDK 数据同步到配对的 watchOS 应用程序中的错误。

**2019 年 8 月 2 日：版本 4.18.7**

* 恢复了版本 4.18.6 中引入的更改，在某些环境中，该更改会导致运行的 iOS 版本低于 11.0 的设备崩溃。

* Adobe Target：在 `ADBTargetRequestObject` 中添加了 `requestLocationParameters` 属性，该属性支持将 impressionId 与 Target 请求一起发送。

**2019 年 7 月 18 日：版本 4.18.6**

* Adobe Target：现在所有请求都包含客户端和 URL 查询参数中的 `sessionId`。
* Adobe Target：修复了一个内存泄漏问题。
* 访客 ID 服务：`visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再对其返回值进行双重编码。

   双重编码会导致来自这些 API 中的返回值被某些安全审阅添加标记。

**2019 年 6 月 5 日：版本 4.18.5**

* Analytics - 启用推送通知后，会将推送选择启用状态附加到生命周期数据。

**2019 年 5 月 24 日：版本 4.18.4**

* 访客 ID 服务 - 将
   `visitorGetUrlVariablesAsync` API 的返回超时增加到 30 秒。

* 访客 ID 服务 - `setPushIdentifier` API 调用现在会在每次调用时向访客 ID 服务发送同步调用。

有关所有解决方案当前和以往发行说明的更多信息，请参阅 [Adobe Experience Cloud 发行说明](https://docs.adobe.com/content/help/zh-Hans/release-notes/experience-cloud/current.html)。
