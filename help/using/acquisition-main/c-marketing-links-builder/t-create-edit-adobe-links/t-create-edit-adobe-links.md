---
description: 您可以创建或编辑营销链接，以深入链接移动应用程序或您的网站。
keywords: mobile
seo-description: 您可以创建或编辑营销链接，以深入链接移动应用程序或您的网站。
seo-title: 创建或编辑营销链接
solution: Marketing Cloud，Analytics
title: 创建或编辑营销链接
topic: 量度
uuid: 305a8265-38de-4d19-8c79-b3912 f5 aae7 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

您可以创建或编辑营销链接，以提供深层链接到移动应用程序或您的网站。有关详细信息，请参阅 [Apple Universal Links和Android应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. 完成以下任务之一：

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * 要编辑某个链接，请在&#x200B;**[!UICONTROL 标题]列中单击此链接的名称。**

1. 在以下字段中键入相应信息：

   * **[!UICONTROL 营销链接名称]**:

      (**Required**) Specify a descriptive name for your Marketing Link. 此名称仅在 Adobe Mobile Services UI 中的“营销链接”页面上显示。描述性的名称可帮助您或您组织内的其他人快速找到特定的链接并可对其用途提供深入分析。

   * **[!UICONTROL 唯一跟踪代码]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. 您可以查看报表以了解跟踪代码的详细使用情况。

   * **[!UICONTROL 添加跟踪上下文数据]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. 在&#x200B;**[!UICONTROL 自定义上下文数据]下拉列表中，选择一个预设标记或一个您自己的标记。**&#x200B;上下文数据用于在部署营销链接时进行报告。

      可用的预设标记如下：

      * **自定义上下文数据**&#x200B;指定密钥和值。如果您添加自定义上下文数据，则必须创建一个处理规则。有关详细信息，请参阅 [处理规则概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

      * **源**&#x200B;指定原始反向链接，如“新闻稿”或“主页”。

      * **Medium**&#x200B;指定营销媒介，如“横幅”或“电子邮件”。

      * **内容**&#x200B;使用链接指定广告的名称或ID。

      * **期限**&#x200B;指定广告的付费条款或其他搜索词。
1. 单击&#x200B;**[!UICONTROL 保存]**。
1. 在以下字段中键入相应信息：

   * **(必需)** 在 **[!UICONTROL 回退URL]**&#x200B;中，指定用户在目标无法匹配时转到的URL(例如，如果用户在桌面上或其他与目标规则不匹配的平台)。
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      有关更多信息，请参阅 [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) 或 [Apple Universal Links和Android应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

   * **(视情况而定)** 如果 **[!UICONTROL 选择了“通用”]** 或“应用程序链接”，则用户可以在 **[!UICONTROL “自定义路径]**”中，使用任何查询参数定义域之后的URL路径。有关详细信息，请参阅 [Apple Universal Links和Android应用程序链接](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)。

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. 如果已安装应用程序，则会显示一个插播式广告的登录页面。

   有关更多信息，请参阅 [间隙](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. 在“目标”页面中，配置链接。

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL 添加决策]**
      * **[!UICONTROL 添加路径]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL 操作决策]**

         受支持的操作系统包括 iOS、Android、AMX 等等。

      * **[!UICONTROL 设备类型]**

         设备类型包括台式机、电子阅读器、游戏机、手机、机顶盒等设备。
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL 应用商店]**
      * **[!UICONTROL Web 链接]**
      * **[!UICONTROL 应用程序深层链接]**
      * **[!UICONTROL 混合链接]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. 要跟踪客户获取信息，请使用&#x200B;**[!UICONTROL 应用商店]目标类型。**

      有关详细信息，请参阅 [创建新链接目标](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)。




1. 要保存营销链接，请单击 ![电子邮件，](assets/icon_elipses.png) 然后 **[!UICONTROL 单击保存]**。
