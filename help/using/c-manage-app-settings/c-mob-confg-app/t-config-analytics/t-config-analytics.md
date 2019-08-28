---
description: 创建新应用程序或编辑现有应用程序时，您可以在“管理应用程序设置”页面上配置“SDK Analytics”选项。
keywords: mobile
seo-description: 创建新应用程序或编辑现有应用程序时，您可以在“管理应用程序设置”页面上配置“SDK Analytics”选项。
seo-title: 配置 SDK Analytics 选项
solution: Marketing Cloud，Analytics
title: 配置 SDK Analytics 选项
topic: 量度
uuid: fd3a21d2-6560-4e96-92fe-b99 caac5 e834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

创建新应用程序或编辑现有应用程序时，您可以在“管理应用程序设置”页面上配置“SDK Analytics”选项。

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL 使用 HTTPS]**

   启用 HTTPS 以加强安全性。

* **[!UICONTROL 回溯会话点击量]**

   启用或禁用Adobe SDK到备份会话信息点击的功能。会话信息点击量当前由崩溃次数和会话时长构成。启用后，Adobe SDK 将回溯会话信息点击至前一会话最后一次点击的 1 秒后。这意味着崩溃次数和会话数据将与它们所发生的正确日期相关联。在应用程序每次新启动时都会回溯一次点击。在禁用后，Adobe SDK 将把会话信息附加到当前的生命周期。

* **[!UICONTROL 隐私]**

   选择隐私选项：

   * **[!UICONTROL 发送数据，直到选择禁用]**
   * **[!UICONTROL 保留数据，直到选择启用]**

* **[!UICONTROL 会话超时（秒）]**

   指定会话超时值。

   默认时间为 300 秒。指定应用程序在后一次启动时，必须与前一次启动间隔多长时间，才能被视为新会话（以秒为单位）。此超时也适用于应用程序被发送到后台后又重新启用的情况。会话时间长度不包括应用程序在后台中运行的时间。

* **[!UICONTROL 批量限制]**

   指定累计多少点击量后发送数据。

   设为 0 则立即发送点击量信息。批量限制表示要在连续调用中发送的点击量阈值。例如，如果此选项设为 10，则在第 10 次点击之前的每次点击都将存储在队列中。当第 10 次点击进入时，将相继发送所有 10 次点击。

* **[!UICONTROL 更多详细信息]**

   单击&#x200B;**[!UICONTROL 更多详细信息]链接可查看报表包 ID 和跟踪服务器、启用或禁用离线跟踪，以及查看正在使用的字符编码模型（例如 UTF-8）。**

   如果启用离线跟踪，则在设备脱机时生成的数据将被添加时间戳，并于稍后发送。如果禁用此选项，则脱机数据将被丢弃。
