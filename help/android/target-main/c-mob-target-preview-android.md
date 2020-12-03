---
description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-title: Android 上的“Target 预览”功能
title: Android 上的“Target 预览”功能
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Android 上的“Target 预览”功能 {#target-preview-on-android}

通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/zh-Hans/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

