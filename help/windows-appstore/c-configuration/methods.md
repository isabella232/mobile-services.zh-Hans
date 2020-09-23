---
description: Windows 8.1 Universal App Store库提供的类和方法。
seo-description: Windows 8.1 Universal App Store库提供的类和方法。
seo-title: SDK方法
solution: Experience Cloud,Analytics
title: SDK方法
topic: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 49%

---


# SDK方法 {#sdk-methods}

Windows 8.1 Universal App Store库提供的类和方法。

>[!TIP]
>
>当您使用 `winmd` winJS(JavaScript)中的方法时，所有方法都自动将其第一个字母小写。

* **GetVersion(winJS:getVersion)**

   返回 Adobe Mobile 库的当前版本。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` -如果报表包启用时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * 以下是此方法的语法：

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

   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` -如果报表包启用时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的语法：

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是此方法的代码示例：

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

   返回当前用户的生命周期值。默认值为0。

   * 以下是此方法的语法：

      ```csharp
      static float GetLifetimeValue();
      ```

   * 以下是此方法的代码示例：

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier(winJS:getUserIdentifier)**

   如果已设置自定义标识符，则返回自定义用户标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`。

   >[!TIP]
   >
   >如果您的应用程序从Experience Cloud3.x升级到4.x SDK，则将检索之前的ID（自定义或自动生成）并将其存储为自定义用户标识符。 这样可在 SDK 升级期间保留访客数据。For new installations on the 4.x SDK, user identifier is `null` until set.

   * 以下是此方法的语法：

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier(winJS:setUserIdentifier)**

   将用户标识符设置为 `identifier`。

   * 以下是此方法的语法：

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging(winJS:getDebugLogging)**

   返回当前的调试日志记录首选项。默认值为 `false`。

   * 以下是此方法的语法：

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging(winJS:setDebugLogging)**

   将调试日志记录首选项设置为 `debugLogging`。仅当使用库的调试版本时，调试日志记录才起作用，发行版忽略此设置。

   * 以下是此方法的语法：

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData(winJS:collectLifecycleData)**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >在应用程序内 `onResume()` 的每个活动中调用此方法，如以下示例所示。 我们还建议将活动或服务作为上下文对象而不是全局应用程序上下文进行传递。

   * 以下是此方法的语法：

      ```csharp
      static void CollectLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **暂停收&#x200B;集生命周期数据(winJS:暂停收集&#x200B;生命周期数据)**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，在暂停时会收集时间戳以确定上一个会话长度。 这还会设置一个标志，使生命周期能够正确地知道应用程序未崩溃。 有关更多信息，请参阅[生命周期量度](/help/windows-appstore/metrics.md)。

   >[!TIP]
   >
   >在应用程序内 `onPause()` 每个活动中的方法中调用此方法，如示例所示。 我们还建议将活动或服务作为上下文对象而不是全局应用程序上下文进行传递。

   * 以下是此方法的语法：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
