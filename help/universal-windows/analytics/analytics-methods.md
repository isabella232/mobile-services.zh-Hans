---
description: 此信息可帮助您将通用 Windows 平台 SDK 与 Adobe Analytics 配合使用。
seo-description: 此信息可帮助您将通用 Windows 平台 SDK 与 Adobe Analytics 配合使用。
seo-title: 分析方法
solution: Marketing Cloud,Analytics
title: Analytics methods
topic: 开发人员和实施
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

此信息可帮助您将通用 Windows 平台 SDK 与 Adobe Analytics 配合使用。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。方法将根据解决方案来添加前缀。Analytics 方法具有“Analytics”前缀。

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **TrackState(winJS:trackState)**

   通过可选的上下文数据跟踪应用程序状态。状态是指您的应用程序中提供的各种视图，例如“主页功能板”、“应用程序设置”、“购物车”等。这些状态与网站中的页面类似，而且 `TrackState` 调用会使页面查看次数递增。如果 `state` 为空，它会在报表中显示为“应用程序名称 应用程序版本 (内部版本)”。如果您在报表中看到该值，请确保在每个 `state` 调用中设置 `TrackState`。

   >[!TIP]
   >
   >这是唯一可增加页面查看次数的跟踪调用。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction(winJS:trackAction)**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，例如“登录”、“横幅点按”、“信息源订阅”及其他量度。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   返回自动生成的 Analytics 访客 ID。这是一个应用程序特定的唯一访客 ID，在初次启动时生成，随后进行存储并一直使用下去。此 ID 会在应用程序升级期间保留，并在应用程序卸载后删除。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   发送当前的 x y 坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime&#x200B;ValueIncrease (winJS: trackLifetime&#x200B;ValueIncrease)**

   向用户的生命周期值中添加 `amount`。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed&#x200B;ActionStart (winJS: trackTimed&#x200B;ActionStart)**

   启动名为 `action` 的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed&#x200B;ActionUpdate (winJS: trackTimed&#x200B;ActionUpdate)**

   传入 `contextData`，以更新与给定 `action` 关联的上下文数据。传入的 `data` 会附加到给定操作的现有数据中，如果已经为 `action` 定义了相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync(winJS:trackTimedActionExistsAsync)**

   如果给定的定时操作存在，则返回true；如果给定的定时操作不存在，则返回false。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd(winJS:trackTimed &#x200B; ActionEnd)**

   结束定时操作。

   * 下面是这种方法对应的语法：

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue(winJS:clearTrackingQueue)**

   清除 Analytics 跟踪队列中所有存储的点击。

   * 下面是这种方法对应的语法：

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync(winJS:getQueueSizeAsync)**

   返回 Analytics 队列中当前存储的点击量。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 以下是这种方法的代码示例：

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
