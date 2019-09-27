---
description: 您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。
keywords: mobile
seo-description: 您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。
seo-title: 添加新应用程序
solution: Marketing Cloud,Analytics
title: 添加新应用程序
topic: 量度
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 添加新应用程序{#add-a-new-app}

您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。

以下说明将帮助您添加新应用程序，并配置 Adobe Analytics 和 Adobe Audience Manager 的集成。

您必须先在 Adobe Mobile Services 用户界面中添加应用程序，然后才能对其进行配置。创建应用程序之后，系统会生成正确的配置文件，您可以将它提供给正为应用程序实施 Mobile SDK 的开发人员。

1. 登录到 Adobe Mobile Services，然后完成以下任务之一：

   * 单击&#x200B;**[!UICONTROL 新建]以创建一个应用程序。**
   * To add additional apps, click Manage Apps in the left navigation menu and click **[!UICONTROL Add]**.

      有关登录的详细信息，请参阅 [登录](/help/using/gs/gs-signin.md)。

      >[!TIP]
      >
      >要管理现有应用程序，请单击左侧导航菜单中的“管理应用程序”，然后单击要修改的应用程序。 您可以在“应用程序信息”页面上进行更改。

1. 在以下字段中键入相应信息：

   **[!UICONTROL 报表包]**

   指定将在 Adobe Analytics 中收集和存储报表数据的报表包。每个应用程序都与一个 Analytics 报表包相连接。如果您将应用程序数据发送到多个报表包，请为每个报表包添加一个新应用程序。每个应用程序都与一个 Analytics 报表包相连接。如果您将应用程序数据发送到多个报表包，请为每个报表包添加一个新应用程序。

   如果您在 Adobe Mobile 中获得了 Analytics 管理员权限，则可以在 Adobe Mobile 中创建新的报表包。To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL 报表包 ID]**

      此ID可在Adobe Analytics中唯一标识报表包。 您的公司前缀会自动添加到 ID 的开头处。

   * **[!UICONTROL 复制设置自]**

      变量、事件、处理规则和其他设置在新的报表包中的设置与在此报表包中设置的设置完全相同。 只有在使用的“**从以下来源复制设置**”报表包是移动设备应用程序模板时，或者只有在您创建的是启用离线功能的报表包时，“Mobile Services”中创建的报表包才会启用离线功能（含时间戳）。

   * **[!UICONTROL 时区]**

      All reporting dates are in this time zone. 此设置会尝试使用与您的浏览器所用时区接近的时区。

   * **[!UICONTROL 货币]**

      收入将作为此类币种进行跟踪和报告。
   >[!TIP]
   >
   >要使用虚拟报告套件(VRS)，请参阅虚 [拟报告套件](/help/using/manage-apps/c-mob-vrs.md)。

   * **[!UICONTROL 图标]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL 名称]**

      (**Optional**) Type a descriptive name for the app. 此名称可帮助您快速找到应用程序，而有意义的名称可以帮助您快速了解应用程序的用途和设置。

   * **[!UICONTROL 类型]**

      从下拉列表中选择一种类型。在左侧导航菜单中显示的可用报表会依据您选择的应用程序类型而变。

      以下是可用的类型：

      * **[!UICONTROL 标准实施]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL 发布]**

         如果您的应用程序是使用 Adobe Digital Publishing Suite 创建的，则可以选择此选项。

      * **[!UICONTROL 游戏]**

         此选项类似于&#x200B;**[!UICONTROL 标准]**&#x200B;选项，但存在一个不同之处，即&#x200B;**游戏]选项会将报表中使用的术语更新为游戏术语。[!UICONTROL **&#x200B;例如，用户被更改为播放器。 对于游戏应用程序，会自动显示特定于游戏的报表。
   * **[!UICONTROL Description]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   添加应用程序后，您可以查看“应用程序信息”页面，了解有关配置其他选项的信息。For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
