---
description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-title: 移动应用程序获取
solution: Marketing Cloud，Analytics
title: 移动应用程序获取
topic: 开发人员和实施
uuid: 5fece619-e4 b8-4d06-9250-dcb66 fa32 ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。

要使用 Acquisition，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.1 或更高版本。

客户获取链接必须在 Adobe Mobile Services 中创建。有关更多信息，请参阅 [](/help/using/acquisition-main/acquisition-main.md)客户赢取。

本节中的信息允许SDK从获取链接发送获取数据。

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *将SDK和配置文件添加到核心实施和生命周期* 中 [的项目](/help/ios/getting-started/dev-qs.md)。
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
   >如果要向多个报表包发送数据，请使用应用程序中与报表包ID列表中第一个报告套件关联的获取设置(获取服务器和appid)。

   `acquisition` 设置由 Adobe Mobile Services 生成，不应对其进行更改。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

启用这些设置后，将会在首次启动应用程序后的初始生命周期调用中自动发送客户获取数据。

>[!CAUTION]
>
>`referrerTimeout` 必须设置为大于的值才能启用应用程序获取。

## 为通用链接启用iOS应用程序

如果您在应用程序中使用通用链接，请将您的Adobe Marketing Links域添加到应用程序的关联域列表中。

在Xcode中，将您的Adobe Marketing Links域添加到关联的域列表中：

1. 转到项目目标，然后单击 **[!UICONTROL 功能]** 选项卡。
2. 向下滚动到 **[!UICONTROL 关联的域]** 部分，然后将其切换。
3. 在营销链接 **[!UICONTROL URL中为您的营销链接域添加一个条目]** 列表。

您的条目 `applinks:5848561889a02a6996aea62b.c00.adobe.com`将类似于。