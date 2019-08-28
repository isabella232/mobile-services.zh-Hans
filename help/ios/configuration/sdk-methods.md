---
description: 以下是 iOS 库提供的方法列表。
seo-description: 以下是 iOS 库提供的方法列表。
seo-title: 配置方法
solution: Marketing Cloud，Analytics
title: 配置方法
topic: 开发人员和实施
uuid: 623c7b07-fbb3-4d39-a5 c4-e64 faec4 ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

以下是 iOS 库提供的方法列表。

SDK目前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。

* **setAppExtensionType**

   配置 Adobe Mobile SDK 设置以确定当前正在执行的扩展类型。

   设置为以下值之一：
   * `ADBMobileAppExtensionTypeRegular` - 扩展与容器应用程序捆绑在一起.
   * `ADBMobileAppExtensionTypeStandAlone` - 扩展未与容器应用程序捆绑在一起.
   >[!TIP]
   >
   >**仅** 当应用程序具有扩展或为独立扩展时，才应使用此方法。For more information, see *ADBMobileAppExtensionType* below.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **版本**

   返回 Adobe Mobile 库的当前版本。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(NSString*) version;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` - 点击会立即发送。
   * `ADBMobilePrivacyStatusOptOut` - 点击将被丢弃。
   * `ADBMobilePrivacyStatusUnknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。默认值在 `ADBMobileConfig.json` 文件中设置。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。

   设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn` - 点击会立即发送。
   * `ADBMobilePrivacyStatusOptOut` - 点击将被丢弃。
   * `ADBMobilePrivacyStatusUnknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   返回当前用户的生命周期值。默认值为 `0`.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   返回自动生成的访客标识符。这是由 Adobe 服务器生成的特定于应用程序的独特访客 ID。如果在生成时无法访问 Adobe 服务器，则会使用 Apple 的 CFUUID 生成该 ID。该值在首次启动时生成，之后会存储并使用该值。在应用程序升级期间，会保留该 ID；在标准应用程序备份过程中，会保存并恢复该 ID；而在应用程序卸载时，则会删除该 ID。

   >[!TIP]
   >
   >如果您的应用程序升级从Experience Cloud3.x升级到4.x SDK，则会检索先前的自定义或自动生成的访客ID，并将其作为自定义用户标识符存储。有关更多信息，请参阅下面的 `userIdentifier` 行。这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符为 `nil`，并且将使用跟踪标识符。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   如果已设置自定义标识符，则会返回用户标识符。如果未设置自定义标识符，则会返回 `nil`。默认值为 `nil`.

   >[!TIP]
   >
   >如果您的应用程序升级从Experience Cloud3.x到4.x SDK，则会检索先前的自定义或自动生成的访客ID，并将其作为自定义用户标识符存储。这样可在 SDK 升级期间保留访客数据。

   对于 4.x SDK 上的新安装，用户标识符在设置之前为 `nil`。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   返回当前的调试日志记录首选项。默认值为 `NO`.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   将调试日志记录首选项设置为 `debug`。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   指示 SDK 无论配置文件中的生命周期会话超时值为多少，下次从后台恢复时都不应启动新会话。

   >[!TIP]
   >
   >此方法适用于在后台注册通知的应用程序，并且只应从运行应用程序时运行的代码调用。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   >[!TIP]
   >
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   允许您在收集生命周期量度时传入其他数据。

   必须从应用程序的入口点调用此方法。Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. SDK 将删除 `NSDictionary` 参数中类型不为 `NSString` 或 `NSNumber` 的值。To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   允许您在应用程序启动时加载其他 ADBMobile JSON 配置文件。在应用程序关闭之前，将一直使用该配置。

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

   * 下面是这种方法对应的语法：

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   设置推送通知的设备令牌。

   >[!IMPORTANT]
   >
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   在 SDK 中设置 IDFA。如果已在 SDK 中设置 IDFA，则将在生命周期中发送 IDFA。此外，也可以在信号（回发）中访问 IDFA。

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. 如果您检索 IDFA 但并未正确使用它，则您的应用程序可能会被拒绝。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
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

