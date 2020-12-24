---
description: 此信息可帮助您实施 iOS 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
seo-description: 此信息可帮助您实施 iOS 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
seo-title: 核心实施和生命周期
solution: Experience Cloud,Analytics
title: 核心实施和生命周期
topic: Developer and implementation
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: ht
source-git-commit: c7400359bc19150926a67b991ba219a7fa187442
workflow-type: ht
source-wordcount: '861'
ht-degree: 100%

---


# 核心实施和生命周期 {#core-implementation-and-lifecycle}

此信息可帮助您实施 iOS 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。

## 下载 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>SDK 需要 iOS 8 或更高版本。

**先决条件**

在下载 SDK 之前，请先完成[核心实施和生命周期](/help/ios/getting-started/requirements.md)的“创建报表包”**&#x200B;中的步骤，以设置一个开发报表包并下载预填充版本的配置文件。

要下载 SDK，请执行以下操作：

>[!IMPORTANT]
>
>从版本 4.21.0 开始，SDK 通过 XCFramework 进行分发。如果使用 4.21.0 或更高版本，请按照以下步骤操作。
>
>SDK 版本 4.21.0 需要 Xcode 12.0 或更高版本以及（如果适用）Cocoapods 1.10.0 或更高版本。

1. 下载并解压缩 `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` 文件，同时确认 `AdobeMobileLibrary` 目录中具有以下软件组件：

   * `ADBMobile.h` - 用于 iOS SDK 的 Objective-C 头文件。
   * `ADBMobileConfig.json` - 为您的应用程序自定义的 SDK 配置文件。
   * `AdobeMobile.xcframework` - 包含两个胖二进制文件，分别用于 iOS 设备（armv7、armv7s、arm64）和模拟器（i386、x86_64、arm64）。

      定位 iOS 应用程序时应链接此 XCFramework。

   * `AdobeMobileExtension.xcframework` - 包含两个胖二进制文件，分别用于 iOS 设备（armv7、armv7s、arm64）和模拟器（i386、x86_64、arm64）。

      定位 iOS 扩展时应链接此 XCFramework。

   * `AdobeMobileWatch.xcframework` - 包含两个胖二进制文件，分别用于 watchOS 设备（arm64_32、armv7k）和模拟器（i386、x86_64、arm64）。

      定位 Apple Watch (watchOS) 应用程序时应链接此 XCFramework。

   * `AdobeMobileTV.xcframework` - 包含两个胖二进制文件，分别用于 tvOS 设备 (arm64) 和模拟器（x86_64、arm64）。

      定位 Apple TV (tvOS) 应用程序时应链接此 XCFramework。

>[!IMPORTANT]
>
>在低于 4.21.0 的版本中，SDK 通过二进制文件进行分发。如果使用的版本低于 4.21.0，请按照以下步骤操作。

1. 下载并解压缩 `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` 文件，同时确认具有以下软件组件：

   * `ADBMobile.h`，用于 iOS AppMeasurement 的 Objective-C 头文件。
   * `ADBMobileConfig.json`，为您的应用程序自定义的 SDK 配置文件。
   * `AdobeMobileLibrary.a`，启用 bitcode 的胖二进制文件，其中包含为 iOS 设备（armv7、armv7s、arm64）和模拟器（i386、x86_64）生成的库。

      当目标面向 iOS 应用程序时，应该关联此胖二进制文件。

   * `AdobeMobileLibrary_Extension.a`，启用 bitcode 的胖二进制文件，其中包含为 iOS 设备（armv7、armv7s、arm64）和模拟器（i386、x86_64）生成的库。

      当目标面向 iOS 扩展时，应该关联此胖二进制文件。

   * `AdobeMobileLibrary_Watch.a`，启用 bitcode 的胖二进制文件，其中包含为 Apple Watch 设备 (armv7k) 和模拟器（i386、x86_64）生成的库。

      当目标面向 Apple Watch (watchOS 2) 扩展应用程序时，应该关联此胖二进制文件。

   * `AdobeMobileLibrary_TV.a`，启用 bitcode 的胖二进制文件，其中包含为新 Apple TV 设备 (arm64) 和模拟器 (x86_64) 生成的库。

      当目标面向 Apple TV (tvOS) 应用程序时，应该关联此胖二进制文件。

>[!IMPORTANT]
>
>如果您在 Adobe Mobile Services 用户界面之外下载 SDK，则必须手动配置 `ADBMobileConfig.json` 文件。如果您是初次使用 Analytics 和 Mobile SDK，请参阅[开始之前](/help/ios/getting-started/requirements.md)以设置一个开发报表包并下载预填充版本的配置文件。

## 将 SDK 和配置文件添加到您的项目 {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动 Xcode IDE 并打开您的应用程序。
1. 在项目导航器中，将 `AdobeMobileLibrary` 文件夹拖放到您的项目下。
1. 确认以下内容：

   * 已选中&#x200B;**[!UICONTROL 根据需要复制项目]**&#x200B;复选框。
   * 已选中&#x200B;**[!UICONTROL 创建群组]**。
   * 未选中&#x200B;**[!UICONTROL 添加到目标]**&#x200B;部分中的任何复选框。

   ![](assets/step_3.png)

1. 单击&#x200B;**[!UICONTROL 完成]**。
1. 在&#x200B;**[!UICONTROL 项目导航器]**&#x200B;中，选择 **`ADBMobileConfig.json`**。
1. 在&#x200B;**[!UICONTROL 文件检查器]**&#x200B;中，将该 JSON 文件添加到您的项目中将使用 Adobe SDK 的任何目标。

   ![](assets/step_4.png)

1. 在&#x200B;**[!UICONTROL 项目导航器]**&#x200B;中，完成以下步骤：

   1. 单击您的应用程序。
   1. 在&#x200B;**[!UICONTROL 常规]**&#x200B;选项卡上，选择您的目标并关联&#x200B;**[!UICONTROL 关联的框架]**&#x200B;和&#x200B;**[!UICONTROL 库]**&#x200B;部分中的所需框架和库。
   * **iOS 应用程序目标**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
      * `CoreLocation.framework`（可选，但是对于“地理跟踪”功能是必需的）
   * **iOS 扩展目标**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch (watchOS 2) 目标**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV (tvOS) 目标**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`

   >[!CAUTION]
   >
   > 在同一目标中关联多个 `AdobeMobileLibrary*.a` 文件将导致意外行为或无法执行生成操作。

   >[!IMPORTANT]
   >
   > 如果使用版本 4.21.0 或更高版本，请确保未嵌入 Adobe XCFramework。

   ![](assets/no-embed.png)

1. 确认您的应用程序在生成时没有出现错误。

## 实施生命周期量度 {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>无论是否调用 `collectlifecycledata`，iOS 都将发送生命周期信息；`collectlifecycledata` 是在应用程序启动序列中提前启动生命周期的唯一方法。

启用生命周期后，每次启动您的应用程序时，系统都会发送一个点击来测量启动次数、升级次数、会话数、参与用户数及其他[生命周期量度](/help/ios/metrics.md)。

在 `application:didFinishLaunchingWithOptions` 中添加一个 `collectLifecycleData`/`collectLifecycleDataWithAdditionalData` 调用：

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
 [ADBMobile collectLifecycleData];
    return YES;
}
```

### 通过生命周期调用包含其他数据

要通过生命周期量度调用包含其他数据，请使用 `collectLifecycleDataWithAdditionalData`：

>[!IMPORTANT]
>
>通过 `collectLifecycleDataWithAdditionalData:` 传递到 SDK 的任何数据将由 SDK 保留在 `NSUserDefaults` 中。SDK 会删除 `NSDictionary` 参数中类型不为 `NSString` 或 `NSNumber` 的值。

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary];
    [contextData setObject:@"Game" forKey:@"myapp.category"];
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData];
    return YES;
}
```

通过 `collectLifecycleDataWithAdditionalData` 发送的其他上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-lifecycle.png)

其他生命周期量度将会自动收集。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

## 后续操作 {#section_A24DC703359D4B5C8F493D6421306FD3}

完成以下任务：

* [跟踪应用程序状态](/help/ios/analytics-main/states.md)
* [跟踪应用程序操作](/help/ios/analytics-main/actions.md)
