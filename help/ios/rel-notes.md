---
description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-title: 发行说明
solution: Marketing Cloud,Analytics
title: 发行说明
topic: 开发人员和实施
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 发行说明 {#release-notes}

以下是适用于Experience cloud解决方案的iOS SDK 4.x的发行说明、已知问题和热修复信息：

**2019年9月20日：版本4.18.8**

* 应用程序内消息传递：

   * 在运行iOS 10或更高版本的设备上， `UserNotifications` 现在使用框架为链接到的应用程序计划本地通知 `UserNotifications.framework`。
   * 全屏消息现在使用Xcode项 `WebKit.framework`目中必须链接的WKWebViews。
   * 修复了推送点进有效负荷无法用作应用程序内消息传递特征的错误。
   * 修复了崩溃问题。

* 常规——修复了每次Analytics调用时SDK数据与成对的watchOS应用程序同步的错误。

**2019年8月2日：版本4.18.7**

* 恢复了版本4.18.6中引入的更改，该更改在某些环境中导致运行11.0以前版本的iOS设备上的崩溃。

* Adobe Target:在中添 `requestLocationParameters` 加了属 `ADBTargetRequestObject`性，该属性允许使impressionId随Target请求一起发送。

**2019年7月18日：版本4.18.6**

* Adobe Target：现在所有请求都包含客户端和 URL 查询参数中的 `sessionId`。
* Adobe Target：修复了一个内存泄漏问题。
* 访客 ID 服务：`visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再对其返回值进行双重编码。

   双重编码会导致来自这些 API 中的返回值被某些安全审阅添加标记。

**2019年6月5日：版本4.18.5**

* 分析——在启用推送通知时，将推送加入状态追加到生命周期数据。

**2019年5月24日：版本4.18.4**

* 访客ID服务——增加了
   `visitorGetUrlVariablesAsync` 30秒的API。

* 访客ID服务- `setPushIdentifier` API调用现在在每次调用访客ID服务时向其发送同步调用。

有关所有解决方案当前和以往发行说明的更多信息，请参阅 [Adobe Experience Cloud 发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
