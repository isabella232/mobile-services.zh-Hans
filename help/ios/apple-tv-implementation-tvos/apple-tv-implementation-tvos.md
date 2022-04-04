---
description: 此信息可帮助您使用 tvOS 实施 Apple TV。
solution: Experience Cloud Services,Analytics
title: 使用 tvOS 实施 Apple TV
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# 使用 tvOS 实施 Apple TV {#apple-tv-implementation-with-tvos}

此信息可帮助您使用 tvOS 实施 Apple TV。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 概述

使用 Apple TV，您现在可以创建要在本机 tvOS 环境中运行的应用程序。您可以使用 iOS 中的多个框架来创建本机应用程序，也可以使用 XML 模板和 JavaScript 创建应用程序。

>[!TIP]
>
>从 `AdobeMobileLibrary` 版本 4.7.0 开始，提供了 tvOS 支持。

## 快速入门 {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>我们假定项目的目标为针对 tvOS 的 Apple TV 应用程序。有关更多信息，请参阅 [tvOS](https://developer.apple.com/tvos/documentation/)。

## 配置适用于 tvOS 的本地应用程序 {#section_5095F19B3C4545F68E8C1E37A7E303AE}

在您的 Xcode 项目中完成以下步骤：

1. 将 AdobeMobileLibrary 文件夹拖动到您的项目中。
1. 确保 `ADBMobileConfig.json` 文件是您目标的成员。
1. 在 tvOS 应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

有关信息，请参阅 [iOS](https://developer.apple.com/ios/resources/) 上的 iOS 文档。

## 配置适用于 tvOS 的 TVML/TVJS 应用程序 {#section_AB2EC8C326654F3387658EBBD990BB12}

1. 将 `AdobeMobileLibrary` 文件夹拖动到您的项目中。
1. 确保 `ADBMobileConfig.json` 文件是您目标的成员。
1. 在 tvOS 应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. 在 `TVApplicationControllerDelegate` 类的实现文件中，导入 SDK。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 在 `TVApplicationControllerDelegate` 类的 `application:didFinishLaunchWithOptions:` 方法中，使用 `installTVMLHooks:` 方法将您的 `TVApplicationController` 对象传递到 SDK。

   Adobe SDK 需要访问应用程序的 `TVApplicationController`，以便在应用程序的 JSContext 中注册自身。此步骤允许您从 JavaScript 文件中调用 Adobe SDK 中的本机方法。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. 在 JavaScript 文件中，使用 `ADBMobile` 对象访问 Adobe SDK 的本机方法。

   有关可用方法的完整列表，请参阅 [TVJS 方法](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md)。
