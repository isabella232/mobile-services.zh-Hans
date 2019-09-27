---
description: 适用于 Experience Cloud 解决方案 4.x SDK 的 Xamarin 组件的 Android 方法。
keywords: Xamarin
seo-description: 适用于 Experience Cloud 解决方案 4.x SDK 的 Xamarin 组件的 Android 方法。
seo-title: Android方法
solution: Marketing Cloud，开发人员
title: Android methods
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

适用于 Experience Cloud 解决方案 4.x SDK 的 Xamarin 组件的 Android 方法。

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **调试记录**

   返回当前调试日志记录首选项，默认值为false。

   * 下面是这种方法对应的语法：

      ```java
      public static Boolean DebugLogging;
      ```

   * 以下是这种方法的代码示例：

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   返回当前用户的生命周期值。

   * 下面是这种方法对应的语法：

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * 以下是这种方法的代码示例：

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。
   * `ADBMobilePrivacyStatus.OptIn` -立即发送点击。
   * `ADBMobilePrivacyStatus.OptOut` -丢弃点击。
   * `ADBMobilePrivacyStatus.Unknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。
   默认值在 [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) 文件中设置。

   * 下面是这种方法对应的语法：

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * 以下是这种方法的代码示例：

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   如果已设置自定义标识符，则返回此标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`.

   * 下面是这种方法对应的语法：

      ```java
      public static UserIdentifier();
      ```

   * 以下是这种方法的代码示例：

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **版本**

   获取库版本。

   * 下面是这种方法对应的语法：

      ```java
      public static string Version;
      ```

   * 以下是这种方法的代码示例：

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，暂停时收集时间戳以确定上一个会话时长。此方法还会设置一个标记，以便生命周期准确知道应用程序并没有崩溃。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 下面是这种方法对应的语法：

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity activity)**

   （4.2 或更高版本）指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 下面是这种方法对应的语法：

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity activity)**

   （4.2 或更高版本）指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 下面是这种方法对应的语法：

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * 以下是这种方法的代码示例：

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. 在应用程序关闭之前，将一直使用该配置。

   * 下面是这种方法对应的语法：

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   （4.2或更高版本）设置用于SDK创建的通知的大图标。 此图标是当用户在通知中心看到完整通知时显示的主图像。

   * 下面是这种方法对应的语法：

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 or later) Sets the small icon that is used for notifications created by the SDK. 此图标显示在状态栏中，是用户在通知中心看到完整通知时显示的次映像。

   * 下面是这种方法对应的语法：

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * 以下是这种方法的代码示例：

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   返回自动为 Analytics 生成的 ID。This is an app-specific unique ID that is generated on initial launch and is stored and used from that point forward. This ID is preserved between app upgrades and is removed on uninstall.

   * 下面是这种方法对应的语法：

      ```java
      public static string TrackingIdentifier;
      ```

   * 以下是这种方法的代码示例：

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   通过可选的上下文数据跟踪应用程序状态。`States`是指应用程序中可用的视图，如“标题屏幕”、“级别 1”、“暂停”，等等。这些状态与网站中的页面类似，而且 `TrackState` 调用会使页面查看次数递增。如果状态为空，则在报表中显示为“应用程序名称应用程序版本（内部版本号）”。如果您在报表中看到该值，请确保在每个 `TrackState` 调用中设置 state。

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   跟踪应用程序中的操作。操作是指应用程序中发生的需要测量的事件，如“终止次数”、“获取的级别”、“信息源订阅”及其他量度。

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   发送当前纬度和经度坐标。Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. 如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `TrackLocation` 调用发送该变量。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   跟踪用户接近信标的时间。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   在用户远离信标后清除信标数据。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   向用户的生命周期值中添加数量。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   开始具有指定操作名称的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   > 这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * 下面是此方法的代码示例：

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   传入数据，以更新与给定操作关联的上下文数据。传入的数据会附加在给定操作的现有数据之后，但如果已为操作定义了相同的键值，则会覆盖现有数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   结束定时操作。

   * 下面是这种方法对应的语法：

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 下面是这种方法对应的语法：

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   强制库发送脱机队列中的所有点击，而不管当前排队的点击数。

   * 下面是这种方法对应的语法：

      ```java
      public static void SendQueuedHits();
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   清除离线队列中的所有点击。

   * 下面是这种方法对应的语法：

      ```java
      public static void ClearQueue(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Retrieves the number of hits that are currently in the offline queue.

   * 下面是这种方法对应的语法：

      ```java
      public static long QueueSize(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   从 ID 服务中检索 Experience Cloud ID。

   * 下面是这种方法对应的语法：

      ```java
      public static string MarketingCloudId;
      ```

   * 以下是这种方法的代码示例：

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   使用 Experience Cloud ID，您可以设置其他的客户 ID 以便关联每位访客。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 下面是这种方法对应的语法：

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * 以下是这种方法的代码示例：

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target methods {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * 下面是这种方法对应的语法：

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   一个方便使用的构造函数，用于使用给定参数创建 `ADBTargetLocationRequest` 对象。

   * 下面是这种方法对应的语法：

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   创建 `ADBTargetLocationRequest`。

   * 下面是这种方法对应的语法：

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * 以下是这种方法的代码示例：

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   从您的应用程序中清除Target cookie。

   * 下面是这种方法对应的语法：

      ```java
      public static void ClearCookies(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回 nil。访客资料保存在 `NSUserDefaults` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * 以下是这种方法的代码示例：

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * 下面是这种方法对应的语法：

      ```java
      public static string Dpuuid; 
      ```

   * 以下是这种方法的代码示例：

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * 下面是这种方法对应的语法：

      ```java
      public static string AudienceDpuuid; 
      ```

   * 以下是这种方法的代码示例：

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   设置 `dpid` 和 `dpuuid`。 If `dpid` and `dpuuid` are set, they are sent with each signal.

   * 下面是这种方法对应的语法：

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * 以下是这种方法的代码示例：

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * 下面是这种方法对应的语法：

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **重置**

   重置受众管理器 `UUID` 并清除当前访客资料。

   * 下面是这种方法对应的语法：

      ```java
      public static void Reset ();
      ```

   * 以下是这种方法的代码示例：

      ```java
       AudienceManager.Reset ();
      ```

## 视频 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

有关视频分析的更多信息，请参阅 [视频分析](/help/android/analytics-main/video-qs.md)。

* **MediaSettings**

   通过指定的参数返回 `MediaSettings` 对象。

   * 下面是这种方法对应的语法：

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * 以下是这种方法的代码示例：

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   返回用于跟踪广告视频的 `MediaSettings` 对象。

   * 下面是这种方法对应的语法：

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Open**

   打开 `ADBMediaSettings` 对象以进行跟踪。

   * 下面是这种方法对应的语法：

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * 以下是这种方法的代码示例：

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **关闭**

   关闭具有指定名称的媒体项目。

   * 下面是这种方法对应的语法：

      ```java
      public static void Close(string name);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Close (settings.Name); 
      ```

* **Play**

   在指定偏移位置播放具有指定名称的媒体项目（以秒为单位）。

   * 下面是这种方法对应的语法：

      ```java
      public static void Play ( string name, double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **完成**

   在提供的偏移位置将媒体项目手动标记为完成（以秒为单位）。

   * 下面是这种方法对应的语法：

      ```java
      public static void Complete (string name, double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   通知媒体模块已在指定的偏移位置停止或暂停视频。

   * 下面是这种方法对应的语法：

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **单击**

   通知媒体模块已单击媒体项目。

   * 下面是这种方法对应的语法：

      ```java
      public static void Click ( string name, double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **跟踪**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 下面是这种方法对应的语法：

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.Track (settings.Name, null); 
      ```
