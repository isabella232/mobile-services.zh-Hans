---
title: 开发人员快速开始
seo-title: 针对Adobe移动服务的BlackBerry开发人员快速开始
description: BlackBerry开发人员快速开始指南可以帮助您了解为Adobe移动服务实施BlackBerry库的过程。
seo-description: BlackBerry开发人员快速开始指南可以帮助您了解为Adobe移动服务实施BlackBerry库的过程。
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# 开发人员快速入门

此信息有助于您了解实施BlackBerry库的过程。

## 获取SDK

**SDK需要BlackBerry 10或更高版本。**

解压下载的SDK后，验证文件夹中是否存在以下文 `AdobeMobile` 件：

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## 将SDK添加到您的项目

1. 右键单击您的项目，然后选择“ **[!UICONTROL 配置]** ”> **[!UICONTROL “添加库]**”。
1. 选择“ **[!UICONTROL 外部库]** ”，然后单 **[!UICONTROL 击“下一步]**”。
1. 单击 **[!UICONTROL 设备]** “库”字 **[!UICONTROL 段旁边的“]** 浏览”。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 在文件 `Device-Debug` 夹中，选 `libADBMobileShared.so` 择并单 **[!UICONTROL 击打开]**。
1. 单击 **[!UICONTROL Simulator库]** 字段旁 **[!UICONTROL 边的“浏览]** ”。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 在文件 `Device-Debug` 夹中，选 `libADBMobileShared.so` 择并单 **[!UICONTROL 击打开]**。
1. 单击 **[!UICONTROL “包括]** ”文件夹字段 **[!UICONTROL 旁边的“]** 添加”。
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 将文件夹 `public` 添加到您的包含中。
1. 在文 `ADBMobile-4.0.0BETA-BlackBerry` 件夹中，有一个名 `.json` 为的配置文件 `ADBMobileConfig.json`。

   将该文件复制到项目的根目录中。
1. 右键单击您的项目，然后选择“ **[!UICONTROL 刷新]**”。

   文 `.json` 件现在应在项目资源管理器 **[!UICONTROL 中可见]**。
1. 打开 `bar-descriptor.xml` 项目的文件。
1. 在窗口底部，选择“资产” **[!UICONTROL 选项卡]** 。
1. 确认已 **[!UICONTROL 选择(所有配置]** )，然后单击窗 **[!UICONTROL 口的“资]** 产”部 **[!UICONTROL 分中的]** “添加文件”。
   >[!TIP]
   >
   >QNX Momentics IDE中存在一个错误，它有时会阻止这些按钮可见。 如果看不到按钮，请调整窗口大小，直到它们出现。

1. 单击“ **[!UICONTROL 工作区]**”。
1. 在项目 `ADBMobileConfig.json` 中查找文件，然后单 **[!UICONTROL 击确定]**。

您的应用程序可以使用从库导入类 `adobeMobileLibrary.jar` /接口 `#include <ADBMobile.hpp>`。

## 添加应用程序权限

在 `bar-descriptor.xml` 项目目录中，添加一行 `<permission>access_internet</permission>`，或在QNX Momentics IDE中，选择“应用程序”选项卡的“ **[!UICONTROL 权限]** ”部分上的“Internet **[!UICONTROL ”框]** 。

## 更新配 `ADBMobileConfig.json` 置文件

文件 `ADBMobileConfig.json` 包含全局SDK设置。 您需要更新一些值才能开始。

The following is an example of an `ADBMobileConfig.json` file:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

您必须至少更新 `rsids` 和 `server` 参数。 有关详细信息，请参 [阅Adobe移动类和方法参考](/help/blackberry/methods.md)。

您现在可以在BlackBerry 10应用程序中实施Analytics。
