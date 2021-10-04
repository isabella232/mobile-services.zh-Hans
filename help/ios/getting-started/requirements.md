---
description: 完成这些步骤可将报表包配置为收集 iOS 应用程序数据。
solution: Experience Cloud,Analytics
title: 开始之前
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 91%

---

# 开始之前 {#before-you-start}

完成这些步骤可将报表包配置为收集 iOS 应用程序数据。

## 特定于角色的任务 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理员和应用程序开发人员必须完成以下任务：

### Analytics 管理员

要配置报表包并收集移动设备应用程序数据，请执行以下操作：

1. 完成[登录 Adobe Mobile Services UI](/help/ios/getting-started/getting-started.md) 中的任一部分。
1. 为每个应用程序开发人员创建一个 Analytics 帐户。

应用程序开发人员现在将有权查看您创建的报表包。

>[!IMPORTANT]
>
>要创建新的报表包并下载 SDK，您必须是 Analytics 管理员。

### 应用程序开发人员

1. 确保 Analytics 管理员已完成以上“Analytics 管理员”**&#x200B;部分中的步骤。

1. 确认 Analytics 管理员已完成以下“登录到 Adobe Mobile Services 用户界面”**&#x200B;中的任一部分。
1. 配置报表包后，完成以下“下载 SDK”**&#x200B;部分中的步骤。

有关角色和权限的更多信息，请参阅[角色和权限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登录 Adobe Mobile Services UI {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是用于移动设备应用程序分析和定位的主要报告界面。完成这些步骤后，您可以下载一个配置文件，该文件已预先配置了数据收集服务器、报表包和许多其他设置。

您可以通过以下某种方式登录 Adobe Mobile Services ：

* **Experience Cloud**

   使用您的 Adobe ID 登录到 [Experience Cloud](https://experience.adobe.com)。

   此方法假定您的公司已配置，并且您已经关联 Analytics 帐户。有关配置的更多信息，请参阅《Experience Cloud中心界面组件指南》中的[管理Experience Cloud用户和产品](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) 。 有关关联帐户的更多信息，请参阅Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html)中的[组织。

   >[!TIP]
   >
   >如果不确定您的公司是否已在 Experience Cloud 中进行配置，请使用现有的 Adobe Analytics 帐户。

* **Adobe Analytics**

   单击&#x200B;**[!UICONTROL 使用 Analytics 登录]**&#x200B;并输入您的 Analytics 公司名称、用户名和密码。

## 创建报表包 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

要创建报表包以收集应用程序数据并定义应用程序，请执行以下操作：

1. 单击&#x200B;**[!UICONTROL 新建应用程序]**。

   如果未看到此按钮，请单击&#x200B;**[!UICONTROL 管理应用程序]** > **[!UICONTROL 添加]**。

1. 在&#x200B;**[!UICONTROL 报表包]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 新的报表包]**。

1. 输入应用程序的名称并选择一个唯一的报表包 ID。

   例如，报表包 ID 为 `mycomobileappdev`。您需要为开发版本和生产版本分别设置单独的报表包和应用程序。在您准备好设置生产版本后，请重复这些步骤。
1. 保留选中&#x200B;**[!UICONTROL 移动设备应用程序模板]**。

   此模板将启用时间戳以收集离线数据，并激活移动设备解决方案变量以捕获生命周期量度。

1. 选择您的&#x200B;**[!UICONTROL 时区]**、**[!UICONTROL 货币]**，然后单击&#x200B;**[!UICONTROL 保存]**。

## 下载 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

要下载 Mobile SDK，请执行以下操作：

1. 登录到 Mobile Services，然后通过以下方式之一打开应用程序：

   * 在&#x200B;**[!UICONTROL 所有应用程序]**&#x200B;下拉列表中，选择您的应用程序。
   * 在右侧窗格中，找到您的应用程序并将其打开。

1. 单击&#x200B;**[!UICONTROL 管理应用程序设置]**。
1. 在&#x200B;**[!UICONTROL 应用程序 SDK 下载]**&#x200B;部分中，滚动到&#x200B;**[!UICONTROL 应用程序 SDK 下载]**&#x200B;部分。

1. 下载适用于您的平台的 SDK 和示例应用程序。

>[!TIP]
>
>您应用程序的配置文件会自动包含在 SDK 下载中，因此无需单独下载该文件。但是，如果您已经下载了 SDK，并且想要获取更新的设置，则需要再次下载配置文件。
