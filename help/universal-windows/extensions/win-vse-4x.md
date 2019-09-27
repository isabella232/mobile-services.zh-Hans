---
description: 利用这些扩展，您可以更方便地在项目中添加 Experience Cloud 解决方案 4.x Windows SDK 的引用。
seo-description: 利用这些扩展，您可以更方便地在项目中添加 Experience Cloud 解决方案 4.x Windows SDK 的引用。
seo-title: Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Analytics
title: 适用于Experience Cloud Solutions 4.x SDK的Windows Visual studio扩展
topic: 开发人员和实施
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

此扩展提供了一种更轻松的方式，可在您的项目中添加Experience Cloud Solutions 4.x Windows SDK的参考。

## 从GitHub安装库 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 从 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 下载 Windows 通用 SDK。
1. 在本地解压缩下载的文件。
1. 双击 **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsix文件以打开安装程序]** 。
1. 选择 **[!UICONTROL 全局位置]** ，然后安装库。

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. 打开您的 Windows 10 项目。
1. 打开“引用管理器”(Reference Manager)对话框。

   ![](assets/ref_manager.png)

1. 在“扩 **[!UICONTROL 展]** ”选项卡上，找到并选 **[择UICONTROL Adobe Mobile SDK]**。
1. 单击&#x200B;**[!UICONTROL 确定]进行保存。**

   Adobe Mobile SDK将添加到您的项目。 如果 **[尚未添加UICONTROL Microsoft Visual C++ Runtime]** ，则此包也将添加到您的项目中。

1. 在“配置管理器”中，选择一个平台类型并开始测试应用程序。

