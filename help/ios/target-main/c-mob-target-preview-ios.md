---
description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-title: iOS 上的 Target 预览
title: iOS 上的 Target 预览
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 87%

---


# iOS 上的“Target 预览”功能{#target-preview-on-ios}

通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。

有关如何设置并使用“Target 预览”功能的更多信息，请参阅 [Target 移动设备预览](https://docs.adobe.com/content/help/zh-Hans/target/using/implement-target/mobile-apps/target-mobile-preview.html)。

>[!IMPORTANT]
>
>要使用“Target 预览”功能，您需要安装 SDK 版本 4.14.0 或更高版本。

## Target 预览方法

* **setPreviewRestartDeplink**

   设置在预览模式下应用预览选择时将触发的应用程序链接。

   * 以下是此方法的语法：

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
