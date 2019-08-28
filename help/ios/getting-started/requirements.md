---
description: 完成这些步骤可将报表包配置为收集 iOS 应用程序数据。
seo-description: 完成这些步骤可将报表包配置为收集 iOS 应用程序数据。
seo-title: 开始之前
solution: Marketing Cloud，Analytics
title: 开始之前
topic: 开发人员和实施
uuid: 04133f6818-41fd-8a13-aec5 b6 f04 df6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

完成这些步骤可将报表包配置为收集 iOS 应用程序数据。

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理员和应用程序开发人员必须完成以下任务：

### Analytics 管理员

要配置报表包并收集移动设备应用程序数据，请执行以下操作：

1. 完成[登录到 Adobe Mobile Services 用户界面](/help/ios/getting-started/getting-started.md)中的某一部分。
1. 为每个应用程序开发人员创建一个 Analytics 帐户。

此时应用程序开发人员便拥有查看您创建的报表包的权限。

>[!IMPORTANT]
>
>要创建新的报表包并下载SDK，您必须是Analytics管理员。

### 应用程序开发人员

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

有关角色和权限的更多信息，请参阅[角色和权限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登录到 Adobe Mobile Services 用户界面 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是用于移动设备应用程序分析和定位的主要报表界面。完成这些步骤后，您可以下载预先配置了数据收集服务器、报表包及许多其他设置的配置文件。

您可以使用以下任一方法登录到 Adobe Mobile Services：

* **Experience Cloud**

   使用您的 Adobe ID 登录到 [Experience Cloud](https://marketing.adobe.com)。

   此方法假定您的公司已被配置，并且您已关联了Analytics帐户。有关供应的更多信息，请参阅 [管理Experience Cloud用户和产品](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。有关链接帐户的详细信息，请参阅 [组织和帐户链接](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)。

   >[!TIP]
   >
   >如果您不确定您的公司是否已在Experience Cloud中供应，请使用您现有的Adobe Analytics帐户。

* **Adobe Analytics**

   单击&#x200B;**[!UICONTROL 使用 Analytics 登录]**&#x200B;并输入您的 Analytics 公司名称、用户名和密码。

## 创建报表包 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

要创建报表包以收集应用程序数据并定义应用程序，请执行以下操作：

1. Click **[!UICONTROL Create New App]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. 输入应用程序的名称并选择一个唯一的报表包 ID。

   例如，报表包 ID 为 `mycomobileappdev`。您需要为开发和生产版本设置单独的报表套件和应用程序。准备好设置生产版本时，请重复这些步骤。
1. 保留选中&#x200B;**[!UICONTROL 移动设备应用程序模板]。**

   此模板将启用时间戳以收集离线数据，并激活移动设备解决方案变量以捕获生命周期量度。

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## 下载 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

要下载 Mobile SDK，请执行以下操作：

1. 登录Mobile Services并通过以下任一方式打开应用程序：

   * 在&#x200B;**[!UICONTROL 所有应用程序]下拉列表中，选择您的应用程序。**
   * 在右侧窗格中，找到您的应用程序并将其打开。

1. Click **[!UICONTROL Manage App Settings]**.
1. 在&#x200B;**[!UICONTROL 应用程序 SDK 下载]**&#x200B;部分中，滚动到&#x200B;**应用程序 SDK 下载]部分。[!UICONTROL **

1. 下载适用于您的平台的 SDK 和示例应用程序。

>[!TIP]
>
>您的应用程序的配置文件自动包含在SDK下载中，因此您无需单独下载该文件。但是，如果您已经下载了 SDK，并且想要获取更新的设置，则需要再次下载配置文件。

