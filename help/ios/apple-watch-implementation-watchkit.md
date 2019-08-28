---
description: 从 WatchOS 2 开始，WatchKit 扩展可在 Apple Watch 设备上运行。在此环境中运行的应用程序需要 WatchConnectivity 框架才能与它们的 iOS 容器应用程序共享数据。
seo-description: 从 WatchOS 2 开始，WatchKit 扩展可在 Apple Watch 设备上运行。在此环境中运行的应用程序需要 WatchConnectivity 框架才能与它们的 iOS 容器应用程序共享数据。
seo-title: 使用 WatchOS 2 实施 Apple Watch
solution: Marketing Cloud，Analytics
title: 使用 WatchOS 2 实施 Apple Watch
topic: 开发人员和实施
uuid: 9498467e-db5 e-411e-a00 e-d19841 f485 de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

从WatchOS开始，您的WatchKit扩展可以在Apple Watch上运行。Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>支持 `AdobeMobileLibrary` v4.6.0 `WatchConnectivity` 开始。

## 入门指南 {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>确保您具有至少以下目标的项目：
>
>* 容器应用程序
>* WatchKit 应用程序
>* WatchKit 扩展
>



有关开发 WatchKit 应用程序的更多信息，请参阅 [The Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)（Watch 应用程序架构）。

## 配置包含的应用程序 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

在您的 Xcode 项目中完成以下步骤：

1. 将 `AdobeMobileLibrary` 文件夹拖动到您的项目中。
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. 在容器应用程序目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

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

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` 在 `ADBMobile` 库中调用，返回一个布尔值，它指示词典是否用于 `ADBMobile` 库的消耗。如果返回 `No`，则不会从 Adobe SDK 发起消息。

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

## 配置WatchKit扩展 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. 在 WatchKit 扩展目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**将二进制文件与库关联]部分，然后添加以下库：[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. 在扩展委托类的实现文件中，导入 `AdobeMobileLibrary`。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

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

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` 在 `ADBMobile` 库中调用，返回一个布尔值，它指示词典是否用于 `ADBMobile` 库的消耗。如果返回 `NO`，则不会从 Adobe SDK 发起消息。

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

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* 由于 WatchKit 应用程序在 Watch 上运行，因此应用程序将在 `a.AppID` 中正确报告它们的名称。
* 在 WatchOS2 应用程序中不会触发生命周期调用。

