---
description: 此扩展为您提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的参考。
seo-description: 此扩展为您提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的参考。
seo-title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
solution: Experience Cloud,Analytics
title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---


# 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的引用。

## 从GitHub安装库 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 从GitHub下载Windows通用 [SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 在本地解压缩下载的文件。
1. 多次单击 **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix文件]** ，打开安装程序。
1. 选择 **[!UICONTROL “全局位置]** ”并安装库。

## 添加对项目的引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 打开Windows 10项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在“扩 **[!UICONTROL 展]** ”选项卡上，找到并选 **[!UICONTROL 择“AdobeMobile SDK]**”。
1. 单击 **[!UICONTROL 确定]** 以保存它。

   AdobeMobile SDK将添加到您的项目。 如果 **[!UICONTROL 尚未添加Microsoft Visual C+]** + Runtime包，则此包也将添加到您的项目。

1. 在Configuration Manager中，选择一种平台类型并开始测试您的应用程序。

