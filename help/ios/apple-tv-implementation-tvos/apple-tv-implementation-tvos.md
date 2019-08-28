---
description: 此信息可帮助您使用 tvOS 实施 Apple TV。
seo-description: 此信息可帮助您使用 tvOS 实施 Apple TV。
seo-title: 使用 tvOS 实施 Apple TV
solution: Marketing Cloud，Analytics
title: 使用 tvOS 实施 Apple TV
topic: 开发人员和实施
uuid: d1571ea2-a5 de-4b96-a527-72abbf51 fab8
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

此信息可帮助您使用 tvOS 实施 Apple TV。

## 新的 Adobe Experience Cloud SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 有关更多信息，请参阅 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)。

通过 Apple TV，您现在能够创建可在本机 tvOS 环境中运行的应用程序。您可以使用 iOS 中的几种框架创建本机应用程序，也可以使用 XML 模板和 JavaScript 创建应用程序。

>[!TIP]
>
>从 `AdobeMobileLibrary` 4.7.0版开始提供TvOS支持。

## 入门指南 {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>我们假定您的项目有一个目标，即面向TvOS的Apple TV应用程序。有关更多信息，请参阅 [tvOS](https://developer.apple.com/tvos/documentation/)。

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

在您的 Xcode 项目中完成以下步骤：

1. 将 AdobeMobileLibrary 文件夹拖动到您的项目中。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. 在 tvOS 应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

有关信息，请参阅 [iOS](https://developer.apple.com/ios/resources/) 上的 iOS 文档。

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. 将 `AdobeMobileLibrary` 文件夹拖动到您的项目中。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. 在 tvOS 应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. 在 `TVApplicationControllerDelegate` 类的实现文件中，导入 SDK。

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Adobe SDK 需要访问应用程序的 `TVApplicationController`，以便在应用程序的 JSContext 中注册自身。此步骤允许您从 JavaScript 文件中调用 Adobe SDK 中的本机方法。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. 在 JavaScript 文件中，使用 `ADBMobile` 对象访问 Adobe SDK 的本机方法。

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

