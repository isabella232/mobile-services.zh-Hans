---
description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-title: 跟踪应用程序的崩溃情况
solution: Experience Cloud,Analytics
title: 跟踪应用程序的崩溃情况
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---


# 跟踪应用程序的崩溃情况 {#track-app-crashes}

此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。

>[!IMPORTANT]
>
>您应当升级到 iOS SDK 版本 4.8.6，其中包含可防止报告假崩溃的关键更改。

## Adobe 何时会报告崩溃？

如果您的应用程序未先转入后台就终止，则 SDK 会在下次启动应用程序时报告崩溃。

## 如何报告崩溃？

iOS 使用系统通知，凭借这些通知，开发人员可以跟踪应用程序生命周期中的不同状态和事件并做出响应。

Adobe Mobile iOS SDK 具有响应 `UIApplicationDidEnterBackgroundNotification` 通知的通知处理程序。在此代码中设置一个值，指示用户已将应用程序置于后台。在随后的启动中，如果找不到该值，则报告崩溃。

## Adobe 为何以这种方式测量崩溃？

这种测量崩溃的方式为以下问题提供了高级答案：“用户是否有意退出我的应用程序？”**

由 Apteligent（以前为 Crittercism）等公司提供的崩溃报告库使用全局 `NSException` 处理程序来提供更详细的崩溃报告。您的应用程序不允许具有多个此类处理程序。鉴于我们的客户可能使用其他崩溃报告提供程序，Adobe 决定不实施全局 `NSException` 处理程序，以防止出现生成错误。

## 导致报告假崩溃的原因是什么？

已知下列情形会错误地导致 SDK 报告崩溃：

* 如果您使用 Xcode 进行调试，则当应用程序在前台运行时，再次启动该应用程序会导致崩溃。

   >[!TIP]
   >
   >在这种情况下，再次从 Xcode 启动应用程序之前，先将应用程序转入后台可避免崩溃。

* 如果您的应用程序处于后台，并通过除 `trackActionFromBackground`、`trackLocation` 或 `trackBeacon` 之外的其他调用发送 Analytics 点击，且应用程序在处于后台时终止（手动或由操作系统终止），则下次启动时将会发生崩溃。

   >[!TIP]
   >
   >在 `lifecycleTimeout` 阈值以外发生的后台活动也可能会导致额外的假启动。

* 如果您的应用程序因后台获取、位置更新等原因而在后台启动，并且未进入前台就由操作系统终止，则下次启动（后台或前台）会导致崩溃。
* 如果您以编程方式从 `NSUserDefaults` 中删除 Adobe 的暂停标志，则当应用程序处于后台时，下次启动或恢复会导致崩溃。

## 如何防止报告假崩溃？

以下做法可帮助您防止报告假崩溃：

* 在 iOS SDK 4.8.6 中添加了代码，以便更好地确定是否确实需要新的生命周期会话。

   此代码修复了上一节中的第 2 个和第 3 个虚假崩溃。

* 确保对非生产报表包执行开发，这样做应该可以阻止出现第 1 个虚假崩溃。
* 不要删除或修改 Adobe Mobile SDK 在 `NSUserDefaults` 中放置的任何值。

   如果这些值在 SDK 之外发生修改，则报告的数据将无效。

