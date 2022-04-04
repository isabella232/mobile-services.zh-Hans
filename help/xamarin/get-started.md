---
description: 本主题介绍了如何开始使用面向移动设备解决方案 4.x SDK 的 Xamarin 组件。
keywords: 沙马林
solution: Experience Cloud Services
title: 面向 Experience Cloud 解决方案 4.x SDK 的 Xamarin 组件
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# 面向 Experience Cloud 解决方案 4.x SDK 的 Xamarin 组件 {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主题介绍了如何开始使用面向移动设备解决方案 4.x SDK 的 Xamarin 组件。

上次更新日期：**2019 年 1 月 10 日**

## 快速入门 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Xamarin Components Store 或 NuGet Gallery 不再提供 Adobe Mobile SDK。要下载 Xamarin 组件，请转到 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

将 ADBMobile 组件导入 Xamarin.Android 项目：

1. 打开您的 Xamarin 项目
1. 打开&#x200B;**[!UICONTROL 引用]**&#x200B;对话框，然后单击 **[!UICONTROL .Net Assembly]** 选项卡。
1. 从 **[!UICONTROL lib/Android]** 文件夹中选择 `ADBMobile.XamarinAndroidBinding.dll`。
1. 将 `ADBMobileConfig.json` 文件添加到您项目的 **[!UICONTROL Assets]** 文件夹中。
1. 添加以下权限：

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 如果您使用应用程序内消息传送服务，请添加以下活动和接收器：

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 如果您使用的是客户获取，请添加以下接收器：

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

将 ADBMobile 组件导入 Xamarin.iOS 项目：

1. 打开您的 Xamarin 项目。
1. 打开&#x200B;**[!UICONTROL 引用]**&#x200B;对话框，然后单击 **[!UICONTROL .Net Assembly]** 选项卡。
1. 从 **[!UICONTROL lib/ios-unified]** 文件夹中选择 `ADBMobile.XamarinIOSBinding.dll`。
1. 将 `ADBMobileConfig.json` 文件添加到项目中。
