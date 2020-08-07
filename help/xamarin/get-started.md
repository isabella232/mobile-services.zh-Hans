---
description: 本主题介绍如何开始使用Mobile solutions 4.x SDK的Xamarin组件。
keywords: Xamarin
seo-description: 本主题介绍如何开始使用Mobile solutions 4.x SDK的Xamarin组件。
seo-title: 用于Experience Cloud解决方案4.x SDK的Xamarin组件
solution: Marketing Cloud,Developer
title: 用于Experience Cloud解决方案4.x SDK的Xamarin组件
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

本主题介绍如何开始使用Mobile solutions 4.x SDK的Xamarin组件。

Last Updated: **January 10, 2019**

## 入门指南 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe移动SDK不再在Xamarin组件商店或NuGet库中提供。 要下载Xamarin组件，请转 [到GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

将ADBMobile组件导入您的Xamarin.Android项目：

1. 打开您的Xamarin项目
1. 打开 **[!UICONTROL “参照]** ”(References)对话框，然 **[!UICONTROL 后单击“.Net组件]** ”(.Net Assembly)选项卡。
1. 从 `ADBMobile.XamarinAndroidBinding.dll` lib/ **[!UICONTROL Android文件夹中选择]** 。
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. 添加以下权限：

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 如果您使用应用程序内消息传递，请添加以下活动和接收器：

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
1. 打开 **[!UICONTROL “参照]** ”(References)对话框，然 **[!UICONTROL 后单击“.Net组件]** ”(.Net Assembly)选项卡。
1. 从 `ADBMobile.XamarinIOSBinding.dll` lib/ios **[!UICONTROL -unified文件夹中进行选择]** 。
1. 将您的 `ADBMobileConfig.json` 文件添加到项目。
