---
description: 此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。
keywords: Unity
seo-description: 此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。
seo-title: 适用于 iOS 和 Android 4.x SDK 的 Unity 插件
solution: Experience Cloud
title: 适用于 iOS 和 Android 4.x SDK 的 Unity 插件
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '141'
ht-degree: 100%

---


# 适用于 iOS 和 Android 4.x SDK 的 Unity 插件 {#unity-plug-in-for-the-ios-and-android-x-sdks}

此插件能够让您从 Unity 应用程序发送 Adobe Analytics 调用。

上次更新：**2020 年 3 月 10 日**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## 入门指南 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

从 GitHub 下载 ADBMobile.unitypackage 文件。

以下是 `ADBMobile.unitypackage` 文件的内容：

* 资产（根）

   * ADBMobile

   * 插件

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * assets

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**可选文件夹**：*Demo* 文件夹中包含 Unity 场景和示例代码。

## 将 ADBMobile 插件导入您的 Unity 项目 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. 打开您的 Unity 项目。
1. 双击 **[!UICONTROL ADBMobile.unitypackage]**。
1. 选择您希望导入的文件夹。
