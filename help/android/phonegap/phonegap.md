---
description: 使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。
keywords: Android;库;移动;SDK
seo-description: 使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。
seo-title: PhoneGap 插件概述
solution: Experience Cloud,Analytics
title: PhoneGap 插件概述
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 97%

---

# PhoneGap 插件概述 {#phonegap-plug-in}

使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。要创建 PhoneGap 项目，请参阅 [PhoneGap](https://helpx.adobe.com/cn/experience-manager/6-4/mobile/using/phonegap.html)。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 使用 npm 安装插件 {#section_43229E57C16944C0B51531CB92089189}

运行以下命令：

```java
cordova plugin add adobe-mobile-services
```

## 手动安装插件 {#section_EA1FD59C484D44878AB509954DEE6037}

## 包含插件

1. 将 `ADBMobile_PhoneGap.java` 文件拖到您的 `src` 文件夹中。

   要移动此文件，请单击&#x200B;**[!UICONTROL 确定]**。

1. 将 `ADB_Helper.js` 文件拖到包含 `index.html` 文件的文件夹中。

   要移动此文件，请单击&#x200B;**[!UICONTROL 确定]**。

1. 在 `res/xml` 文件夹中，打开 `config.xml` 文件并通过添加以下内容注册一个新插件：

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例如，如果您的包名为 `com.example.phonegaptest`，则 `android-package` 值应当如下所示：

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## 包含 AppMeasurement 库

1. 要下载 AppMeasurement 库，请参阅[获取 SDK](/help/android/getting-started/dev-qs.md)。
1. 将 `adobeMobileLibrary.jar` 文件拖到您的 `src` 文件夹中。

   要移动此文件，请单击&#x200B;**[!UICONTROL 确定]**。

1. 右键单击`adobeMobileLibrary.jar`文件，然后选择&#x200B;**[!UICONTROL 添加为库]**。
1. 根据项目的要求，输入库的名称、级别和位置。
1. 将 `ADBMobileConfig.json` 文件拖到应用程序根目录的 `assets` 文件夹中。
1. 确认您选择的是根应用程序而&#x200B;**不是**&#x200B;应用程序中的应用程序。

   要移动此文件，请单击&#x200B;**[!UICONTROL 确定]**。

## 添加应用程序权限

AppMeasurement 库需要以下权限来发送数据和记录离线跟踪调用：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

要添加这些权限，请将以下行添加到 `AndroidManifest.xml` 文件中，该文件位于应用程序项目目录内：

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

要启用应用程序内消息传送，请执行以下操作：

更新 AndroidManifest.xml 以声明全屏活动，并启用消息通知处理程序：

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

如果您在 Adobe Mobile Services 中创建消息时选择模态布局，请选择以下主题之一：

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

例如：

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## 实施自定义跟踪 {#section_FD102B3CDAA4492FB04E56BF17E28663}

在 `html` 文件中，将以下内容添加到要在其中使用跟踪的 `<head>` 标记中：

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
