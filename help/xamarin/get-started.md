---
description: 本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。
keywords: Xamarin
seo-description: 本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。
seo-title: Experience Cloud Solutions4.x SDK的Xamarin组件
solution: Marketing Cloud，开发人员
title: Experience Cloud Solutions4.x SDK的Xamarin组件
uuid: e7a48107-bd0 e-47d6-b49 c-dfce189 ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主题介绍如何开始使用用于移动解决方案 4.x SDK 的 Xamarin 组件。

上次更新日期：**2019 年 1 月 10 日**

## 入门指南 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK不再提供在Xamarin Components商店或Nubet Gallery中。要下载 Xamarin 组件，请转到 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

将AdbMobile组件导入您的Xamarin. Android项目：

1. 打开您的Xamarin项目

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. 从 `ADBMobile.XamarinAndroidBinding.dll`**[!UICONTROL lib/Android]** 文件夹中进行选择。

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 添加以下权限：

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 如果您使用应用程序内消息传递，请添加以下活动和接收方：

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 如果您使用的是客户获取，请添加以下接收方：

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

将AdbMobile组件导入您的Xamarin. iOS项目：

1. 打开您的Xamarin项目。
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. 从 `ADBMobile.XamarinIOSBinding.dll`**[!UICONTROL lib/ios统一]** 文件夹中进行选择。

1. 将您的 `ADBMobileConfig.json` 文件添加到项目中。


