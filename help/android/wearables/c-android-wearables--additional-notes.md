---
description: 以下是一些信息，可帮助您配置Android扩展，以便从Android可穿戴应用程序收集数据。
seo-description: 以下是一些信息，可帮助您配置Android扩展，以便从Android可穿戴应用程序收集数据。
seo-title: Android 可穿戴应用程序：其他说明
solution: Experience Cloud,Analytics
title: Android 可穿戴应用程序：其他说明
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 51%

---


# Android 可穿戴应用程序：其他说明{#android-wearables-additional-notes}

以下是一些信息，可帮助您配置Android扩展，以便从Android可穿戴应用程序收集数据。

* Adobe移动Android可穿戴设备扩展需要Android版本4.4(KitKat)或更高版本。
* 还添加了一个额外的上下文值 `A.RunMode`，以指示数据是来自容器应用程序还是扩展。

   * `RunMode` = `Application`

      点击来自便携式应用程序。

   * `RunMode` = `Extension`

      点击来自可穿戴应用程序。

* SDK 会自动将 `aid`/`vid`/`visitor` `service id`/`privacy` 状态从便携式应用程序同步到可穿戴应用程序，因此请不要从可穿戴应用程序调用 `setPrivacyStatus`/`setUserIdentifier`/`idSync`。
* 对于可穿戴应用程序，[应用程序内消息](/help/android/messaging-main/messaging/messaging.md)、[Target](/help/android/target-main/target.md) 和 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 处于禁用状态。

