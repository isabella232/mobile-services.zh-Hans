---
description: 使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。
keywords: android；库；移动；sdk
seo-description: 使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。
seo-title: PhoneGap插件概述
solution: Marketing Cloud,Analytics
title: PhoneGap插件概述
topic: 开发人员和实施
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# PhoneGap插件概述 {#phonegap-plug-in}

使用该插件，您可以从 PhoneGap 项目发送 Android AppMeasurement 调用。要创建PhoneGap项目，请参 [阅PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html)。

## 新版Adobe Experience Platform Mobile SDK

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* 要开始使用，请转到Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 使用 npm 安装插件 {#section_43229E57C16944C0B51531CB92089189}

运行以下命令：

```java
cordova plugin add adobe-mobile-services
```

## 手动安装插件 {#section_EA1FD59C484D44878AB509954DEE6037}

## 包含插件

1. 将文件 `ADBMobile_PhoneGap.java` 拖到您的文 `src` 件夹。

   To move this file, click **[!UICONTROL OK]**.

1. 将文 `ADB_Helper.js` 件拖动到包含该文件的文 `index.html` 件夹

   To move this file, click **[!UICONTROL OK]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例如，如果您的包名为 `com.example.phonegaptest`，则 `android-package` 值应当如下所示：

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## 包括AppMeasurement库

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. 将文件拖 `adobeMobileLibrary.jar` 到您的文 `src` 件夹。

   To move this file, click **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. 根据项目的要求，输入库的名称、级别和位置。
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. 确认您选择的是根应用程序而&#x200B;**不是**&#x200B;应用程序中的应用程序。

   To move this file, click **[!UICONTROL OK]**.

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

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

