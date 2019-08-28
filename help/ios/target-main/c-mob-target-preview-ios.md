---
description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
seo-title: iOS 上的“Target 预览”功能
title: iOS 上的“Target 预览”功能
uuid: d92867a4-0569-4732-a928-28f9 e2 f8 b21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# iOS 上的 Target 预览{#target-preview-on-ios}

通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>要使用Target预览，您需要SDK版本4.14.0或更高版本。

## 目标预览方法

* **setPreviewRestartDeeplink**

   在“预览”模式下应用预览选项时，可设置将要触发的应用程序深层链接。

   * 下面是这种方法对应的语法：

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
