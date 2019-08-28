---
description: 由通用 Windows 平台库提供的类和方法。
seo-description: 由通用 Windows 平台库提供的类和方法。
seo-title: SDK方法
solution: Marketing Cloud，Analytics
title: SDK方法
topic: 开发人员和实施
uuid: e3aa41d6-7bc0-4208-a662-12907c209 a77 a77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

由通用 Windows 平台库提供的类和方法。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **getVersion(WinJS：getVersion)**

   返回 Adobe Mobile 库的当前版本。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **getPrivacyStatusAsync(WinJS：getPrivacyStatusAsync)**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` - 点击将立即发送。
   * `ADBMobilePrivacyStatusOptOut` - 点击将被丢弃。
   * `ADBMobilePrivacyStatusUnknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      The default value is set in the `ADBMobileConfig.json` config file. 有关详细信息，请参阅 [AdbMobileConfig. json配置文件](/help/universal-windows/c-configuration/c.json.md)。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * 以下是此方法的代码示例：

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **setPrivacyStatus(WinJS：setPrivacyStatus)**

   将当前用户的隐私状态设置为 `status`。设置为以下值之一：
   * `ADBMobilePrivacyStatusOptIn` - 点击会立即发送。
   * `ADBMobilePrivacyStatusOptOut` - 点击将被丢弃。
   * `DBMobilePrivacyStatusUnknown` - 如果报表包启用了时间戳，则会保存点击，直到隐私状态更改变为加入(点击)或退出(点击被丢弃)。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      * 下面是这种方法对应的语法：

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * 以下是此方法的代码示例：

         **C-sharp**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **getLifeTimeValue(WinJS：getLifeTimeValue)**

   返回当前用户的生命周期值。默认值为 `0`.

   * 下面是这种方法对应的语法：

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **getUserIdentifier(WinJS：getUserIdentifier)**

   如果设置了自定义标识符，则返回自定义用户标识符。Returns `null` if a custom identifier is not set.
默认值为 `null`.

   >[!IMPORTANT]
   >
   >如果您的应用程序升级从Experience Cloud3.x到4.x SDK，则将检索之前的ID服务(自定义或自动生成)作为自定义用户标识符。这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符在设置之前为 `null`。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * 以下是这种方法的代码示例：

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **setUserIdentifier(WinJS：setUserIdentifier)**

   将用户标识符设置为 `identifier`。

   * 下面是这种方法对应的语法：

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * 以下是这种方法的代码示例：

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **getDebglogging(WinJS：getDebglogging)**

   返回当前的调试日志记录首选项。默认值为 `false`.

   * 下面是这种方法对应的语法：

      ```csharp
      static bool GetDebugLogging();
      ```

   * 以下是这种方法的代码示例：

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **setDebglogging(WinJS：setDebglogging)**

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

* **CollectLiveCycleData(WinJS：CollectLifecyCleData)**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期指标](/help/universal-windows/metrics.md)。

   * 下面是这种方法对应的语法：

      ```csharp
      static void CollectLifecycleData();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollectingLifecyCleData(WinJS：PauseCollectingLifecyCleData)**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，暂停时收集时间戳以确定上一个会话时长。此方法还会设置一个标记，以便生命周期准确知道应用程序并没有崩溃。有关更多信息，请参阅[生命周期量度](/help/universal-windows/metrics.md)。

   * 下面是这种方法对应的语法：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
