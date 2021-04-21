---
description: 构建iOS项目
keywords: Unity
solution: Experience Cloud
title: 构建项目
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# 构建项目{#building-your-project}

## iOS

在为iOS构建时，将创建一个Xcode项目。 默认情况下，`ADBMobileWrapper.mm`和`AdobeMobileLibrary.a`文件将位于新项目的库组中。 执行构建应用程序所需的以下手动步骤：

1. 将 `ADBMobileConfig.json` 文件添加到项目中。

   确保它是构建的成员，任何必要的目标。

1. 在项目的&#x200B;**[!UICONTROL 构建阶段]**&#x200B;选项卡中，添加指向以下库的链接：

   * `SystemConfiguration.framework`
（此库可能已链接。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>要使用SDK的本地通知应用程序内消息，您必须从第一个Unity Scene中的开始方法调用`ADBMobile.EnableLocalNotifications();`。

## Android

在为Android构建时，`apk`文件已在正确位置包含`ADBMobileConfig.json`文件。 默认情况下，还会使用`/Plugins/Android`文件夹中的`AndroidManifest.xml`文件。

如果您需要使用自己的自定义清单文件，应添加以下更改。

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
