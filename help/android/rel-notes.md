---
description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 的发行说明和已知问题。
seo-description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 的发行说明和已知问题。
seo-title: 发行说明
solution: Marketing Cloud，Analytics
title: 发行说明
topic: 开发人员和实施
uuid: 16bb4de8-a216-47a8-928c-0b1 e1421 adf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# 发行说明 {#release-notes}

以下是适用于Experience Cloud解决方案的Android SDK4.x的发行说明、已知问题和修补程序信息：

**2019年月日：版本4.17.9**

* 访客ID服务：修复了调用Syncidentifiers时 `StrictMode` 出现的冲突。

   此违规行为是通过在主线程上阅读共享首选项引起的。

* Adobe Target：在中 `requestLocationParameters``TargetRequestObject`添加了属性，它允许随Target请求发送impressionID。

**2019年月18日：版本4.17.8**

* Adobe Target：所有请求现在都包括客户端和URL查询参数中的sessionID。
* 应用程序内消息传递：修复了如下问题：如果通过空的点击链接 URL 触发消息，则 Android 应用程序就会崩溃。
* 访客 ID 服务：`Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再对其返回值进行双重编码。

   双重编码会导致来自这些 API 中的返回值被某些安全审阅添加标记。

**2019年月日：版本4.17.7**

* 一般-针对低于20的Android API级别的网络调用现在将使用TLS1.1或TLS1.2。
* 分析-启用推送通知后，附加的推送状态到生命周期数据。

**2019年月24日：版本4.17.6**

* 访客ID服务-
   `setPushIdentifier` API调用现在每次调用访问者ID服务时发送同步调用。

* 访问者ID服务-将连接和读取超时从秒提高到秒钟。


有关所有解决方案当前和以往发行说明的更多信息，请参阅 [Adobe Experience Cloud 发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
