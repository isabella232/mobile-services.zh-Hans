---
title: 开发人员快速入门
description: 《BlackBerry开发人员快速入门指南》可帮助您了解为AdobeMobile Services实施BlackBerry库的过程。
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# 开发人员快速入门

此信息可帮助您了解实施BlackBerry库的过程。

## 获取SDK

**SDK需要BlackBerry 10或更高版本。**

解压缩下载的SDK后，请确认`AdobeMobile`文件夹中存在以下文件：

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

1. 右键单击您的项目并选择&#x200B;**[!UICONTROL 配置]** > **[!UICONTROL 添加库]**。
1. 选择&#x200B;**[!UICONTROL 外部库]**&#x200B;并单击&#x200B;**[!UICONTROL 下一步]**。
1. 单击&#x200B;**[!UICONTROL 设备库]**&#x200B;字段旁边的&#x200B;**[!UICONTROL Browse]**。
1. 导航到`ADBMobile-4.0.0BETA-BlackBerry`文件夹。
1. 在`Device-Debug`文件夹中，选择`libADBMobileShared.so`并单击&#x200B;**[!UICONTROL 打开]**。
1. 单击&#x200B;**[!UICONTROL 模拟器库]**&#x200B;字段旁边的&#x200B;**[!UICONTROL Browse]**。
1. 导航到`ADBMobile-4.0.0BETA-BlackBerry`文件夹。
1. 在`Device-Debug`文件夹中，选择`libADBMobileShared.so`并单击&#x200B;**[!UICONTROL 打开]**。
1. 单击&#x200B;**[!UICONTROL Include folders]**&#x200B;字段旁边的&#x200B;**[!UICONTROL Add]**。
1. 导航到`ADBMobile-4.0.0BETA-BlackBerry`文件夹。
1. 将`public`文件夹添加到包含的文件夹中。
1. 在`ADBMobile-4.0.0BETA-BlackBerry`文件夹中，有一个名为`ADBMobileConfig.json`的`.json`配置文件。

   将该文件复制到项目的根中。
1. 右键单击您的项目并选择&#x200B;**[!UICONTROL 刷新]**。

   现在，`.json`文件应会显示在&#x200B;**[!UICONTROL 项目资源管理器]**&#x200B;中。
1. 打开项目的`bar-descriptor.xml`文件。
1. 在窗口底部，选择&#x200B;**[!UICONTROL 资产]**&#x200B;选项卡。
1. 确认已选择&#x200B;**[!UICONTROL （所有配置）]**，然后单击窗口&#x200B;**[!UICONTROL Assets]**&#x200B;部分中的&#x200B;**[!UICONTROL 添加文件]**。
   >[!TIP]
   >
   >QNX Momentics IDE中存在一个错误，该错误有时会阻止显示这些按钮。 如果看不到按钮，请调整窗口大小，直到它们显示。

1. 单击&#x200B;**[!UICONTROL 工作区]**。
1. 在您的项目中找到`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 确定]**。

您的应用程序可以使用`#include <ADBMobile.hpp>`从`adobeMobileLibrary.jar`库导入类/接口。

## 添加应用程序权限

在项目目录的`bar-descriptor.xml`中，添加行`<permission>access_internet</permission>`，或在QNX Momentics IDE中，选择&#x200B;**[!UICONTROL Application]**&#x200B;选项卡权限部分上的&#x200B;**[!UICONTROL Internet]**&#x200B;框。

## 更新`ADBMobileConfig.json`配置文件

`ADBMobileConfig.json`文件包含全局SDK设置。 您需要更新一些值才能开始使用。

以下是`ADBMobileConfig.json`文件的示例：

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

必须至少更新`rsids`和`server`参数。 有关更多详细信息，请参阅[Adobe移动类和方法引用](/help/blackberry/methods.md)。

您现在可以在BlackBerry 10应用程序中实施Analytics。
