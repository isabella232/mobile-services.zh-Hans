---
description: 您可以创建或编辑营销链接，以提供到移动设备应用程序或网站的深层链接。
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 创建或编辑营销链接
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 96%

---

# 创建或编辑营销链接{#create-or-edit-marketing-links}

您可以创建或编辑营销链接，以提供到移动设备应用程序或网站的深层链接。有关更多信息，请参阅 [Apple 通用链接和 Android 应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. 在应用程序的左侧导航窗格中，展开&#x200B;**[!UICONTROL 客户获取]**，然后单击&#x200B;**[!UICONTROL 营销链接生成器]**。
1. 完成以下任务之一：

   * 要创建营销链接，请单击&#x200B;**[!UICONTROL 新建]**。
   * 要编辑某个链接，请在&#x200B;**[!UICONTROL 标题]**&#x200B;列中单击此链接的名称。

1. 在以下字段中键入相应信息：

   * **[!UICONTROL 营销链接名称]**：

      （**必需**）为您的营销链接指定一个描述性名称。此名称仅在 Adobe Mobile Services UI 中的“营销链接”页面上显示。描述性的名称可帮助您或您组织内的其他人快速找到特定的链接并可对其用途提供深入分析。

   * **[!UICONTROL 唯一跟踪代码]**：

      （**必需**）指定所需的跟踪代码，或单击 ![生成图标](assets/icon_generate.png) 以创建新的跟踪代码。您可以查看报表以了解跟踪代码的详细使用情况。

   * **[!UICONTROL 添加跟踪上下文数据]**：

      （**可选**）单击 **[!UICONTROL +]** 图标，然后键入相关信息以使用上下文数据跟踪您的促销活动。在&#x200B;**[!UICONTROL 自定义上下文数据]**&#x200B;下拉列表中，选择一个预设标记或一个您自己的标记。上下文数据用于报告营销链接在何时部署。

      可用的预设标记如下：

      * **自定义上下文数据**
指定键和值。如果您添加自定义上下文数据，则必须创建一个处理规则。有关更多信息，请参阅 [处理规则概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) (在Adobe Analytics文档中)。

      * **来源**
指定原始反向链接，如“商务通讯”或“主页”。

      * **媒介**
指定营销媒介，如“横幅广告”或“电子邮件”。

      * **内容**
指定带有链接的广告的名称或 ID。

      * **搜索词**
指定广告的付费关键词或其他搜索词。
1. 单击&#x200B;**[!UICONTROL 保存]**。
1. 在以下字段中键入相应信息：

   * **（必需）**&#x200B;在&#x200B;**[!UICONTROL 回退 URL]** 中，指定当目标无法匹配时（例如，如果用户在不匹配目标规则的桌面或其他平台上），用户会被定向到的 URL。
   * 在&#x200B;**[!UICONTROL 营销链接选项]**&#x200B;中，选择&#x200B;**[!UICONTROL 插播式广告]**&#x200B;或&#x200B;**[!UICONTROL 通用链接和应用程序链接]**。

      有关更多信息，请参阅[插播式广告](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)或 [Apple 通用链接和 Android 应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

   * **（有条件）**&#x200B;如果已选择&#x200B;**[!UICONTROL 通用链接或应用程序链接]**，则在&#x200B;**[!UICONTROL 自定义路径]**&#x200B;中，用户可以使用任何查询参数在域后面定义 URL 路径。有关更多信息，请参阅 [Apple 通用链接和 Android 应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. 单击&#x200B;**[!UICONTROL 编辑深层链接插播式广告]**，然后配置此链接。

   （**可选**）如果存在多个目标，可以根据用户是否已安装移动设备应用程序将其路由到相应目标。如果安装了应用程序，则会显示插播式广告登陆页面。

   有关更多信息，请参阅[插播式广告](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)。

1. 单击&#x200B;**[!UICONTROL 保存]**，然后单击&#x200B;**[!UICONTROL 下一步]**。
1. 在“目标”页面中，配置链接。

   1. 单击&#x200B;**[!UICONTROL 决策]**&#x200B;图标 (![决策图标](assets/icon_decision.png))，然后选择以下决策位置之一：

      * **[!UICONTROL 添加决策]**
      * **[!UICONTROL 添加路径]**
   1. 如果已选择&#x200B;**[!UICONTROL 添加决策]**，请选择以下决策类型之一：

      * **[!UICONTROL 操作决策]**

         受支持的操作系统包括 iOS、Android、AMX 等等。

      * **[!UICONTROL 设备类型]**

         设备类型包括台式机、电子阅读器、游戏机、手机、机顶盒等设备。
   1. 单击&#x200B;**[!UICONTROL 目标]**&#x200B;图标 (![正方形图标](assets/icon_square.png))，然后选择以下目标类型之一：

      * **[!UICONTROL 应用商店]**
      * **[!UICONTROL Web 链接]**
      * **[!UICONTROL 应用程序深层链接]**
      * **[!UICONTROL 混合链接]**

      >[!TIP]
      >
      >如果您使用 **[!UICONTROL Web 链接]**&#x200B;目标类型，并将链接指向应用商店，则不会跟踪客户获取。要跟踪客户获取，请使用&#x200B;**[!UICONTROL 应用商店]**&#x200B;目标类型。

      有关更多信息，请参阅[创建新链接目标](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)。




1. 要保存营销链接，请单击 ![省略号](assets/icon_elipses.png)，然后单击&#x200B;**[!UICONTROL 保存]**。
