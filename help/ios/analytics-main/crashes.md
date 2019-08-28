---
description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-title: 跟踪应用程序崩溃
solution: Marketing Cloud，Analytics
title: 跟踪应用程序崩溃
topic: 开发人员和实施
uuid: f81988b-198a-4ba9-ad53-78af90 e43856
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 跟踪应用程序的崩溃情况 {#track-app-crashes}

此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。

>[!IMPORTANT]
>
>您应该升级到iOS SDK版本4.8.6，该版本包含防止虚假崩溃的关键更改。

## Adobe 何时会报告崩溃？

如果您的应用程序未先转入后台就终止，则 SDK 会在下次启动应用程序时报告崩溃。

## 如何报告崩溃？

iOS 使用系统通知，凭借这些通知，开发人员可以跟踪应用程序生命周期中的不同状态和事件并做出响应。

Adobe Mobile iOS SDK 具有响应 `UIApplicationDidEnterBackgroundNotification` 通知的通知处理程序。在此代码中，设置了一个指示用户已将应用程序转入后台的值。在后续启动时，如果找不到该值，则会报告崩溃。

## Adobe 为何以这种方式测量崩溃？

这种测量崩溃的方式为以下问题提供了高级答案：“用户是否有意退出我的应用程序？”**

由 Apteligent（以前为 Crittercism）等公司提供的崩溃报告库使用全局 `NSException` 处理程序来提供更详细的崩溃报告。您的应用程序不允许具有多个此类处理程序。鉴于我们的客户可能使用其他崩溃报告提供程序，Adobe 决定不实施全局 `NSException` 处理程序，以防止出现生成错误。

## 导致报告假崩溃的原因是什么？

以下情况已知会错误地导致 SDK 报告崩溃：

* 如果您使用 Xcode 进行调试，则在应用程序处于前台时再次启动应用程序会导致崩溃。

   >[!TIP]
   >
   >在从Xcode再次启动应用程序之前，您可以通过本地化应用程序来避免出现崩溃。

* If your app is in the background and sends Analytics hits through a call other than `trackActionFromBackground`, `trackLocation`, or `trackBeacon`, and the app is terminated (manually or by the OS) while in the background, and the next launch will be a crash.

   >[!TIP]
   >
   >Background activity that occurs beyond the `lifecycleTimeout` threshold might also result in an additional false launch.

* 如果您的应用程序因后台获取、位置更新等原因而在后台启动，并且未进入前台就由操作系统终止，则下次启动（后台或前台）会导致崩溃。
* 如果您以编程方式从 `NSUserDefaults` 中删除 Adobe 的暂停标志，则当应用程序处于后台时，下次启动或恢复会导致崩溃。

## 如何防止报告假崩溃？

以下做法可帮助您防止报告假崩溃：

* 在 iOS SDK 4.8.6 中，添加了相应的代码以更好地确定新的生命周期会话是否为实际所需。

   此代码可修复上一部分中的第 2 种和第 3 种假崩溃。

* 确保您针对非生产性报表包执行开发，这样应当可防止发生第 1 种假崩溃。
* 不要删除或修改 Adobe Mobile SDK 在 `NSUserDefaults` 中放置的任何值。

   如果这些值在SDK之外进行修改，则报告的数据将无效。

