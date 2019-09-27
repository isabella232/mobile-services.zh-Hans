---
description: Windows 8.1 通用应用商店库提供的类和方法。
seo-description: Windows 8.1 通用应用商店库提供的类和方法。
seo-title: SDK方法
solution: Marketing Cloud,Analytics
title: SDK方法
topic: 开发人员和实施
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Windows 8.1 通用应用商店库提供的类和方法。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion (winJS: getVersion)**

   返回 Adobe Mobile 库的当前版本。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` -立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` -丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * 以下是此方法的代码示例：

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus(winJS:setPrivacyStatus)**

   将当前用户的隐私状态设置为 `status`。设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn` -立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` -丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 下面是这种方法对应的语法：

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是这种方法的代码示例：

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue(winJS:getLifetimeValue)**

   返回当前用户的生命周期值。默认值为 0。

   * 下面是这种方法对应的语法：

      ```csharp
      static float GetLifetimeValue();
      ```

   * 以下是这种方法的代码示例：

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier(winJS:getUserIdentifier)**

   如果设置了自定义标识符，则返回自定义用户标识符。如果未设置自定义标识符，则返回 null。默认值为 `null`.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous ID (either custom or automatically generated) is retrieved and stored as the custom user identifier. 这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符在设置之前为 `null`。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier(winJS:setUserIdentifier)**

   将用户标识符设置为 `identifier`。

   * 下面是这种方法对应的语法：

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging(winJS:getDebugLogging)**

   返回当前的调试日志记录首选项。默认值为 `false`.

   * 下面是这种方法对应的语法：

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging(winJS:setDebugLogging)**

   将调试日志记录首选项设置为 `debugLogging`。调试日志记录功能仅在使用库的调试版本时才可用，发行版本将忽略此设置。

   * 下面是这种方法对应的语法：

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData(winJS:collectLifecycleData)**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. 我们还建议将 Activity 或 Service 作为上下文对象（而非全局应用程序上下文）传递。

   * 下面是这种方法对应的语法：

      ```csharp
      static void CollectLifecycleData();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **暂停收&#x200B;集生命周期数据(winJS:pauseCollecting &#x200B; LifecycleData)**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，暂停时收集时间戳以确定上一个会话时长。此方法还会设置一个标记，以便生命周期准确知道应用程序并没有崩溃。有关更多信息，请参阅[生命周期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. 我们还建议将 Activity 或 Service 作为上下文对象（而非全局应用程序上下文）传递。

   * 下面是这种方法对应的语法：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
