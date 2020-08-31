---
description: 以下是 Android 库提供的 Adobe Analytics 方法列表。
keywords: android;library;mobile;sdk
seo-description: 以下是 Android 库提供的 Adobe Analytics 方法列表。
seo-title: Analytics 方法
solution: Marketing Cloud,Analytics
title: Analytics 方法
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '740'
ht-degree: 100%

---


# Analytics 方法 {#analytics-methods}

以下是 Android 库提供的 Adobe Analytics 方法列表。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀，例如，Experience Cloud ID 方法的前缀为 `analytics`。

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包：

* **trackState**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中可用的一些视图，例如 `home dashboard`、`app settings`、`cart` 等等。这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

   如果 `state` 为空，则会在报表中显示 `app name app version (build)`。如果您在报表中看到此值，请确保在每个 `trackState` 调用中设置 `state`。

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
跟踪应用程序中的操作。

   例如，您的应用程序中发生的要测量的操作，包括 `logons`、`banner taps`、`feed subscriptions` 及其他量度。

   * 以下是此方法的语法：

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
返回自动为 Analytics 生成的访客标识符。

   这是在初始启动时生成的特定于应用程序的唯一访客 ID，并从那时起被保存和使用。这个 ID 在应用程序升级期间仍会保留，并在应用程序卸载后删除。

   * 以下是此方法的语法：

      ```java
      public static String getTrackingIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```java
      String trackingId = Analytics.getTrackingIdentifier();
      ```

* **trackLocation**

   发送当前的纬度和经度，以及在定义的目标点中的位置。有关更多信息，请参阅[地理位置和目标点](/help/android/location/geo-poi.md)。

   * 以下是此方法的语法：

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   向用户的生命周期值中添加 `amount`。

   * 以下是此方法的语法：

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   启动名为 `action` 的定时操作。

   如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

   ```java
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   传入 `contextData`，以更新与 `action` 关联的上下文数据。传入的 `data` 将附加到操作的现有数据中，如果已经为 `action` 定义相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * 以下是此方法的代码示例：

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   结束定时操作。如果提供 `block`，您可以访问最终时间值，并且还能够在发送最终点击之前处理 `data`。

   >[!TIP]
   >
   >如果提供 `block`，则必须返回 `true` 才能发送点击。为 `block` 传递 `null` 将发送最终点击。

   * 以下是此方法的语法：

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
              contextData.put("price", 49.95);
              return true;
          }
      });
      ```

* **sendQueuedHits**

   **需要 SDK 4.1。**

   无论有多少点击已排入队列，此方法都强制库发送离线队列中的所有点击。

   * 以下是此方法的语法：

      ```java
      public static void sendQueuedHits();
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   返回离线队列中存储的跟踪调用的数量。

   * 以下是此方法的语法：

      ```java
      public static long getQueueSize();
      ```

   * 以下是此方法的代码示例：

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   清除离线队列中的所有点击。

   * 以下是此方法的语法：

      ```java
      public static void clearQueue();
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > 手动清除队列时务必谨慎。此过程无法撤消。

* **processReferrer**

   处理来自 Google Play 商店的反向链接营销活动数据以供以后将来使用。

   * 以下是此方法的语法：

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > 此 API 在 SDK 版本 4.18.0 中开始提供

   从提供的 Google Play Install Referrer URL 检索客户获取数据。

   从此 API 收集的数据将在发送安装点击时发送到 Analytics，并将在 Adobe Data Callback 中提供。

   如果 SDK 已收集反向链接数据，调用此方法将导致不执行任何操作。

   有关如何检索反向链接 URL 的信息，请参阅 Google 文档：https://developer.android.com/google/play/installreferrer/library

   * 以下是此方法的语法：

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * 以下是此方法的代码示例：

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
