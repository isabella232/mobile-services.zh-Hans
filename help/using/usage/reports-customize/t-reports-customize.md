---
description: 此信息可帮助您通过添加其他过滤器（区段）来自定义内置报表。
keywords: mobile
seo-description: 此信息可帮助您通过添加其他过滤器（区段）来自定义内置报表。
seo-title: 将过滤器添加到报表
solution: Marketing Cloud，Analytics
title: 将过滤器添加到报表
topic: 报表,量度
uuid: 19c395cc-2e07-4588-825b-f2 f8 b10 a87 c1
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Add filters to reports{#add-filters-to-reports}

此信息可帮助您通过添加其他过滤器（区段）来自定义内置报表。

>[!IMPORTANT]
>
>营销报告和分析、专门分析、数据仓库和其他Analytics报告界面也提供移动应用程序指标。如果某个划分或报表类型在 Adobe Mobile 中不可用，则它可能是使用其他报表界面生成的。

在本示例中，我们将自定义“**[!UICONTROL 用户和会话]”报表，但相关说明适用于任何报表。**

1. Open your app and click **[!UICONTROL Usage]** &gt; **[!UICONTROL Users &amp; Sessions]**.

   ![](assets/customize1.png)

   此报表提供了我们的应用程序用户在特定时段内的完整概况。但是，此应用程序的 iOS 和 Android 版本的量度都是在同一报表包中收集的。通过将自定义过滤器添加到用户量度，我们便可以按移动设备操作系统来划分用户。

1. Click **[!UICONTROL Customize]**.

   ![](assets/customize2.png)

1. Under **[!UICONTROL Users]**, click **[!UICONTROL Add Filter]** and click **[!UICONTROL Add Rule]**.

1. Select **[!UICONTROL Operating Systems]**, and from the drop-down list, and select **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   要将Android添加为过滤器，您需要重复此步骤。

1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL Android]**.

   您的过滤器现在应当类似于以下示例：

   ![](assets/customize4.png)

1. Click **[!UICONTROL Update]**.
1. To regenerate the report, click **[!UICONTROL Run]**.

   现在，报表会显示按操作系统划分的用户。我们对报表标题进行了更改，以匹配应用于此报表的过滤器。

   ![](assets/customize5.png)

   您可以对此报告进行自定义。在iOS8.3中，您可以添加包含iOS8.3操作系统版本过滤器的第一个启动项量度，以查看有多少iOS8.3客户升级其应用程序并执行首次启动。
1. Under **[!UICONTROL First Launches]**, click **[!UICONTROL Add Filter]**, click **[!UICONTROL Add Rule]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL iOS]**.
1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating System Versions]** from the drop-down list, and select **[!UICONTROL iOS 8.3]**.

   您的过滤器现在应当类似于以下示例：

   ![](assets/customize6.png)

1. Click **[!UICONTROL Update]** and **[!UICONTROL Run]**.

   此报表当前会显示首次启动该应用程序的 iOS 8.3 用户数。

   ![](assets/customize7.png)

   请花些时间对报表自定义菜单中的各个选项进行测试，并确保为您最喜爱的项目添加书签。Adobe Mobile中的报告URL可正常使用，可通过电子邮件发送或添加到收藏夹中。
