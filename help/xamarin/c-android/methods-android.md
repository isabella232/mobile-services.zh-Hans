---
description: 适用于Experience Cloud解决方案4.x SDK的Xamarin组件的Android方法。
keywords: 沙马林
solution: Experience Cloud
title: Android 方法
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Android 方法{#android-methods}

适用于Experience Cloud解决方案4.x SDK的Xamarin组件的Android方法。

## 配置方法 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   返回当前调试日志记录首选项，默认值为false。

   * 以下是此方法的语法：

      ```java
      public static Boolean DebugLogging;
      ```

   * 以下是此方法的代码示例：

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   返回当前用户的生命周期值。

   * 以下是此方法的语法：

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * 以下是此方法的代码示例：

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。
   * `ADBMobilePrivacyStatus.OptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatus.OptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatus.Unknown` - 如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   默认值在[ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md)文件中设置。

   * 以下是此方法的语法：

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * 以下是此方法的代码示例：

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **用户标识符**

   如果已设置自定义标识符，则会返回此标识符。 如果未设置自定义标识符，则返回null。 默认值为 `null`。

   * 以下是此方法的语法：

      ```java
      public static UserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **版本**

   获取库版本。

   * 以下是此方法的语法：

      ```java
      public static string Version;
      ```

   * 以下是此方法的代码示例：

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，暂停时会收集一个时间戳来确定上一个会话长度。 这还会设置一个标记，以便生命周期能够正确知道应用程序没有崩溃。 有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData(Activity activity)**

   （4.2或更高版本）指示SDK应收集生命周期数据以在SDK的所有解决方案中使用。 有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData(Activity activity)**

   （4.2或更高版本）指示SDK应收集生命周期数据以在SDK的所有解决方案中使用。 有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * 以下是此方法的代码示例：

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   （4.2或更高版本）允许您在应用程序启动时加载其他`ADBMobile JSON`配置文件。 在应用程序关闭之前，将一直使用该配置。

   * 以下是此方法的语法：

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * 以下是此方法的代码示例：

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   （4.2或更高版本）设置用于SDK创建的通知的大图标。 此图标是用户在通知中心查看完整通知时显示的主要图像。

   * 以下是此方法的语法：

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   （4.2或更高版本）设置用于SDK创建的通知的小图标。 此图标显示在状态栏中，是用户在通知中心查看完整通知时显示的辅助图像。

   * 以下是此方法的语法：

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * 以下是此方法的代码示例：

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics 方法 {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   返回自动为Analytics生成的ID。 这是在初始启动时生成的特定于应用程序的唯一ID，并从那时起被保存和使用。 此ID在应用程序升级期间仍会保留，并在卸载时删除。

   * 以下是此方法的语法：

      ```java
      public static string TrackingIdentifier;
      ```

   * 以下是此方法的代码示例：

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   通过可选的上下文数据跟踪应用程序状态。`States` 是您的应用程序中可用的一些视图，例如“标题屏幕”、“级别1”、“暂停”等。这些状态与网站中的页面类似，而且 `TrackState` 调用会使页面查看次数递增。如果状态为空，它会在报表中显示为“应用程序名称应用程序版本（内部版本）”。 如果在报表中看到此值，请确保在每个`TrackState`调用中设置状态。

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，例如“死亡”、“获得的级别”、“信息源订阅”及其他量度。

   >[!TIP]
   >
   >
   >如果您的代码可能会在应用程序位于后台时运行（例如，后台数据检索），请改用 `trackActionFromBackground`。

   * 以下是此方法的语法：

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   发送当前纬度和经度坐标。此方法还使用`ADBMobileConfig.json`文件中定义的目标点来确定作为参数提供的位置是否位于您的任何POI中。 如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `TrackLocation` 调用发送该变量。

   * 以下是此方法的语法：

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   跟踪用户接近信标的时间。

   * 以下是此方法的语法：

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   在用户远离信标后清除信标数据。

   * 以下是此方法的语法：

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   向用户的生命周期值中添加数量。

   * 以下是此方法的语法：

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   开始具有指定操作名称的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   > 这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   传入数据，以更新与给定操作关联的上下文数据。传入的数据将附加到给定操作的现有数据中，如果已经为操作定义了相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * 以下是此方法的代码示例：

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   结束定时操作。

   * 以下是此方法的语法：

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * 以下是此方法的代码示例：

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

   * 以下是此方法的语法：

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 以下是此方法的代码示例：

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   强制库发送离线队列中的所有点击，而不考虑当前排队的点击量。

   * 以下是此方法的语法：

      ```java
      public static void SendQueuedHits();
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   清除离线队列中的所有点击。

   * 以下是此方法的语法：

      ```java
      public static void ClearQueue(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.ClearQueue(); 
      ```

* **队列大小**

   检索离线队列中的当前点击量。

   * 以下是此方法的语法：

      ```java
      public static long QueueSize(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience CloudID方法 {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   从 ID 服务中检索 Experience Cloud ID。

   * 以下是此方法的语法：

      ```java
      public static string MarketingCloudId;
      ```

   * 以下是此方法的代码示例：

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   使用Experience CloudID，您可以设置其他客户ID以与每个访客关联。 访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 以下是此方法的语法：

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * 以下是此方法的代码示例：

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target 方法 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   向您配置的Target服务器发送请求，并返回在`Action<NSDictionary>`回调中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * 以下是此方法的代码示例：

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

   一个方便使用的构造函数，用于使用给定参数创建`ADBTargetLocationRequest`对象。

   * 以下是此方法的语法：

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * 以下是此方法的代码示例：

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   创建 `ADBTargetLocationRequest`。

   * 以下是此方法的语法：

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * 以下是此方法的代码示例：

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   从您的应用程序中清除Target Cookie。

   * 以下是此方法的语法：

      ```java
      public static void ClearCookies(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回nil。 访客资料保存在 `NSUserDefaults` 中，以供在多次启动应用程序时轻松访问。

   * 以下是此方法的语法：

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * 以下是此方法的代码示例：

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   返回当前的`DPID`。

   * 以下是此方法的语法：

      ```java
      public static string Dpuuid; 
      ```

   * 以下是此方法的代码示例：

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   返回当前的`DPUUID`。

   * 以下是此方法的语法：

      ```java
      public static string AudienceDpuuid; 
      ```

   * 以下是此方法的代码示例：

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   设置`dpid`和`dpuuid`。 如果设置了`dpid`和`dpuuid`，则它们将随每个信号一起发送。

   * 以下是此方法的语法：

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * 以下是此方法的代码示例：

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   向受众管理发送一个具有特征的信号，并获取`Action<NSDictionary>`回调中返回的匹配区段。

   * 以下是此方法的语法：

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * 以下是此方法的代码示例：

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

   重置Audience Manager `UUID`并清除当前访客资料。

   * 以下是此方法的语法：

      ```java
      public static void Reset ();
      ```

   * 以下是此方法的代码示例：

      ```java
       AudienceManager.Reset ();
      ```

## 视频 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

有关Video Analytics的更多信息，请参阅[Video Analytics](/help/android/analytics-main/video-qs.md)。

* **媒体设置**

   通过指定的参数返回 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * 以下是此方法的代码示例：

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   返回用于跟踪广告视频的 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * 以下是此方法的代码示例：

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Open**

   打开 `ADBMediaSettings` 对象以进行跟踪。

   * 以下是此方法的语法：

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * 以下是此方法的代码示例：

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

   关闭名为“name”的媒体项目。

   * 以下是此方法的语法：

      ```java
      public static void Close(string name);
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Close (settings.Name); 
      ```

* **播放**

   在给定的“offset”时间（以秒为单位）播放名为“name”的媒体项目。

   * 以下是此方法的语法：

      ```java
      public static void Play ( string name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **完成**

   在提供的“offset”时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```java
      public static void Complete (string name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **停止**

   通知媒体模块已在给定的“offset”时间停止或暂停视频。

   * 以下是此方法的语法：

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **单击**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```java
      public static void Click ( string name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **跟踪**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.Track (settings.Name, null); 
      ```
