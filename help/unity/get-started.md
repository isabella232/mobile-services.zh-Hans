---
description: 此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。
keywords: Unity
seo-description: 此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。
seo-title: 适用于 iOS 和 Android 4.x SDK 的 Unity 插件
solution: Marketing Cloud，开发人员
title: 适用于 iOS 和 Android 4.x SDK 的 Unity 插件
uuid: 83289a73-982d-4472-a8 c8-00b562 dc80 f5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# 适用于 iOS 和 Android 4.x SDK 的 Unity 插件 {#unity-plug-in-for-the-ios-and-android-x-sdks}

此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。

上次更新：**2016 年 10 月 20 日**

## 入门指南 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

从 GitHub 或 Developer Connection 下载 [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 文件。

以下是 `ADBMobile.unitypackage` 文件的内容：

* Assets（根）

   * ADBMobile

      * Demo

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
   * 插件

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * 资产

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a



可选文件夹：Demo 文件夹包含适用于每种受支持的脚本语言的 Unity 场景和示例代码。

## 将 ADBMobile 插件导入您的 Unity 项目 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. 打开您的 Unity 项目。
1. Double-click **[!UICONTROL ADBMobile.unitypackage]**.
1. 选择您希望导入的文件夹。

