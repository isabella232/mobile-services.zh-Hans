---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs方法
solution: Experience Cloud
title: ADBMobile.cs方法
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 66%

---


# ADBMobile.cs方法 {#adbmobile-cs-methods}

## 配置方法

* **CollectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void CollectLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications（仅限iOS）**

   在应用程序中启用本地通知。

   * 以下是此方法的语法：

      ```java
      public static void EnableLocalNotifications();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   返回当前的调试日志记录首选项。默认值为 `false`。

   * 以下是此方法的语法：

      ```java
      public static bool GetDebugLogging();
      ```

   * 以下是此方法的代码示例：

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   返回当前用户的生命周期值。

   * 以下是此方法的语法：

      ```java
      public static double GetLifetimeValue();
      ```

   * 以下是此方法的代码示例：

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。
   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即发送点击。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：丢弃点击。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果启用了脱机跟踪，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。

      如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) file.

   * 以下是此方法的语法：

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * 以下是此方法的代码示例：

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   如果已设置自定义标识符，则返回自定义用户标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`。

   * 以下是此方法的语法：

      ```java
      public static string GetUserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```java
      var userId = ADBMobile.GetUserIdentifier();
      ```

* **GetVersion**

   获取库版本。

   * 以下是此方法的语法：

      ```java
      public static string GetVersion();
      ```

   * 以下是此方法的代码示例：

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive（仅限iOS）**

   指示 SDK 无论配置文件中的生命周期会话超时值为多少，下次从后台恢复时都不应启动新会话。

   >[!TIP]
   >
   >此方法适用于在后台注册通知的应用程序，并且只应从应用程序在后台运行时运行的代码中调用。

   * 以下是此方法的语法：

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData（仅限Android）**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，在暂停时会收集时间戳以确定上一个会话长度。 这还会设置一个标志，使生命周期能够正确地知道应用程序未崩溃。 有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext（仅限Android）**

   向SDK指示它应根据UnityPlayer的当前活动设置其应用程序上下文。

   * 以下是此方法的语法：

      ```java
      public static void SetContext();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   将调试日志记录首选项设置为启用。

   * 以下是此方法的语法：

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   将当前用户的隐私状态设置为状态。 设置为以下值之一：

   * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即发送点击。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`：丢弃点击。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`:如果启用了脱机跟踪，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的语法：

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * 以下是此语法的代码示例：

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   将用户标识符设置为userId。

   * 以下是此方法的语法：

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Analytics 方法

* **GetTrackingIdentifier**

   检索分析跟踪标识符。

   * 以下是此方法的语法：

      ```java
      public static string GetTrackingIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中可用的视图，如“标题屏幕”、“级别1”、“暂停”等。 这些状态与网站中的页面类似，而且 `TrackState` 调用会使页面查看次数递增。

   如果状态为空，则状态将显示 *`app name app version (build)`* 为报告。 If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      var contextData = new Dictionary<string, object>);
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   跟踪您的应用程序中的操作。操作是您要衡量的应用程序中发生的事情，如“死亡”、“获得的级别”、“供给订阅”和其他指标。

   >[!TIP]
   >
   >如果您的代码可能会在应用程序位于后台时运行（例如，后台数据检索），请改用 `trackActionFromBackground`。

   * 以下是此方法的语法：

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground（仅限iOS）**

   跟踪在后台发生的操作。在某些情况下，这会阻止触发生命周期事件。

   >[!TIP]
   >
   >仅应当在应用程序处于后台时运行的代码中调用此方法。

   * 以下是此方法的语法：

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   发送当前纬度和经度坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标在定义的POI中，则填充上下文数据变量，并随TrackLocation调用发送。

   * 以下是此方法的语法：

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null);
      ```

* **TrackBeacon**

   跟踪用户接近信标的时间。

   * 以下是此方法的语法：

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata);
      ```

* **TrackingClearCurrentBeacon**

   在用户远离信标后清除信标数据。

   * 以下是此方法的语法：

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   增加用户终身价值。

   * 以下是此方法的语法：

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   开始具有指定操作名称的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   传入数据以更新与给定操作关联的上下文数据。 传入的数据将附加到给定操作的现有数据中，并覆盖数据（如果已为操作定义相同的密钥）。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata);
      ```

   * 以下是此方法的代码示例：

      ```java
      var contextData = new Dictionary<string, object>;
      contextData.Add("checkpoint", "1:32");
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   结束定时操作。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 以下是此方法的语法：

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * 以下是此方法的代码示例：

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   强制库发送离线队列中的所有点击，而不考虑当前排队的点击量。

   * 以下是此方法的语法：

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackingSendQueuedHits();
      ```

* **TrackingClearQueue**

   清除离线队列中的所有点击。

   * 以下是此方法的语法：

      ```java
      public static void TrackingClearQueue();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   检索离线队列中的当前点击量。

   * 以下是此方法的语法：

      ```java
      public static int TrackingGetQueueSize();
      ```

   * 以下是此方法的代码示例：

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience CloudID方法

* **GetMarketingCloudID**

   从 ID 服务中检索 Experience Cloud ID。

   * 以下是此方法的语法：

      ```java
      public static string GetMarketingCloudID();
      ```

   * 以下是此方法的代码示例：

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   使用Experience CloudID，您可以设置其他客户ID以与每个访客关联。 访客API接受同一访客的多个客户ID以及客户类型标识符，以分隔不同客户ID的范围。 此方法对应于 JavaScript 库中的 setCustomerIDs。

   * 以下是此方法的语法：

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers);
      ```

   * 以下是此方法的代码示例：

      ```java
      var ids = new Dictionary<string, object> ();
      ids.Add ("player1", "jimbob");
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

## 客户获取方法

* **ProcessGooglePlayInstallReferrerUrl** ( *仅限Android)*

   将从调用返回的推荐人URL传递给此方法的Google Play安装推荐人API。

   * 以下是此方法的语法：

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * 以下是此方法的代码示例：

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
