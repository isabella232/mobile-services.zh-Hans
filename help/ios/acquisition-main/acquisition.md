---
description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-title: 移动App客户获取
solution: Marketing Cloud,Analytics
title: Mobile app acquisition
topic: 开发人员和实施
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。

要使用 Acquisition，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.1 或更高版本。

客户获取链接必须在 Adobe Mobile Services 中创建。For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

本节中的信息允许SDK从客户获取链接发送客户获取数据。

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 将库添加到您的项目并实施生命周期。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >  如果您将数据发送到多个报表包，请使用与报表包 ID 列表中的第一个报表包关联的应用程序中的客户获取设置（客户获取服务器和应用程序 ID）。

   `acquisition` 设置由 Adobe Mobile Services 生成，不应对其进行更改。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

启用这些设置后，将会在首次启动应用程序后的初始生命周期调用中自动发送客户获取数据。

>[!CAUTION]
>
>`referrerTimeout`  必须将  设置为大于 0 的值，才能启用应用程序客户获取。

## Enabling your iOS app for Universal Links

If you are using Universal Links in your app, add your Adobe Marketing Links domain to the Associated Domains list for your app.

In Xcode, to add your Adobe Marketing Links domain to the Associated Domains list:

1. 转到您的项目目标并单击“功 **[!UICONTROL 能]** ”选项卡。
2. 向下滚动到“关 **[!UICONTROL 联的域]** ”部分并将其打开。
3. 在“营销链接 **[!UICONTROL URL]** ”的“域”列表中为“营销链接”域添加一个条目。

你的条目看起来就象 `applinks:5848561889a02a6996aea62b.c00.adobe.com`。