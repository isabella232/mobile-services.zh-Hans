---
description: 必须先在 SDK 配置中启用客户获取跟踪，然后才能跟踪和报告营销链接。
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 配置客户获取
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# 配置客户获取 {#configure-acquisition}

必须先在 SDK 配置中启用客户获取跟踪，然后才能跟踪和报告营销链接。

1. 在应用程序的“管理应用程序设置”界面上，滚动到 **[!UICONTROL SDK 客户获取选项]**&#x200B;部分。
1. 完成以下任务：

   * 要启用客户获取，请选中&#x200B;**[!UICONTROL 启用]**&#x200B;复选框。

      选中此复选框后，**[!UICONTROL 反向链接超时]**&#x200B;字段会变为活动状态，其值会从 0 秒变为 5 秒。

   * 在&#x200B;**[!UICONTROL 反向链接超时（秒）]**&#x200B;字段中输入一个值

      （**可选**）如果您已启用&#x200B;**[!UICONTROL 启用]**&#x200B;复选框，则此字段为可选字段。指定的超时值以秒为单位，您可以更改此值。此设置指定在发送“首次启动”点击之前等待客户获取信息的时间。
   >[!IMPORTANT]
   >必须输入非零值。如果您启用了客户获取，但将超时值保留为 0，则客户获取链接将无法正常工作。我们建议您使用 5 秒的默认值。

1. 在您的应用程序中下载并使用新的 SDK 配置文件。

   您已成功在 **iOS** 上配置了客户获取。要在 **Android** 上启用客户获取，请完成[跟踪移动设备客户获取](/help/android/acquisition-main/acquisition.md)中的步骤。
