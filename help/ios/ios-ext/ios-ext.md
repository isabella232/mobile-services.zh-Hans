---
description: 您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。
seo-description: 您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。
seo-title: iOS 扩展实施
solution: Experience Cloud,Analytics
title: iOS 扩展实施
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 80%

---


# iOS 扩展实施 {#ios-extension-implementation}

您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 有关使用 iOS SDK 而不使用包装器的建议 {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>我们强烈建议您使用 iOS SDK，而不要使用包装器。

Apple提供一组API，通过向包含的应用程序发送请求并接收响应，Watch应用程序可与包含的应用程序通信。 尽管您可以将跟踪数据作为词典从 Watch 应用程序发送到容器应用程序，然后在容器应用程序中调用任何跟踪方法来发送数据，但是这种解决方案存在局限性。

大多数情况下，当用户使用 Watch 应用程序时，容器应用程序将在后台运行，只有调用 `TrackActionInBackground`、`TrackLocation` 和 `TrackBeacon` 才是安全的。调用其他跟踪方法会干扰生命周期数据，因此您应该专门使用这三种方法，从 Watch 应用程序中发送数据。

即使这三种跟踪方法符合您的要求，仍请使用 iOS SDK，因为该适用于 Watch 应用程序的 SDK 包含除应用程序内消息传送之外的所有移动功能。

## 入门指南 {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>确保您的项目至少具有以下目标：
>
>* 一个目标，用于包含应用程序。
>* 一个目标用于扩展。

>



如果您正在使用WatchKit应用程序，您应该有第三个目标。 有关为 Apple Watch 开发的更多信息，请参阅[为 Apple Watch 开发](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)。

## 配置容器应用程序 {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

在您的 Xcode 项目中完成以下步骤：

1. 将 AdobeMobileLibrary 文件夹拖动到您的项目中。
1. 确保 `ADBMobileConfig.json` 文件是容器应用程序目标的成员。
1. 在容器应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 打开容器应用程序目标的&#x200B;**[!UICONTROL 功能]**&#x200B;选项卡，启用&#x200B;**[!UICONTROL 应用程序组]**，然后添加一个新的应用程序组（例如，`group.com.adobe.testAp`）。

1. 与 Adobe Mobile 库进行任何交互之前，在应用程序委托的 `application:didFinishLaunchingWithOptions` 中设置该应用程序组：

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 确认您的应用程序在生成时没有出现意外错误。

## 配置扩展 {#section_28C994B7892340AC8D1F07AF26FF3946}

1. 确保 `ADBMobileConfig.json` 文件是扩展目标的成员。
1. 在扩展目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 打开扩展目标的&#x200B;**[!UICONTROL 功能]**&#x200B;选项卡，启用&#x200B;**[!UICONTROL 应用程序组]**，然后选择您在上面“配置容器应用程序”**&#x200B;的步骤 4 中添加的应用程序组。

1. 与 Adobe Mobile 库进行任何交互之前，在 InterfaceController 的 `awakeWithContext:` 中设置该应用程序组：

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 确认您的应用程序在生成时没有出现意外错误。

## 其他说明 {#section_21497E81231549CB9F164DEECFF5BA0D}

请牢记以下信息：

* 添加了一个额外的上下文数据值 `a.RunMode`，以指示数据是来自容器应用程序还是扩展：

   * `a.RunMode = Application`

      此值表示点击来自容器应用程序。
   * `a.RunMode = Extension`

      此值表示点击来自扩展。

* 如果您从旧版SDK升级，则在启动包含的应用程序时，Adobe会自动将所有用户默认值和缓存的文件从包含的应用程序的文件夹迁移到应用程序组的共享文件夹。
* 如果从未启动包含的应用程序，则会放弃扩展的点击。
* 版本号和内部版本号必须在包含的应用程序和扩展应用程序之间相同。
* iOS扩展应用程序上不会触发生命周期调用。

