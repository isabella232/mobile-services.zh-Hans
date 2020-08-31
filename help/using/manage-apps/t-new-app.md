---
description: 您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。
keywords: mobile
seo-description: 您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。
seo-title: 添加新应用程序
solution: Marketing Cloud,Analytics
title: 添加新应用程序
topic: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '709'
ht-degree: 100%

---


# 添加新应用程序{#add-a-new-app}

您可以使用此信息完成以下操作：创建新应用程序并配置其关键量度；配置 Adobe Analytics、 和 Adobe Audience Manager 的 SDK 选项；配置客户获取和 ID 服务选项；以及下载配置文件、SDK 和开发人员及测试人员工具。

以下说明将帮助您添加新应用程序，并配置 Adobe Analytics 和 Adobe Audience Manager 的集成。

您必须先在 Adobe Mobile Services 用户界面中添加应用程序，然后才能对其进行配置。创建应用程序之后，系统会生成正确的配置文件，您可以将它提供给正为应用程序实施 Mobile SDK 的开发人员。

1. 登录到 Adobe Mobile Services，然后完成以下任务之一：

   * 单击&#x200B;**[!UICONTROL 新建]**&#x200B;以创建一个应用程序。
   * 要添加其他应用程序，请单击左侧导航菜单中的“管理应用程序”，然后单击&#x200B;**[!UICONTROL 添加]**。

      有关登录的更多信息，请参阅[登录](/help/using/gs/gs-signin.md)。

      >[!TIP]
      >
      >要管理现有的应用程序，请单击左侧导航菜单中的“管理应用程序”，然后单击要修改的应用程序。您可以在“应用程序信息”页面上进行更改。

1. 在以下字段中键入相应信息：

   **[!UICONTROL 报表包]**

   指定将在 Adobe Analytics 中收集和存储报表数据的报表包。每个应用程序都与一个 Analytics 报表包相连接。如果您将应用程序数据发送到多个报表包，请为每个报表包添加一个新应用程序。每个应用程序都与一个 Analytics 报表包相连接。如果您将应用程序数据发送到多个报表包，请为每个报表包添加一个新应用程序。

   如果您在 Adobe Mobile 中获得了 Analytics 管理员权限，则可以在 Adobe Mobile 中创建新的报表包。要新建报表包，请选择&#x200B;**[!UICONTROL 新建报表包]**，然后在以下字段中键入相应信息：

   * **[!UICONTROL 报表包 ID]**

      此 ID 可唯一标识 Adobe Analytics 中的报表包。您的公司前缀会自动添加到 ID 的开头处。

   * **[!UICONTROL 从以下来源复制设置]**

      变量、事件、处理规则及其他设置在新报表包中的设置情况与此报表包中完全一致。只有在使用的&#x200B;**[!UICONTROL 从以下来源复制设置]**&#x200B;报表包是移动设备应用程序模板时，或者只有在您创建的是启用离线功能的报表包时，“Mobile Services”中创建的报表包才会启用离线功能（含时间戳）。

   * **[!UICONTROL 时区]**

      所有报表日期都在此时区内。此设置会尝试使用与您的浏览器所用时区接近的时区。

   * **[!UICONTROL 货币]**

      将按此类货币对收入进行跟踪和报告。
   >[!TIP]
   >
   >要使用虚拟报表包 (VRS)，请参阅[虚拟报表包](/help/using/manage-apps/c-mob-vrs.md)。

   * **[!UICONTROL 图标]**

      （**可选**）要浏览并为您的应用程序选择图标，请单击&#x200B;**[!UICONTROL 图标]**。

   * **[!UICONTROL 名称]**

      （**可选**）为应用程序键入一个描述性名称。此名称可帮助您快速找到应用程序，而且有意义的名称还可帮助您快速了解应用程序的用途和设置。

   * **[!UICONTROL 类型]**

      从下拉列表中选择一种类型。左侧导航菜单中显示的可用报表，因您选择的应用程序类型而异。

      下面显示了可用的类型：

      * **[!UICONTROL 标准]**

         您可以保留已为大多数应用程序选择的&#x200B;**[!UICONTROL 标准]**&#x200B;选项。

      * **[!UICONTROL 出版物]**

         如果您的应用程序是使用 Adobe Digital Publishing Suite 创建的，则可以选择此选项。

      * **[!UICONTROL 游戏]**

         此选项类似于&#x200B;**[!UICONTROL 标准]**&#x200B;选项，但存在一个不同之处，即&#x200B;**[!UICONTROL 游戏]**&#x200B;选项会将报表中使用的术语更新为游戏术语。例如，用户将更改为玩家。对于游戏应用程序，会自动显示特定于游戏的报表。
   * **[!UICONTROL 描述]**

      （**可选**）键入应用程序的描述。



1. 单击&#x200B;**[!UICONTROL 保存]**&#x200B;以添加新应用程序。

   添加应用程序后，您可以查看“应用程序信息”页面，了解有关配置其他选项的信息。有关更多信息，请参阅[管理应用程序设置](/help/using/c-manage-app-settings/c-manage-app-settings.md)。
