---
description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
keywords: mobile
seo-description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
seo-title: 配置客户获取
solution: Marketing Cloud,Analytics
title: 配置客户获取
topic: 量度
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 配置客户获取 {#configure-acquisition}

在跟踪和报告营销链接之前，必须在SDK配置中启用客户获取跟踪。

1. 在应用程序的“管理应用程序设置”界面上，滚动到 **[!UICONTROL SDK 客户获取选项]**&#x200B;部分。
1. 完成以下任务：

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * 在“引用超时（秒）” **[!UICONTROL 字段中输入一个值]** 。

      (可&#x200B;**选**)如果启用了“启用 **** ”复选框，则此字段为可选字段。 指定的超时值以秒为单位，您可以更改此值。此设置指定在发送首次启动点击之前等待客户获取信息的时间段。
   >[!IMPORTANT]
   >必须输入非零值。 如果您启用“客户获取”，但将值保留为零，则“客户获取”链接将不起作用。 建议您使用5秒的默认值。

1. 在您的应用程序中下载并使用新的 SDK 配置文件。

   您已成功在 **iOS** 上配置了客户获取。To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
