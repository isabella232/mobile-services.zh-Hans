---
description: 您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。
seo-description: 您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。
seo-title: iOS 扩展实施
solution: Marketing Cloud，Analytics
title: iOS 扩展实施
topic: 开发人员和实施
uuid: afc03fe-403e-4643-ada1-30e403 ee238
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# iOS extension implementation {#ios-extension-implementation}

您可以使用 iOS 扩展帮助从 Apple Watch 应用程序 (WatchOS 1)、“今天”小组件、照片编辑小组件以及其他 iOS 扩展应用程序中收集使用情况数据。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>我们强烈建议您使用iOS SDK而不是您的包装器。

Apple 提供了一组允许 Watch 应用程序与容器应用程序进行通信（方法是向容器应用程序发送请求，然后接收响应）的 API。尽管您可以将跟踪数据作为词典从 Watch 应用程序发送到容器应用程序，然后在容器应用程序中调用任何跟踪方法来发送数据，但是这种解决方案存在局限性。

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. 调用其他跟踪方法会干扰生命周期数据，因此您应该专门使用这三种方法，从 Watch 应用程序中发送数据。

即使这三种跟踪方法符合您的要求，仍请使用 iOS SDK，因为该适用于 Watch 应用程序的 SDK 包含除应用程序内消息传送之外的所有移动功能。

## 入门指南 {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>确保您具有至少以下目标的项目：
>
>* 一个用于包含应用程序的目标。
>* 一个用于扩展的目标。
>



如果您正在使用 WatchKit 应用程序，则还应具有第三个目标。有关为Apple Watch开发的详细信息，请参阅 [为Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)开发。

## 配置包含的应用程序 {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

在您的 Xcode 项目中完成以下步骤：

1. 将 AdobeMobileLibrary 文件夹拖动到您的项目中。
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. 在容器应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. 与 Adobe Mobile 库进行任何交互之前，在应用程序委托的 `application:didFinishLaunchingWithOptions` 中设置该应用程序组：

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 确认您的应用程序在生成时没有出现意外错误。

## 配置扩展 {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. 在扩展目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 确认您的应用程序在生成时没有出现意外错误。

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

请牢记以下信息：

* 添加了一个额外的上下文数据值 `a.RunMode`，以指示数据是来自容器应用程序还是扩展：

   * `a.RunMode = Application`

      此值表示点击来自容器应用程序。
   * `a.RunMode = Extension`

      此值表示点击来自扩展。

* 如果您从早期版本的 SDK 升级，则在容器应用程序启动后，Adobe 会自动将容器应用程序文件夹中的所有用户默认设置和缓存文件迁移到应用程序组的共享文件夹。
* 如果容器应用程序从未启动过，则会丢弃扩展中的点击量。
* 您的容器应用程序和扩展应用程序的版本号和内部版本号必须相同。
* 在 iOS 扩展应用程序中不会触发生命周期调用。

