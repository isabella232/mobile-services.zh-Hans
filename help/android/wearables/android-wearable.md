---
description: 从 Android SDK 版本 4.5 开始，新增了一个 Android 扩展，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-description: 从 Android SDK 版本 4.5 开始，新增了一个 Android 扩展，此扩展允许您从 Android 可穿戴应用程序中收集数据。
seo-title: Android 可穿戴应用程序：快速入门
solution: Experience Cloud,Analytics
title: Android 可穿戴应用程序：快速入门
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '291'
ht-degree: 100%

---


# Android 可穿戴应用程序：快速入门{#android-wearables-getting-started}

从 Android SDK 版本 4.5 开始，新增了一个 Android 扩展，此扩展允许您从 Android 可穿戴应用程序中收集数据。

## 为便携式应用程序配置 SDK (Android Studio) {#section_262237484EC44C58953891B105F0D000}

有关将 SDK 导入项目的更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)。

1. 将 `ADBMobileConfig.json` 文件添加到您项目的 assets 文件夹中。
1. 将 `adobeMobileLibrary-*.jar` 文件添加到 libs 文件夹中，或确保项目引用了该文件。

   >[!TIP]
   >
   >在添加该 `.jar` 文件后，您可能需要同步 Gradle 项目。

1. 在 `onCreate` 方法中，允许 SDK 使用 `Config.setContext` 访问您的应用程序上下文：

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. 将以下代码添加到 `AndroidManifest.xml` 文件：

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 确保您的项目包含 Google Play 服务库。
1. 实施 `WearableListenerService` 或将相应的代码添加到 `WearableListenerService` 中：

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. 将 `WearListenerService` 添加到 `AndroidManifest.xml` 文件：

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## 为可穿戴应用程序配置 SDK (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. 完成以下任务之一：

   * 将相同的 `ADBMobileConfig.json` 文件添加到可穿戴项目的 assets 文件夹中。
   * 更改 Gradle 配置以使用便携式应用程序 assets 文件夹中的 `ADBMobileConfig.json`：

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. 将 `adobeMobileLibrary-*.jar` 文件添加到 libs 文件夹中，或确保项目引用了该文件。

   在添加该 jar 文件后，您可能需要同步 Gradle 项目。

1. 在 `onCreate` 方法中，允许 SDK 使用 `Config.setContext` 访问您的应用程序上下文：

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. 将以下代码添加到 `AndroidManifest.xml`：

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 确保您的项目包含 Google Play 服务库。
1. 实施 `WearableListenerService` 或将相应的代码添加到 `WearableListenerService` 中：

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. 将 `WearListenerService` 添加到 `AndroidManifest.xml` 文件：

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

