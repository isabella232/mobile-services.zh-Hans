---
description: 从 WatchOS 2 开始，WatchKit 扩展将在 Apple Watch 设备上运行。在此环境中运行的应用程序需要具备 WatchConnectivity 框架才能与它们的 iOS 容器应用程序共享数据。
seo-description: 从 WatchOS 2 开始，WatchKit 扩展将在 Apple Watch 设备上运行。在此环境中运行的应用程序需要具备 WatchConnectivity 框架才能与它们的 iOS 容器应用程序共享数据。
seo-title: 使用 WatchOS 2 实施 Apple Watch
solution: Experience Cloud,Analytics
title: 使用 WatchOS 2 实施 Apple Watch
topic: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '542'
ht-degree: 100%

---


# 使用 WatchOS 2 实施 Apple Watch{#apple-watch-implementation-with-watchos}

从 WatchOS 2 开始，WatchKit 扩展可在 Apple Watch 上运行。在此环境中运行的应用程序需要 `WatchConnectivity` 框架才能与它们的 iOS 容器应用程序共享数据。

>[!TIP]
>
>从 `AdobeMobileLibrary` v4.6.0 开始，支持 `WatchConnectivity`。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## 入门指南 {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>确保您的项目至少具有以下目标：
>
>* 容器应用程序
>* WatchKit 应用程序
>* WatchKit 扩展

>



有关开发 WatchKit 应用程序的更多信息，请参阅 [Watch 应用程序架构](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)。

## 配置容器应用程序 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

在您的 Xcode 项目中完成以下步骤：

1. 将 `AdobeMobileLibrary` 文件夹拖动到您的项目中。
1. 确保 `ADBMobileConfig.json` 文件是容器应用程序目标的成员。
1. 在容器应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 在实现 `UIApplicationDelegate` 协议的类中，添加 `WCSessionDelegate` 协议。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. 在应用程序委托类的实现文件中，导入 `AdobeMobileLibrary`。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. 在对 `ADBMobile` 库进行调用之前，在应用程序委托的 `application:didFinishLaunchingWithOptions:` 中配置 `WCSession`。

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. 在应用程序委托中，实现 `session:didReceiveMessage:` 和 `session:didReceiveUserInfo:` 方法。

   将在 `ADBMobile` 库中调用 `syncSettings:`，它将返回一个布尔值，指示词典是否可供 `ADBMobile` 库使用。如果返回 `No`，则不会从 Adobe SDK 发起消息。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 配置 WatchKit 扩展 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. 确保 `ADBMobileConfig.json` 文件是 WatchKit 扩展目标的成员。
1. 在 WatchKit 扩展目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. 在实现 `WKExtensionDelegate` 协议的类中，导入 `WatchConnectivity` 并添加 `WCSessionDelegate` 协议。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. 在扩展委托类的实现文件中，导入 `AdobeMobileLibrary`。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. 在对 `ADBMobile` 库进行任何调用之前，在扩展委托的 `applicationDidFinishLaunching` 中配置 `WCSession`。

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. 在扩展委托的 `applicationDidFinishLaunching` 中，为 SDK 初始化 Watch 应用程序。

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. 在扩展委托中，实现 `session:didReceiveMessage:` 和 `session:didReceiveUserInfo:` 方法。

   将在 `ADBMobile` 库中调用 `syncSettings:`，它将返回一个布尔值，指示词典是否可供 `ADBMobile` 库使用。如果返回 `NO`，则不会从 Adobe SDK 发起消息。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 其他信息 {#section_7BCDB5CF0D424DCA97883753D1881233}

请牢记以下信息：

* 对于 WatchKit 应用程序，`a.RunMode` 将设置为 `Extension`。
* 由于 WatchKit 应用程序在 Watch 上运行，因此应用程序将在 `a.AppID` 中正确报告它们的名称。
* 在 WatchOS2 应用程序中不会触发生命周期调用。

