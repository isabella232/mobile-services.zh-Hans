---
description: 此扩展为您提供了一种更简单的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。
seo-description: 此扩展为您提供了一种更简单的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。
seo-title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
solution: Experience Cloud,Analytics
title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---

# 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展提供了一种在项目中添加Experience Cloud Solutions 4.x Windows SDK参考的更简单的方法。

## 从GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}安装库

1. 从[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)下载Windows Universal SDK。
1. 将下载的文件解压缩到本地。
1. 多次 — 单击&#x200B;**[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]**&#x200B;文件以打开安装程序。
1. 选择&#x200B;**[!UICONTROL 全局位置]**&#x200B;并安装库。

## 添加对项目{#section_00C14FE9243D4330BE1F4BB56FCF08B1}的引用

1. 打开Windows 10项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;选项卡上，找到并选择&#x200B;**[!UICONTROL Adobe Mobile SDK]**。
1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;以保存它。

   Adobe Mobile SDK将添加到您的项目。 如果尚未添加&#x200B;**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;包，则此包也将添加到您的项目。

1. 在Configuration Manager中，选择一个平台类型并开始测试您的应用程序。
