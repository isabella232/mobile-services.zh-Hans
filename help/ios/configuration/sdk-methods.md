---
description: 以下是 iOS 库提供的方法列表。
seo-description: 以下是 iOS 库提供的方法列表。
seo-title: 配置方法
solution: Experience Cloud,Analytics
title: 配置方法
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 100%

---

# 配置方法 {#configuration-methods}

以下是 iOS 库提供的方法列表。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。

* **setAppExtensionType**

   配置 Adobe Mobile SDK 设置，以确定当前正在执行的扩展类型。

   设置为以下值之一：
   * `ADBMobileAppExtensionTypeRegular` - 扩展与容器应用程序捆绑在一起.
   * `ADBMobileAppExtensionTypeStandAlone` - 扩展未与容器应用程序捆绑在一起.

   >[!TIP]
   >
   >**仅**&#x200B;当您的应用程序具有扩展或本身是独立扩展时，才应使用此方法。有关更多信息，请参阅下面的“ADBMobileAppExtensionType”**。

   * 以下是此方法的语法：

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   返回 Adobe Mobile 库的当前版本。

   * 以下是此方法的语法：

      ```objective-c
      +(NSString*) version;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。默认值在 `ADBMobileConfig.json` 文件中设置。

   * 以下是此方法的语法：

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。

   设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的语法：

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   返回当前用户的生命周期值。默认值为 `0`。

   * 以下是此方法的语法：

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   返回自动生成的访客标识符。这是由 Adobe 服务器生成的特定于应用程序的唯一访客 ID。如果生成期间无法访问 Adobe 服务器，则使用 Apple 的 CFUUID 来生成访客 ID。这个值是在初始启动时生成的，并从那时起被保存和使用。访客 ID 在应用程序升级期间被保留下来，在标准应用程序备份过程中被保存并恢复，又在卸载应用程序时被删除。

   >[!TIP]
   >
   >如果您的应用程序从 Experience Cloud 3.x SDK 升级到 4.x SDK，则会检索之前的自定义访客 ID 或自动生成的访客 ID，并将其存储为自定义用户标识符。有关更多信息，请参阅下面的 `userIdentifier` 行。这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符为 `nil`，并且将使用跟踪标识符。

   * 以下是此方法的语法：

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   如果已设置自定义标识符，则会返回用户标识符。如果未设置自定义标识符，则会返回 `nil`。默认值为 `nil`。

   >[!TIP]
   >
   >如果您的应用程序从 Experience Cloud 3.x SDK 升级到 4.x SDK，则会检索之前的自定义访客 ID 或自动生成的访客 ID，并将其存储为自定义用户标识符。这样可在 SDK 升级期间保留访客数据。

   对于 4.x SDK 上的新安装，用户标识符在设置之前为 `nil`。

   * 以下是此方法的语法：

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 以下是此方法的语法：

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   返回当前的调试日志记录首选项。默认值为 `NO`。

   * 以下是此方法的语法：

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   将调试日志记录首选项设置为 `debug`。

   * 以下是此方法的语法：

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   指示 SDK 无论配置文件中的生命周期会话超时值为多少，下次从后台恢复时都不应启动新会话。

   >[!TIP]
   >
   >此方法专门用于在后台注册通知的应用程序，而且只应从应用程序处于后台时运行的代码中调用。

   * 以下是此方法的语法：

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   >[!TIP]
   >
   >首选在 `application:didFinishLaunchingWithOptions:` 中调用此方法。

   * 以下是此方法的语法：

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   允许您在收集生命周期量度时传入其他数据。

   必须从应用程序的入口点调用此方法。在适用的情况下，这可能包括 AppDelegate 类中的以下一种或两种方法：`application:didFinishLaunchingWithOptions:` 和/或 `applicationWillEnterForeground:`。

   >[!IMPORTANT]
   >
   >通过 `collectLifecycleDataWithAdditionalData:` 传递到 SDK 的数据将由 SDK 持久保留在 `NSUserDefaults` 中。SDK 将删除 `NSDictionary` 参数中类型不为 `NSString` 或 `NSNumber` 的值。要使用 `collectLifecycleDataWithAdditionalData:`，您必须具有 SDK **版本 4.4** 或更高版本。

   * 以下是此方法的语法：

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   使用此 API 可暂停收集生命周期数据。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   >[!IMPORTANT]
   >
   >在 `applicationDidEnterBackground` 委托方法中，必须首先调用 `pauseCollectingLifecycleData` 方法。
   >
   >提供的 API 可用于缓解装有 iOS 13 的 iPhone7/7s 或较旧设备上会话长度度量出现异常的问题。这是由 iOS 13 中发生了一些未知更改所致，在这些更改中，iOS 没有为置于后台的应用程序留出足够的时间来完成后台任务。

   * 以下是此方法的语法：

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   让您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。在应用程序关闭之前，将一直使用该配置。

   >[!IMPORTANT]
   >
   >要使用 `overrideConfigPath`，您必须具有 SDK 版本 4.2 或更高版本。

   * 以下是此方法的语法：

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   设置推送通知的设备令牌。

   >[!IMPORTANT]
   >
   >应当只在 `application:didRegisterForRemoteNotificationsWithDeviceToken:` 方法中使用此方法。

   * 以下是此方法的语法：

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   在 SDK 中设置 IDFA。如果已在 SDK 中设置 IDFA，则将在生命周期内发送 IDFA。也可以在信号（回发）中访问 IDFA。

   >[!TIP]
   >
   >**仅**&#x200B;当使用广告服务时，才应从 Apple API 检索 IDFA。如果您检索 IDFA 但并未正确使用它，则您的应用程序可能会被拒绝。
   >
   >如果应用程序需要 IDFA，请查阅 [Apple 的文档](https://developer.apple.com/documentation/adsupport)，查询用户的广告跟踪偏好和检索 IDFA 值。
   >
   >对于 iOS 14+，需要实施新的[应用程序跟踪透明度框架](https://developer.apple.com/documentation/apptrackingtransparency)才能够成功检索 IDFA 值。
   * 以下是此方法的语法：

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```
