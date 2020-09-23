---
description: 此扩展为您提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的参考。
seo-description: 此扩展为您提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的参考。
seo-title: 针对Experience Cloud解决方案4.x SDK的Windows Visual Studio扩展
solution: Experience Cloud,Analytics
title: 针对Experience Cloud解决方案4.x SDK的Windows Visual Studio扩展
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展为您提供了一种更轻松的方式，在您的项目中添加Experience Cloud解决方案4.x Windows SDK的参考。

## 从GitHub安装库 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 从GitHub下载Windows通用 [SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. 在本地解压缩下载的文件。
1. 多次单击ADBMobileWindowsStoreVSIX.vsix或ADBMobileWindowsPhoneVSIX.vsix文件以打开安装程序。

1. 选择 **[!UICONTROL “全局位置]** ”并安装库。

## 添加对项目的引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 打开Windows 8.1或Windows Phone 8.1项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在Windows **[!UICONTROL 8]** .1或Windows Phone 8.1的“扩展”选项卡上，找到并选择“ **[!UICONTROL Adobe移动SDK”]**。
1. 单击 **[!UICONTROL 确定]** 以保存它。

   AdobeMobile SDK将添加到您的项目中，如果尚未添加，则 **[!UICONTROL 还会添加Microsoft Visual C+]** + Runtime包。

1. 在Configuration Manager中，选择一种平台类型，然后开始测试您的应用程序。

