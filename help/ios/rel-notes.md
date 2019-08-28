---
description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-description: 适用于 Experience Cloud 解决方案的 iOS SDK 4.x 的发行说明和已知问题。
seo-title: 发行说明
solution: Marketing Cloud，Analytics
title: 发行说明
topic: 开发人员和实施
uuid: e1613dc5-02a4-43a7-93a7-997a-29b4d1d
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# 发行说明 {#release-notes}

以下是适用于Experience Cloud解决方案的iOS SDK4.x的发行说明、已知问题和修补程序信息：

**2019年月日：4.18.7版**

* 还原了版本4.18.6中引入的更改，在某些环境中，在运行iOS版本的设备上运行的设备发生崩溃。

* Adobe Target：在中添加了一个 `requestLocationParameters``ADBTargetRequestObject`属性，它允许随Target请求发送impressionID。

**2019年月18日：版本4.18.6**

* Adobe Target：现在所有请求都包含客户端和 URL 查询参数中的 `sessionId`。
* Adobe Target：修复了一个内存泄漏问题。
* 访客 ID 服务：`visitorAppendToURL` 和 `visitorGetUrlVariablesAsync` API 不再对其返回值进行双重编码。

   双重编码会导致来自这些 API 中的返回值被某些安全审阅添加标记。

**2019年月日：版本4.18.5**

* 分析-启用推送通知后，将推送选择状态追加到生命周期数据。

**2019年月24日：4.18.4版**

* 访客ID服务-增加了对
   `visitorGetUrlVariablesAsync` API到30秒。

* 访客ID服务- `setPushIdentifier` API调用现在调用访问者ID服务时发送对访问者ID服务的同步调用。

有关所有解决方案当前和以往发行说明的更多信息，请参阅 [Adobe Experience Cloud 发行说明](https://marketing.adobe.com/resources/help/en_US/whatsnew/)。
