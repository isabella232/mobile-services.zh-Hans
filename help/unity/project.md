---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 构建项目
solution: Experience Cloud
title: 构建项目
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 15%

---


# 构建项目{#building-your-project}

## iOS

在为iOS构建时，将创建一个Xcode项目。 默认情况下， `ADBMobileWrapper.mm` 和 `AdobeMobileLibrary.a` 文件将位于新项目的库组中。 执行构建应用程序所需的以下手动步骤：

1. 将 `ADBMobileConfig.json` 文件添加到项目中。

   确保它是构建的成员，任何必要的目标。

1. 在项目 **[!UICONTROL 的“构建阶段]** ”选项卡中，添加指向以下库的链接：

   * `SystemConfiguration.framework`
（此库可能已链接。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>要使用SDK的本地通知应用程序内消息，您必须从 `ADBMobile.EnableLocalNotifications();` 第一个Unity Scene中的开始方法调用。

## Android

在为Android构建时，文 `apk` 件已在正确 `ADBMobileConfig.json` 的位置包含文件。 默认情况下，还 `AndroidManifest.xml` 会使用您 `/Plugins/Android` 文件夹中的文件。

如果您需要使用您自己的自定义清单文件，应添加以下更改。

添加以下权限：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

如果您使用应用程序内消息传送服务，请添加以下活动和接收器：

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
