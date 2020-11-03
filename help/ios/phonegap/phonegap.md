---
description: 使用该插件，您可以从 PhoneGap 项目发送 iOS AppMeasurement 调用。
keywords: phonegap
seo-description: 使用该插件，您可以从 PhoneGap 项目发送 iOS AppMeasurement 调用。
seo-title: PhoneGap 插件
solution: Experience Cloud,Analytics
title: PhoneGap 插件
topic: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '327'
ht-degree: 100%

---


# PhoneGap 插件{#phonegap-plug-in}

使用该插件，您可以从 PhoneGap 项目发送 iOS AppMeasurement 调用。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

正在寻找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？请单击[此处](https://aep-sdks.gitbook.io/docs/)获取我们的最新文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 Adobe Experience Platform Launch。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 创建 PhoneGap 项目

要创建 PhoneGap 项目，请参阅 [PhoneGap](https://helpx.adobe.com/cn/experience-manager/6-4/mobile/using/phonegap.html)。

## 使用 npm 安装插件：{#section_43229E57C16944C0B51531CB92089189}

1. 运行以下命令：

   ```
   cordova plugin add adobe-mobile-services
   ```

## 手动安装插件 {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### 包含 AppMeasurement 库

要包含 AppMeasurement，请执行以下操作：

1. 将 `ADBMobile_PhoneGap.h` 和 `ADBMobile_PhoneGap.m` 拖到 Xcode 项目的 **[!UICONTROL Plugins]** 文件夹中。
1. 完成以下设置：

   1. 选择&#x200B;**[!UICONTROL 将项目复制到目标组的文件夹（如有必要）]**。
   1. 选择您要使用 AppMeasurement 代码的目标位置。

1. 将 `ADB_Helper.js` 拖到您项目的 `www` 文件夹中。
1. 在 `res/xml` 文件夹中，打开 `config.xml` 并通过添加以下内容注册一个新插件：

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### 添加应用程序权限

AppMeasurement 库需要执行以下操作：

1. 启动 Xcode IDE 并打开您的应用程序。
1. 将 **[!UICONTROL AdobeMobile]** 文件夹拖到您的 Xcode 项目中，并完成以下设置：

   1. 选择&#x200B;**[!UICONTROL 将项目复制到目标组的文件夹（如有必要）]**。
   1. 选择&#x200B;**[!UICONTROL 为添加的任何文件夹创建群组]**。
   1. 选择您要在其中使用 AppMeasurement 代码的目标并单击&#x200B;**[!UICONTROL 完成]**。

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. 在您的项目目标的&#x200B;**[!UICONTROL 生成阶段]**&#x200B;选项卡中，展开&#x200B;**[!UICONTROL 将二进制文件与库关联]**&#x200B;部分，然后添加以下库：

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 确认您的应用程序在生成时没有出现意外错误。

## 实施自定义跟踪 {#section_FD102B3CDAA4492FB04E56BF17E28663}

在要使用跟踪的 `html` 文件中，将以下内容添加到 `<head>` 标记内：

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

