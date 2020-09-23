---
description: 通用Windows平台库提供的类和方法。
seo-description: 通用Windows平台库提供的类和方法。
seo-title: SDK方法
solution: Experience Cloud,Analytics
title: SDK方法
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 61%

---


# SDK方法 {#sdk-methods}

通用Windows平台库提供的类和方法。

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
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync(winJS:getPrivacyStatusAsync)**

   返回当前用户隐私状态的枚举表示形式。

   * `ADBMobilePrivacyStatusOptIn` -立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` -丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      The default value is set in the `ADBMobileConfig.json` config file. 有关详细信息，请 [参阅ADBMobileConfig.json配置文件](/help/universal-windows/c-configuration/c.json.md)。

   * 以下是此方法的语法：

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

* **SetPrivacyStatus(winJS:setPrivacyStatus)**

   将当前用户的隐私状态设置为 `status`。设置为以下值之一：
   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `DBMobilePrivacyStatusUnknown` -如果您的报表包启用了时间戳，则会保存点击，直到隐私状态更改为选择加入（发送点击）或选择退出（丢弃点击）为止。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      * 以下是此方法的语法：

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

* **GetLifetimeValue(winJS:getLifetimeValue)**

   返回当前用户的生命周期值。默认值为 `0`。

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

   如果已设置自定义标识符，则返回自定义用户标识符。 Returns `null` if a custom identifier is not set.
默认值为 `null`。

   >[!IMPORTANT]
   >
   >如果您的应用程序从Experience Cloud3.x升级到4.x SDK，将检索之前的ID服务（自定义或自动生成）并将其存储为自定义用户标识符。 这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符在设置之前为 `null`。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * 以下是此方法的代码示例：

      ```csharp
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

      ```javascript
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

      ```javascript
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

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/universal-windows/metrics.md)。

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

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，在暂停时会收集时间戳以确定上一个会话长度。 这还会设置一个标志，使生命周期能够正确地知道应用程序未崩溃。 有关更多信息，请参阅[生命周期量度](/help/universal-windows/metrics.md)。

   * 以下是此方法的语法：

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
