---
description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
keywords: android;library;mobile;sdk
seo-description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-title: 移动设备应用程序客户获取
solution: Experience Cloud,Analytics
title: 移动设备应用程序客户获取
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 100%

---


# 移动设备应用程序客户获取 {#mobile-app-acquisition}

带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>要使用“客户获取”功能，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.1 或更高版本。

必须在 Adobe Mobile Services 中创建客户获取链接。有关更多信息，请参阅[客户获取](/help/using/acquisition-main/acquisition-main.md)。

**在 SDK 版本 4.18.0 及更高版本中**：

从 2020 年 3 月 1 日开始，Google 将弃用 install_referrer 意图广播机制。有关更多信息，请参阅[仍在使用 InstallBroadcast？在 2020 年 3 月 1 日之前切换到 Play Referrer API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)。要继续从 Google Play 商店收集安装反向链接信息，请更新您的应用程序以使用 SDK 版本 4.18.0 或更新版本。

弃用后，您需要从新的 Google API 收集安装反向链接 URL，并将生成的 URL 传递给 SDK，而不是创建 `BroadcastReceiver`。

1. 将 Google Play Install Referrer 程序包添加到您 Gradle 文件的依赖项中：

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. 要从 Install Referrer API 检索反向链接 URL，请完成[获取安装反向链接](https://developer.android.com/google/play/installreferrer/library#install-referrer)中的步骤。

1. 将反向链接 URL 传递到 SDK：

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>为避免在应用程序中调用不必要的 API，Google 建议您在安装后立即调用一次 API。

要确定在您的应用程序中使用 Google Play Install Referrer API 的最佳方式，请参阅 Google 的文档。以下是如何将 Adobe SDK 与 Google Play Install Referrer API 一起使用的示例：

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**在 SDK 版本 4.13.1 及更高版本中**：

如果您无法使用在 Adobe Mobile Services 中创建的客户获取链接，仍然可以通过使用 Google Play Acquisition 由 SDK 收集并发送客户获取数据。

要从标准 Google Play Acquisition 促销活动中收集客户获取数据，请执行以下操作：

* 使用标准 Google Play 商店客户获取方法。

   自定义客户获取数据可用于标准 Google Play Acquisition 键值对。

* 在用户下载并运行从 Google Play 商店客户获取获得的应用程序时，将收集来自反向链接的数据并将这些数据发送至 Adobe Mobile Services。

   * 数据将存储在之前在 SDK 中注册的 `AdobeDataCallback` 实例内以供使用。

      有关更多信息，请参阅[配置方法](/help/android/configuration/methods.md)。

   * 将使用 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 或 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 事件类型。

   * Google Play 中的客户获取数据包含的自定义键将具有“`a.acquisition.custom.`”命名空间。

如果您使用在 Adobe Mobile Services 中创建的客户获取链接，请完成下列任务以将自定义数据添加到客户获取链接：

1. 为客户获取变量添加前缀“`adb`”。

   当 SDK 在首次启动中从 Adobe Mobile Services 收到客户获取数据时，将存储该数据，并在之前使用 SDK 注册的实例 `AdobeDataCallback` 中提供。有关更多信息，请参阅[配置方法](/help/android/configuration/methods.md)。

1. 将使用 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 或 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 事件类型。

1. 自定义数据键将带有“`a.acquisition.custom.`”前缀。

>[!TIP]
>
>如果您将数据发送到多个报表包，请使用与报表包 ID 列表中的第一个报表包关联的应用程序中的客户获取数据。

此部分中的更新将使 SDK 能够通过客户获取链接发送客户获取数据。

## 跟踪移动客户获取 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 对反向链接实施 `BroadcastReceiver`：

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. 更新 `AndroidManifest.xml` 以启用在上一步骤中创建的 `BroadcastReceiver`：

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. 确认 `ADBMobileConfig.json` 文件包含必需的客户获取设置：

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >如果您将数据发送到多个报表包，请使用与报表包 ID 列表中的第一个报表包关联的应用程序中的客户获取设置（客户获取服务器和应用程序 ID）。

   `acquisition` 设置由 Adobe Mobile Services 生成，不应对其进行更改。有关如何下载预配置了 `acquisition` 设置的自定义 `ADBMobileConfig.json` 文件的更多信息，请参阅[开始之前](/help/android/getting-started/requirements.md)。

启用这些设置后，将会在首次启动应用程序后的初始生命周期调用中自动发送客户获取数据。

>[!CAUTION]
>
>`referrerTimeout` 必须设置为大于 0 的值，才能启用应用程序客户获取。
