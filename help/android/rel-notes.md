---
description: 适用于 Experience Cloud 解决方案的 Android SDK 4.x 的发行说明和已知问题。
solution: Experience Cloud,Analytics
title: 发行说明
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# 发行说明 {#release-notes}

以下是适用于 Experience Cloud 解决方案的 Android SDK 4.x 的发行说明、已知问题和热修复信息：

## 2020年4月3日：4.18.2

* 应用程序内消息 — 出于安全原因，SDK创建的WebViews现在将属性`setAllowFileAccess`设置为`false`。

## 2020年3月12日：4.18.1

* Target - Target会话ID现在作为上下文数据参数`a.target.sessionId`添加到发往Adobe Analytics的Analytics-for-Target内部点击中。

## 2020年1月16日：4.18.0

* 客户获取 - 添加了一个新的 API `Analytics.processGooglePlayInstallReferrerUrl(final String url)`，以支持 Google Play Install Referrer API。

   有关 Install Referrer API 的更多信息，请参阅[仍在使用 InstallBroadcast？在 2020 年 3 月 1 日之前切换到 Play Referrer API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)。

## 2019 年 9 月 20 日：版本 4.17.10

* 常规：修复了 Android API 级别 21 或更高级别上某些地区的区域设置字符串生成。

## 2019 年 7 月 18 日：版本 4.17.8

* Adobe Target：现在所有请求都在 URL 查询参数中包含客户端和会话 ID。
* 应用程序内消息传送：修复了以下问题：当通过空的点进URL触发消息时，Android应用程序崩溃。
* 访客 ID 服务：`Visitor.appendToURL` 和 `Visitor.getUrlVariablesAsync` API 不再对其返回值进行双重编码。

   双重编码会导致来自这些 API 中的返回值被某些安全审阅添加标记。

## 2019 年 6 月 6 日：版本 4.17.7

* 常规 - 低于 20 的 Android API 级别上的网络调用现在将使用 TLS 1.1 或 TLS 1.2。
* Analytics - 启用推送通知后，会将推送选择启用状态附加到生命周期数据。

## 2019 年 5 月 24 日：版本 4.17.6

* 访客ID服务 — `setPushIdentifier` API调用现在会在每次调用时向访客ID服务发送同步调用。
* 访客 ID 服务 - 将连接和读取超时从 2 秒增加到 5 秒。

有关所有解决方案当前和以往发行说明的更多信息，请参阅 [Adobe Experience Cloud 发行说明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html)。
