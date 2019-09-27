---
description: 本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。
keywords: Xamarin
seo-description: 本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。
seo-title: 适用于Experience Cloud Solutions 4.x SDK的Xamarin组件
solution: Marketing Cloud,Developer
title: Xamarin components for Experience Cloud Solutions 4.x SDK
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。

上次更新日期：**2019 年 1 月 10 日**

## 入门指南 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Xamarin组件商店或NuGet Gallery中不再提供Adobe Mobile SDK。 要下载 Xamarin 组件，请转到 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

将ADBMobile组件导入您的Xamarin.Android项目：

1. 打开Xamarin项目

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/Android folder.`ADBMobile.XamarinAndroidBinding.dll`****

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 添加以下权限：

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. If you are using In-app messaging, add the following activity and receiver :

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 如果您使用客户获取，请添加以下接收器：

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

将ADBMobile组件导入您的Xamarin.iOS项目：

1. 打开您的Xamarin项目。
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. 从 `ADBMobile.XamarinIOSBinding.dll` lib/ios- **[!UICONTROL unified文件夹中进行选择]** 。

1. 将您的 `ADBMobileConfig.json` 文件添加到项目中。


