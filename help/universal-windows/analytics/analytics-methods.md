---
description: 帮助您将通用Windows平台SDK与Adobe Analytics一起使用的信息。
seo-description: 帮助您将通用Windows平台SDK与Adobe Analytics一起使用的信息。
seo-title: Analytics 方法
solution: Experience Cloud,Analytics
title: Analytics 方法
topic-fix: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
exl-id: 3ceaedfa-274f-4dc7-9e4c-15233d09f935
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 57%

---

# Analytics 方法 {#analytics-methods}

帮助您将通用Windows平台SDK与Adobe Analytics一起使用的信息。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。 方法将根据解决方案来添加前缀。分析方法前缀为“Analytics”。

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包。

>[!TIP]
>
>当您从winJS(JavaScript)使用`winmd`方法时，所有方法都会自动将其第一个字母小写。

* **TrackState(winJS:trackState)**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中提供的视图，如“主仪表板”、“应用程序设置”、“购物车”等。 这些状态与网站中的页面类似，而且 `TrackState` 调用会使页面查看次数递增。如果`state`为空，则报告中将显示为“应用程序名称应用程序版本（内部版本）”。 如果在报告中看到此值，请确保在每个`TrackState`调用中设置`state`。

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction(winJS:trackAction)**

   跟踪您的应用程序中的操作。操作是您要衡量的应用程序中发生的事情，如“登录”、“横幅点击”、“源订阅”和其他量度。

   * 以下是此方法的语法：

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync(winJS:getTrackingIdentifierAsync)**

   返回自动生成的Analytics访客ID。 这是特定于应用程序的唯一访客ID，在初始启动时生成，然后从该点开始存储和使用。 此ID将在应用程序升级期间保留，并在卸载时删除。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * 以下是此方法的代码示例：

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation(winJS:trackLocation)**

   发送当前的 x y 坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 以下是此方法的语法：

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime值&#x200B;增加(winJS:trackLifetime &#x200B; ValueIncrease)**

   向用户的生命周期值中添加 `amount`。

   * 以下是此方法的语法：

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart(winJS:trackTimed &#x200B; ActionStart)**

   启动名为 `action` 的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate(winJS:trackTimed &#x200B; ActionUpdate)**

   传入 `contextData`，以更新与给定 `action` 关联的上下文数据。传入的 `data` 会附加到给定操作的现有数据中，如果已经为 `action` 定义了相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync(winJS:trackTimedActionExistsAsync)**

   如果给定的定时操作存在，则返回true；如果给定的定时操作不存在，则返回false。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 以下是此方法的代码示例：

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd(winJS:trackTimed &#x200B; ActionEnd)**

   结束定时操作。

   * 以下是此方法的语法：

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue(winJS:clearTrackingQueue)**

   清除Analytics跟踪队列中所有存储的点击。

   * 以下是此方法的语法：

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 以下是此方法的代码示例：

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync(winJS:getQueueSizeAsync)**

   返回Analytics队列中当前存储的点击数。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 以下是此方法的代码示例：

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
