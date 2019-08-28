---
description: 以下是可帮助您配置 Android 扩展的一些信息，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-description: 以下是可帮助您配置 Android 扩展的一些信息，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-title: Android可穿戴附加备注
solution: Marketing Cloud，Analytics
title: Android可穿戴附加备注
topic: 开发人员和实施
uuid: 3bcf352b-4d46-4ab3-81ec-c27 e86 fe9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

以下是可帮助您配置 Android 扩展的一些信息，此扩展允许您从 Android 可穿戴应用程序中收集数据。

* Adobe Mobile Android 可穿戴应用程序扩展需要 Android 版本 4.4 (KitKat) 或更高版本。
* 还添加了一个额外的上下文值 `A.RunMode`，以指示数据是来自容器应用程序还是扩展。

   * `RunMode` = `Application`

      点击来自手持应用程序。

   * `RunMode` = `Extension`

      点击来自可穿戴应用程序。

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [可穿戴应用程序禁用应用程序内消息](/help/android/messaging-main/messaging/messaging.md)、 [Target](/help/android/target-main/target.md)和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 。

