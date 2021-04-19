---
description: 此扩展为您提供了一种更简单的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。
seo-description: 此扩展为您提供了一种更简单的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。
seo-title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
solution: Experience Cloud,Analytics
title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---

# 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展为您提供了一种更简单的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。

## 从GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}安装库

1. 从[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)下载Windows Universal SDK。
1. 将下载的文件解压缩到本地。
1. 多次单击ADBMobileWindowsStoreVSIX.vsix或ADBMobileWindowsPhoneVSIX.vsix文件以打开安装程序。

1. 选择&#x200B;**[!UICONTROL 全局位置]**&#x200B;并安装库。

## 添加对项目{#section_00C14FE9243D4330BE1F4BB56FCF08B1}的引用

1. 打开Windows 8.1或Windows Phone 8.1项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在Windows 8.1或Windows Phone 8.1的&#x200B;**[!UICONTROL “扩展]**”选项卡上，找到并选择&#x200B;**[!UICONTROL Adobe Mobile SDK]**。
1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;以保存它。

   Adobe Mobile SDK将添加到您的项目中，如果尚未添加，则还会添加&#x200B;**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;包。

1. 在Configuration Manager中，选择一种平台类型，然后开始测试您的应用程序。
