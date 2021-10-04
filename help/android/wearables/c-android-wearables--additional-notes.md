---
description: 以下这些信息可帮助您配置 Android 扩展，以便能够从 Android 可穿戴应用程序收集数据。
solution: Experience Cloud,Analytics
title: Android 可穿戴应用程序：其他说明
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Android 可穿戴应用程序：其他说明{#android-wearables-additional-notes}

以下这些信息可帮助您配置 Android 扩展，以便能够从 Android 可穿戴应用程序收集数据。

* Adobe Mobile Android 可穿戴设备扩展需要具备 Android 版本 4.4 (KitKat) 或更高版本。
* 还添加了一个额外的上下文值 `A.RunMode`，以指示数据是来自容器应用程序还是扩展。

   * `RunMode` = `Application`

      点击来自便携式应用程序。

   * `RunMode` =  `Extension`

      点击来自可穿戴应用程序。

* SDK 会自动将 `aid`/`vid`/`visitor` `service id`/`privacy` 状态从便携式应用程序同步到可穿戴应用程序，因此请不要从可穿戴应用程序调用 `setPrivacyStatus`/`setUserIdentifier`/`idSync`。
* 对于可穿戴应用程序，[应用程序内消息](/help/android/messaging-main/messaging/messaging.md)、[Target](/help/android/target-main/target.md) 和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 处于禁用状态。
