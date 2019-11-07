---
description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
keywords: Android;库;移动;SDK
seo-description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-title: 移动设备应用程序客户获取
solution: Marketing Cloud,Analytics
title: 移动设备应用程序客户获取
topic: 开发人员和实施
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# 移动设备应用程序客户获取 {#mobile-app-acquisition}

带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从应用商店下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

>[!IMPORTANT]
>
>要使用 Acquisition，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.1 或更高版本。

客户获取链接必须在 Adobe Mobile Services 中创建。有关更多信息，请参阅[客户获取](/help/using/acquisition-main/acquisition-main.md)。

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

   当 SDK 收到来自 Adobe Mobile Services 的客户获取数据（首次启动）时，该数据将存储在之前在 SDK 中注册的 `AdobeDataCallback` 实例内以供使用，如[配置方法](/help/android/configuration/methods.md)中所述。

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
