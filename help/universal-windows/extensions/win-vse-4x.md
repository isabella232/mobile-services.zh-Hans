---
description: 此扩展为您在项目中添加Experience Cloud解决方案4.x Windows SDK引用提供了一种更简单的方法。
solution: Experience Cloud Services,Analytics
title: 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# 适用于 Experience Cloud 解决方案 4.x SDK 的 Windows Visual Studio 扩展 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展为在您的项目中添加Experience Cloud解决方案4.x Windows SDK的引用提供了一种更轻松的方法。

## 从GitHub安装库 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 从下载Windows通用SDK [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. 在本地解压缩下载的文件。
1. 双击 **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** 文件以打开安装程序。
1. 选择 **[!UICONTROL 全局位置]** 并安装库。

## 向项目添加引用 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 打开您的Windows 10项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在 **[!UICONTROL 扩展]** 选项卡，找到并选择 **[!UICONTROL AdobeMobile SDK]**.
1. 单击 **[!UICONTROL 确定]** 来保存它。

   AdobeMobile SDK将添加到您的项目中。 如果 **[!UICONTROL Microsoft Visual C++运行时]** 包尚未添加，此包也将添加到您的项目中。

1. 在配置管理器中，选择一个平台类型并开始测试您的应用程序。
