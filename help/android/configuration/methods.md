---
description: 以下是 Android 库提供的方法列表。
keywords: android;library;mobile;sdk
seo-description: 以下是 Android 库提供的方法列表。
seo-title: 配置方法
solution: Experience Cloud,Analytics
title: 配置方法
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 100%

---


# 配置方法{#configuration-methods}

以下是 Android 库提供的方法列表。

## 初始配置 {#section_9169243ECC4744A899A8271F92090ECD}

必须在主活动的 `onCreate` 方法中对以下方法调用一次：

* `setContext`
以下是此方法的代码示例：

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## SDK 设置（配置类）{#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * 注册用于实现 `AdobeDataCallback` 接口的对象。覆盖的“call”方法将通过 `Config.MobileDataEvent` 值以及 `Map<String, Object>` 中用于触发事件的关联数据进行调用。有关哪些事件将触发此回调的更多详细信息，请参阅本主题底部的 *MobileDataEventEnum*。

      >[!TIP]
      >
      >此方法需要版本 4.9.0 或更高版本。

   * 以下是此方法的语法：

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * 以下是此方法的代码示例：

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * 返回 Adobe Mobile 库的当前版本。
   * 以下是此方法的语法：

      ```java
      public static String getVersion();
      ```

   * 以下是此方法的代码示例：

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * 返回当前用户隐私状态的枚举表示形式。

      以下是隐私状态值：

      * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即发送点击。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：丢弃点击。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

         如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。默认值在 `ADBMobileConfig.json` 文件中设置。
   * 以下是此方法的语法：

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * 将当前用户的隐私状态设置为 `status`。

      您可以将隐私状态设置为以下值之一：
      * `MOBILE_PRIVACY_STATUS_OPT_IN`：立即发送点击。将会立即发送这些点击。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：丢弃点击。将会丢弃这些点击。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。
   * 以下是此方法的语法：

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * 返回当前用户的生命周期值。默认值为 `0`。

   * 以下是此方法的语法：

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * 以下是此方法的代码示例：

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * 如果已设置自定义标识符，则会返回自定义用户标识符。如果未设置自定义标识符，则会返回 `null`。默认值为 `null`。

      >[!TIP]
      >
      >如果您的应用程序从 Experience Cloud 3.x SDK 升级到 4.x SDK，则会检索之前的自定义访客 ID 或自动生成的访客 ID，并将其存储为自定义用户标识符。这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符在设置之前为 `null`。

   * 以下是此方法的语法：

      ```java
      public static String&amp getUserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * 将用户标识符设置为 `identifier`。
   * 以下是此方法的语法：

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * 返回当前的调试日志记录首选项。默认值为 `false`。
   * 以下是此方法的语法：

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * 将调试日志记录首选项设置为 `debugLogging`。
   * 以下是此方法的语法：

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * 指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/android/configuration/methods.md)。

   * 以下是此方法的语法：

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * 以下是此方法的代码示例：

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      包含额外的上下文数据：

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * （**版本 4.2 或更高版本**）指示 SDK 应收集生命周期数据以用于 SDK 中的所有解决方案。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。
   * 以下是此方法的语法：

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * 以下是此方法的代码示例：

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
      ```

* **pauseCollecting&#x200B;LifecycleData**

   * 指示 SDK 您的应用程序已暂停，以便正确计算生命周期量度。例如，`onPause` 会收集一个时间戳，以确定上一个会话长度。此方法还会设置一个标志，以便生命周期知晓应用程序并没有崩溃。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

   * 以下是此方法的语法：

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * （**版本 4.2 或更高版本**）设置将用于由 SDK 创建的通知的小图标。此图标将显示在状态栏中，并且将是用户在通知中心查看完整通知时显示的辅助图像。
   * 以下是此方法的语法：

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * （**版本 4.2 或更高版本**）设置将用于由 SDK 创建的通知的大图标。此图标将是用户在通知中心查看完整通知时显示的主要图像。
   * 以下是此方法的语法：

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * 以下是此方法的代码示例：

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * （**版本 4.2 或更高版本**）允许您在应用程序启动时加载其他 ADBMobile JSON 配置文件。在应用程序关闭之前，将一直使用该配置。
   * 以下是此方法的语法：

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * 以下是此方法的代码示例：

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * 设置推送通知的设备令牌。
   * 以下是此方法的语法：

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * 向 SDK 提供一个可调用对象以返回从 Google Play 服务返回的广告标识符字符串。SDK 在后台线程中运行此任务，并根据从可调用对象返回的值为广告标识符设置内部变量。

      >[!IMPORTANT]
      > 
      >如果您要在客户获取或生命周期中使用广告标识符，则必须先调用该广告标识符，然后再调用 `Config.collectLifecycleData`。

      * 以下是此方法的语法：

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * 以下是此方法的代码示例：

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback Interface {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
