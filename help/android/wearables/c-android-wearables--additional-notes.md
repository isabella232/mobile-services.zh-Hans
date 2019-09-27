---
description: 以下是可帮助您配置 Android 扩展的一些信息，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-description: 以下是可帮助您配置 Android 扩展的一些信息，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-title: Android可穿戴设备附加说明
solution: Marketing Cloud,Analytics
title: Android Wearables  Additional Notes
topic: 开发人员和实施
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
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

      The hit comes from the wearable app.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [In-app messages, Target, and Audience Manager are disabled for the wearable app.](/help/android/messaging-main/messaging/messaging.md)[](/help/android/target-main/target.md)[](/help/android/audience-manager/audiencemgmt.md)

