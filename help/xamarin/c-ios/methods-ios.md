---
description: 适用于Experience Cloud解决方案4.x SDK的Xamarin组件的iOS方法。
keywords: 沙马林
solution: Experience Cloud
title: iOS 方法
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
exl-id: 92897d08-2b66-4688-9870-c877bea53cfc
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 70%

---

# iOS 方法{#ios-methods}

适用于Experience Cloud解决方案4.x SDK的Xamarin组件的iOS方法。

## 配置方法 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   * 以下是此方法的语法：

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   返回当前的调试日志记录首选项。默认值为 `false`。

   * 以下是此方法的语法：

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   将调试日志记录首选项设置为已启用。

   * 以下是此方法的语法：

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   返回当前用户的生命周期值。

   * 以下是此方法的语法：

      ```objective-c
      public static double LifetimeValue();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。
   * `ADBMobilePrivacyStatus.OptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatus.OptOut` - 丢弃点击。
   * ADBMobilePrivacyStatus.Unknown — 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。 如果禁用了离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   默认值在[ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md)中设置。

   * 以下是此方法的语法：

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   将当前用户的隐私状态设置为状态。 设置为以下值之一：
   * `ADBMobilePrivacyStatus.OptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatus.OptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatus.Unknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的语法：

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **用户标识符**

   如果已设置自定义标识符，则返回自定义用户标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`。

   * 以下是此方法的语法：

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   如果已设置自定义标识符，则返回自定义用户标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`。

   * 以下是此方法的语法：

      ```objective-c
      public static string UserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier"); 
      ```

* **GetVersion**

   获取库版本。

   * 以下是此方法的语法：

      ```objective-c
      public static string Version();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive（仅限iOS）**

   指示 SDK 无论配置文件中的生命周期会话超时值为多少，下次从后台恢复时都不应启动新会话。

   >[!TIP]
   >
   >此方法专门用于在后台注册通知的应用程序，并且只应从应用程序处于后台时运行的代码中调用。

   * 以下是此方法的语法：

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics 方法 {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   检索分析跟踪标识符。

   * 以下是此方法的语法：

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中可用的一些视图，例如“标题屏幕”、“级别1”、“暂停”等。 这些状态与网站上的页面类似，并且`TrackState`调用会使页面查看次数递增。如果状态为空，它会在报表中显示为“应用程序名称应用程序版本（内部版本）”。 如果在报表中看到此值，请确保在每个`TrackState`调用中设置状态。

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，例如“死亡”、“获得的级别”、“信息源订阅”及其他量度。

   >[!TIP]
   >
   >如果您的代码可能会在应用程序位于后台时运行（例如，后台数据检索），请改用 `trackActionFromBackground`。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground（仅限iOS）**

   跟踪在后台发生的操作。在某些情况下，这会阻止触发生命周期事件。

   >[!TIP]
   >
   > 仅应当在应用程序处于后台时运行的代码中调用此方法。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   发送当前纬度和经度坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `TrackLocation` 调用发送该变量。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   跟踪用户接近信标的时间。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   在用户远离信标后清除信标数据。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   向用户的生命周期值中添加金额。

   * 以下是此方法的语法：

      public nbsp；静态voidTrackLifetimeValueIncrease(double amount， NSDictionary cdata);

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   开始具有指定操作名称的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   传入数据，以更新与给定操作关联的上下文数据。 传入的数据将附加到给定操作的现有数据中，如果已经为操作定义了相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   结束定时操作。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 以下是此方法的语法：

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   强制库发送离线队列中的所有点击，而不考虑当前排队的点击量。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   清除离线队列中的所有点击。

   * 以下是此方法的语法：

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   检索离线队列中的当前点击量。

   * 以下是此方法的代码示例：

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience CloudID方法 {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   从 ID 服务中检索 Experience Cloud ID。

   * 以下是此方法的语法：

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   使用Experience CloudID，您可以设置其他客户ID以与每个访客关联。 访客API接受同一访客具有多个客户ID，并且还使用客户类型标识符区分不同客户ID的适用范围。 此方法对应于 JavaScript 库中的 setCustomerIDs。

   * 以下是此方法的语法：

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target 方法 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   向您配置的Target服务器发送请求，并返回在`Action<NSDictionary>`回调中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   一个方便使用的构造函数，用于使用给定参数创建`ADBTargetLocationRequest`对象。

   * 以下是此方法的语法：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   创建 `ADBTargetLocationRequest`。

   * 以下是此方法的语法：

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   清除应用程序中的任何目标 Cookie。

   * 以下是此方法的语法：

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回nil。 访客配置文件保存在`NSUserDefaults`中，以便在多次启动应用程序时轻松访问。

   * 以下是此方法的语法：

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   返回当前 DPID。

   * 以下是此方法的语法：

      ```objective-c
      public static string AudienceDpid ();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   返回当前 DPUUID。

   * 以下是此方法的语法：

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   设置dpid和dpuuid。 如果设置了dpid和dpuuid，则它们将随每个信号一起发送。

   * 以下是此方法的语法：

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   向受众管理发送一个具有特征的信号，并获取`Action<NSDictionary>`回调中返回的匹配区段。

   * 以下是此方法的语法：

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   重置 Audience Manager UUID 并清除当前访客资料。

   * 以下是此方法的语法：

      ```objective-c
      public static void AudienceReset ();
      ```

   * 以下是此方法的语法：

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## 视频 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

有关更多信息，请参阅[Video Analytics](/help/ios/getting-started/dev-qs.md)。

* **MediaCreateSettings**

   通过指定的参数返回 `ADBMediaSettings` 对象。

   * 以下是此方法的语法：

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   返回用于跟踪广告视频的 `ADBMediaSettings` 对象。

   * 以下是此方法的语法：

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   打开 `ADBMediaSettings` 对象以进行跟踪。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   关闭名为“name”的媒体项目。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   在给定的“offset”时间（以秒为单位）播放名为“name”的媒体项目。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   在提供的“offset”时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   通知媒体模块已在给定的“offset”时间停止或暂停视频。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
