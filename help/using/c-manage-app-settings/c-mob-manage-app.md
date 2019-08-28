---
description: 您可以通过配置各种变量和量度来跟踪和管理从应用程序收到的数据。
keywords: mobile
seo-description: 您可以通过配置各种变量和量度来跟踪和管理从应用程序收到的数据。
seo-title: 管理您的应用程序
solution: Marketing Cloud，Analytics
title: 管理您的应用程序
topic: 量度
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 管理您的应用程序 {#managing-your-app}

您可以通过配置各种变量和量度来跟踪和管理从应用程序收到的数据。

## 管理变量和量度 {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **“标准变量和量度”**

   每个应用程序都包含用于跟踪购物车和购买活动的变量和量度。Some purchase information cannot be handled with processing rules, so the SDK exposes the special `"&&products"` context data. 例如，您可以使用诸如购物车加货、购物车减货、结账、订购等变量。上下文数据必须映射到 Adobe Analytics 中的数据。如果该变量填充了一个来自上下文数据的简单映射，则它是映射到此变量的键。如果变量由Analytics Admin Tools中更复杂的规则填充，则将其保留为空。

   有关这些变量和量度的更多信息，请参阅以下内容：

   * [Android中的产品变量](/help/android/analytics-main/products/products.md)
   * [iOS中的产品变量](/help/ios/analytics-main/products/products.md)

* **自定义变量**

   “自定义变量”页面会显示针对包含您的应用程序数据的报表包配置的所有自定义 Analytics 变量。在此页面中，您可以启用其他变量，并将上下文数据映射到 Analytics 变量。

### 将上下文数据映射到 Analytics 变量

Click **[!UICONTROL Manage App Settings]** &gt; **[!UICONTROL Manage Variables &amp; Metrics]** &gt; **[!UICONTROL Custom Variables]**.

These mappings call the same API that is used in [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![上下文数据映射](assets/custom_data_content.png)

以下是您可以配置的自定义变量列表：

* **[!UICONTROL “自定义属性]** ”(或props)回答问题“哪一个？”Prop 可以设置为将要与同一次点击中发送的其他变量和量度相关联的文本值。该值可用于过滤报表，也可以按关联的量度以排名顺序列出。

   在为跟踪调用（或命中）中的属性设置值时，它仅适用于此调用。

* **[!UICONTROL 自定义变量]** (或evar)还回答问题“哪一个？”但是，evar 值不仅应用于发送该变量的点击，还会应用于于随后的点击中发送的变量和量度，直至该值到期或设置了新值为止。
* **[!UICONTROL 自定义列表变量(或多值变量)]** 的行为与变量相同，但允许您在一次点击时捕获多个值。有关详细信息，请参阅 [列表变量](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html)。

Analytics中的以下映射在Mobile Services中创建。

* **[!UICONTROL 名称]**

   数据收集变量的易记名称。

* **[!UICONTROL 上下文数据]**

   如果该变量填充了一个来自上下文数据的简单映射，则它是映射到此变量的键。如果变量由 Analytics 管理工具中更为复杂的规则填充，则将此字段保留为空。

   在上下文数据列中单击并选择希望映射的上下文数据变量。下拉列表中包含在过去 30 天中收到的变量，因此如果您要映射的上下文数据不在此列表中，则可以手动键入它。

* **[!UICONTROL 持久性(自定义变量和自定义列表变量)]**

   持久性决定自定义变量 (eVar) 值将过期或不再与其他点击相关联的时间。如果某个 eVar 在点击触发时过期，那么将无值与该 eVar 的点击相关联。这意味着触发点击时没有任何 eVar 值处于活动状态。

   您可以选择以下选项之一：

   * **[!UICONTROL 会话]**

      eVar值一直存在于Analytics访问的长度。

   * **[!UICONTROL 跟踪调用]**

      eVar值仅保留跟踪调用或点击其中包含的值。

   * **[!UICONTROL 永不过期]**

      eVar值保留所有后续跟踪调用。
   * **[!UICONTROL 高级]**

      Adobe Analytics 拥有更高级的 UI 可用于设置 eVar 持久性。如果为Mobile Services不支持的eVar设置持久值，则此值将显示在Mobile Services UI中。

      To manage eVars, click **[!UICONTROL Adobe Analytics Report Suite Manager]** &gt; **[!UICONTROL Conversion Variables UI]**.

   * **[!UICONTROL 列表支持]**

      允许在一次跟踪调用中通过多个值与属性相关联。分隔符必须为一个字符，不能为零或空格。

   * **[!UICONTROL Delimiter（分隔符）]**

      分隔符必须为一个字符，不能为零或空格。

### 其他 Analytics 变量

您可以使用位于每个变量部分底部的下拉列表来启用其他变量。

![添加变量](assets/add_variable.png)

选择一个未使用的变量数字，并键入一个名称。此外，您还可以提供您要存储的上下文数据变量，以及任何其他信息。

* **自定义量度**

   量度(或事件)回答问题 *有多少？**或多少？*。事件可以在每次用户执行操作或者持有数字值（例如价格）时递增。自定义量度包括以下事件：已创建应用程序、已下载或导出 PDF 或 CSV 文件、已保存促销活动、已下载 SDK、已运行报表、已添加指向应用商店的链接、已激活应用程序内消息，等等。

   选择以下自定义量度类型之一：

   * **[!UICONTROL 整数]**
   * **[!UICONTROL 小数]**
   * **[!UICONTROL 货币]**

## 管理目标点 {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

兴趣点允许您定义可用于关联用途、使用应用程序内消息等的地理位置。在目标点中发送一个点击之后，该目标点会附加到该点击上。有关目标点的更多信息，请参阅 [管理目标点](/help/using/location/t-manage-points.md).

## 管理链接目标 {#section_F722A387E22A430187B063D358A87711}

您可以创建、编辑、存档/取消存档和删除链接目标。在构建营销链接、推送通知或应用程序内消息时，可以在行中调用这些目标。有关链接目标的详细信息，请参阅 [管理链接目标](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md)。

## 管理回发 {#section_78B0A8D7AE6940E78D85AE3AB829E860}

回发允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 Mobile 以将自定义数据发送至第三方目的地。有关回发的更多信息，请参阅[配置回发](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md)。
