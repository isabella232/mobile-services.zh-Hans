---
title: 开发人员快速入门
seo-title: BlackBerry Developer Quick Start for Adobe Mobile Services
description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
seo-description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start

此信息可帮助您了解 BlackBerry 库的实施过程。

## 获取 SDK

**SDK 需要 BlackBerry 10 或更高版本。**

在解压缩下载的 SDK 之后，请确认以下文件存在于 `AdobeMobile` 文件夹中：

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

## 将 SDK 添加到您的项目

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Select **[!UICONTROL External library]** and click **[!UICONTROL Next]**.
1. 单击&#x200B;**[!UICONTROL 设备库]**&#x200B;字段旁边的&#x200B;**浏览[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. 单击&#x200B;**[!UICONTROL 模拟器库]**&#x200B;字段旁边的&#x200B;**浏览[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. 单击&#x200B;**[!UICONTROL 包含文件夹]**&#x200B;字段旁边的&#x200B;**添加[!UICONTROL 。]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 将 `public` 文件夹添加到包含项中。
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   将该文件复制到项目的根目录。
1. Right-click on your project and select **[!UICONTROL Refresh]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. 打开项目的 `bar-descriptor.xml` 文件。
1. 在窗口底部选择&#x200B;**[!UICONTROL 资产]选项卡。**
1. 确认已选择&#x200B;**[!UICONTROL （所有配置）]**，然后单击窗口的&#x200B;**[!UICONTROL 资产]部分中的**&#x200B;添加文件&#x200B;**。**
   >[!TIP]
   >
   >There is a bug in the QNX Momentics IDE that sometimes prevents those buttons from being visible. If you can't see the buttons, resize the windows until they appear.

1. Click Workspace.****
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## 添加应用程序权限

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

`ADBMobileConfig.json` 文件包含全局 SDK 设置。您需要更新几个值才能开始使用它。

以下是 `ADBMobileConfig.json` 文件的示例：

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

You must at least update the `rsids` and `server` parameters. For more details, see Adobe Mobile class and method reference.[](/help/blackberry/methods.md)

现在，您可以在 BlackBerry 10 应用程序中实施 Analytics。
