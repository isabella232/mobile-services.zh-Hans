---
description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
title: Android 上的“Target 预览”功能
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Android 上的“Target 预览”功能 {#target-preview-on-android}

通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。

有关如何设置和使用“Target预览”功能的更多信息，请转到Adobe Target用户指南中的[Target移动设备预览](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

>[!IMPORTANT]
>
>要使用“Target 预览”功能，您需要安装 SDK 版本 4.14.0 或更高版本。

* **setPreviewRestartDeeplink**

   设置在“预览”模式下应用预览选择时将触发的应用程序深层链接。

   * 以下是此方法的语法：

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
