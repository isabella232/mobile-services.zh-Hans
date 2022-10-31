---
description: 创建新应用程序或编辑现有应用程序时，您可以在“管理应用程序设置”页面上配置“SDK Analytics”选项。
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 配置 SDK Analytics 选项
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%

---

# 配置 SDK Analytics 选项 {#configure-sdk-analytics-options}

{#eol}

创建新应用程序或编辑现有应用程序时，您可以在“管理应用程序设置”页面上配置“SDK Analytics”选项。

在 **[!UICONTROL SDK Analytics 选项]**&#x200B;下的以下字段中键入相应信息：

* **[!UICONTROL 使用 HTTPS]**

   启用 HTTPS 以加强安全性。

* **[!UICONTROL 回溯会话点击量]**

   启用或禁用 Adobe SDK 回溯会话信息点击量的功能。会话信息点击量当前由崩溃次数和会话时长构成。启用后，Adobe SDK 会将会话信息点击日期回溯到上一个会话最后一次点击后 1 秒。这意味着崩溃数据和会话数据将与正确的日期（即崩溃和会话发生的日期）相关联。在应用程序每次新启动时都会回溯一次点击。在禁用后，Adobe SDK 将把会话信息附加到当前的生命周期。

* **[!UICONTROL 隐私]**

   选择隐私选项：

   * **[!UICONTROL 发送数据，直到选择禁用]**
   * **[!UICONTROL 保留数据，直到选择启用]**

* **[!UICONTROL 会话超时（秒）]**

   指定会话超时值。

   默认时间为 300 秒。指定从应用程序启动到将该启动视为新会话之前必须经过的时长（以秒为单位）。此超时也适用于应用程序被发送到后台后又重新启用的情况。应用程序在后台所用的时间不包括在会话时长中。

* **[!UICONTROL 批量限制]**

   指定累计多少点击量后发送数据。

   设为 0 则立即发送点击量信息。批量限制是指连续调用中发送的点击数阈值。例如，如果将此选项设置为 10，则第 10 次点击之前的每次点击都将存储在队列中。当第 10 次点击进入时，将连续发送所有 10 次点击。

* **[!UICONTROL 更多详细信息]**

   单击&#x200B;**[!UICONTROL 更多详细信息]**&#x200B;链接可查看报表包 ID 和跟踪服务器、启用或禁用离线跟踪，以及查看正在使用的字符编码模型（例如 UTF-8）。

   启用脱机跟踪后，设备在脱机时生成的数据将加盖时间戳，并稍后发送。如果禁用此选项，将丢弃脱机数据。
