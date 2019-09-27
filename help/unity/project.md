---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Building your project
solution: Marketing Cloud，开发人员
title: Building your project
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

当您构建 iOS 项目时，会生成一个 Xcode 项目。默认情况下，`ADBMobileWrapper.mm` 和 `AdobeMobileLibrary.a` 文件会出现在新项目的库群组中。手动执行构建应用程序所必需的下列步骤：

1. 将您的 `ADBMobileConfig.json` 文件添加到项目中。

   确保它是任何目标所必需的构建中的成员。

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(This library might be linked already.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

构建 Android 项目时，`apk` 文件已经在正确的位置包含了 `ADBMobileConfig.json` 文件。By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

如果您需要使用自己的自定义清单文件，则应该进行以下更改。

添加以下权限：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

If you are using In-app messaging, add the following activity and receiver:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

如果您使用客户获取，请添加以下接收器：

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
