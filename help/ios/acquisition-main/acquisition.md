---
description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户在单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-description: 带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户在单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。
seo-title: 移动设备应用程序客户获取
solution: Experience Cloud,Analytics
title: 移动设备应用程序客户获取
topic: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 100%

---


# 移动设备应用程序客户获取 {#mobile-app-acquisition}

带有唯一跟踪码的客户获取链接可以在 Adobe Mobile Services 中生成。当用户在单击生成的链接后从 Apple App Store 下载并运行应用程序时，SDK 会自动收集客户获取数据并将这些数据发送至 Adobe Mobile Services。

要使用“客户获取”功能，您&#x200B;**必须**&#x200B;具有 SDK 版本 4.1 或更高版本。

必须在 Adobe Mobile Services 中创建客户获取链接。有关更多信息，请参阅[客户获取](/help/using/acquisition-main/acquisition-main.md)。

此部分中的信息将使 SDK 能够通过客户获取链接发送客户获取数据。

## 跟踪移动设备应用程序客户获取 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 确认 `ADBMobileConfig.json` 文件包含必需的客户获取设置：

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
   >如果您将数据发送到多个报表包，请使用与报表包 ID 列表中的第一个报表包关联的应用程序中的客户获取设置（客户获取服务器和应用程序 ID）。

   `acquisition` 设置由 Adobe Mobile Services 生成，不应对其进行更改。有关如何下载预配置了 `acquisition` 设置的自定义 `ADBMobileConfig.json` 文件的更多信息，请参阅[开始之前](/help/ios/getting-started/requirements.md)。

启用这些设置后，将会在首次启动应用程序后的初始生命周期调用中自动发送客户获取数据。

>[!CAUTION]
>
>`referrerTimeout` 必须设置为大于 0 的值，才能启用应用程序客户获取。

## 启用 iOS 应用程序的通用链接

如果您在应用程序中使用通用链接，请将您的 Adobe 营销链接域添加到应用程序的“关联的域”列表。

在 Xcode 中，要将您的 Adobe 营销链接域添加到“关联的域”列表，请执行以下操作：

1. 转到项目目标并单击&#x200B;**[!UICONTROL 功能]**&#x200B;选项卡。
2. 向下滚动到&#x200B;**[!UICONTROL 关联的域]**&#x200B;部分并将其打开。
3. 在&#x200B;**[!UICONTROL 域]**&#x200B;列表中，从营销链接 URL 为您的营销链接域添加一个条目。

您输入的内容类似于 `applinks:5848561889a02a6996aea62b.c00.adobe.com`。