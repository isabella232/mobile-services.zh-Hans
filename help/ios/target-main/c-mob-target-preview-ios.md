---
description: 通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。
title: iOS 上的 Target 预览
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# iOS 上的 Target 预览{#target-preview-on-ios}

通过“Target 预览”功能，您可以轻松地对 Target 活动执行端到端的 QA 操作，并在设备上预览这些活动。

有关如何设置和使用“Target预览”功能的更多信息，请参阅Adobe Target文档中的[Target移动设备预览](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) 。

>[!IMPORTANT]
>
>要使用“Target 预览”功能，您需要安装 SDK 版本 4.14.0 或更高版本。

## Target 预览方法

* **setPreviewRestartDeeplink**

   设置在“预览”模式下应用预览选择时将触发的应用程序深层链接。

   * 以下是此方法的语法：

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
