---
description: 此扩展为您在项目中添加Experience Cloud解决方案4.x Windows SDK引用提供了一种更简单的方法。
solution: Experience Cloud,Analytics
title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展为在您的项目中添加Experience Cloud解决方案4.x Windows SDK的引用提供了一种更轻松的方法。

## 从GitHub安装库 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 从[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)下载Windows通用SDK。
1. 在本地解压缩下载的文件。
1. 双击&#x200B;**[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]**&#x200B;文件以打开安装程序。
1. 选择&#x200B;**[!UICONTROL 全局位置]**&#x200B;并安装库。

## 向项目添加引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 打开您的Windows 10项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;选项卡上，找到并选择&#x200B;**[!UICONTROL AdobeMobile SDK]**。
1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;以保存。

   AdobeMobile SDK将添加到您的项目中。 如果尚未添加&#x200B;**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;包，则此包也将添加到您的项目中。

1. 在配置管理器中，选择一个平台类型并开始测试您的应用程序。
