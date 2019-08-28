---
description: 以下是 iOS 库提供的 Adobe Analytics 方法列表。
seo-description: 以下是 iOS 库提供的 Adobe Analytics 方法列表。
seo-title: 分析方法
solution: Marketing Cloud，Analytics
title: 分析方法
topic: 开发人员和实施
uuid: d49fe6de-cb32-4b96-9891-c567310 e59 a6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

以下是 iOS 库提供的 Adobe Analytics 方法列表。

SDK目前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包。

* **trackState:data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。如果 `state` 为空，它会在报表中显示为“应用程序名称 应用程序版本 (内部版本)”。**&#x200B;如果您在报表中看到此值，请确保在每个 `state` 调用中设置 `trackState`。

   >[!TIP]
   >
   >这是增加页面视图的唯一跟踪调用。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   跟踪您的应用程序中的操作。您要测量的操作(如 `logons`、 `banner taps`和其他指标 `feed subscriptions`)会在您的应用程序中进行。

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   检索分析跟踪标识符。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   跟踪后台发生的操作，此方法在某些情况下会阻止生命周期事件的触发。

   >[!TIP]
   >
   >仅应在应用程序处于后台运行的代码中调用此方法。

   * 下面是这种方法对应的语法：

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   发送当前的 x y 坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   跟踪用户接近信标的时间。

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   在用户远离信标后清除信标数据。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   向用户的生命周期值中添加 `amount`。

   * 下面是这种方法对应的语法：

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   启动名为 `action` 的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   传入 `data`，以更新与给定 `action` 关联的上下文数据。传入的 `data` 将附加到操作的现有数据中，如果已经为 `action` 定义相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   结束定时操作。如果提供 `block`，您将可以访问最终时间值，并且还能够在发送最终点击之前处理 `data`。

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   需要SDK4.1。无论当前有多少点击正在排队，强制库在脱机队列中发送所有点击。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   检索离线队列中的当前点击量。

   * 下面是这种方法对应的语法：

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   清除离线队列中的所有点击。

   >[!CAUTION]
   >
   >手动清除队列时务必谨慎。此过程无法撤消。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   跟踪推送消息点进。

   >[!IMPORTANT]
   >
   >此方法不增加页面视图。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
