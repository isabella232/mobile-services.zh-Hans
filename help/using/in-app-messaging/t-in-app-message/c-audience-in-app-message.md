---
description: 您可以为应用程序内消息配置受众选项，包括查看、触发器和特征选项。
keywords: mobile
seo-description: 您可以为应用程序内消息配置受众选项，包括查看、触发器和特征选项。
seo-title: 受众应用程序内消息
solution: Marketing Cloud，Analytics
title: 受众应用程序内消息
topic: 量度
uuid: 6c815d4c-7626-4cf4-9158-3f059c79317a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

您可以为应用程序内消息配置受众选项，包括查看、触发器和特征选项。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 在“受众”页面上的以下字段中键入相应信息：

   * **[!UICONTROL 查看]**

      选择触发消息显示的选项：

      * **[!UICONTROL 一直]**

         该选项表示每次触发都会显示消息。

      * **[!UICONTROL 一次]**

         该选项表示只有第一次触发才会显示消息。

      * **[!UICONTROL 点进之前]**

         该选项表示在用户点进之前，每次触发都会显示消息。此触发器仅适用于全屏消息和警告消息。大多数的消息需要重定向或使用 Internet 中的资源，且离线时不会显示。要始终显示消息而不考虑网络连接情况，请选中&#x200B;**[!UICONTROL 离线显示]复选框。**
   * **[!UICONTROL 触发器]**

      从下拉列表中选择一个选项，然后选择一个条件。例如，您可以从第一个下拉列表中选择&#x200B;**[!UICONTROL 已启动]**，从第二个下拉列表中选择&#x200B;**存在[!UICONTROL 。]**&#x200B;您还可以指定需要纳入显示消息的触发点击中的自定义上下文数据。

      >[!IMPORTANT]
      >
      >如果您选择多个触发器，则要显示要显示的消息，则必须在同一点击上发生所有触发器。

   * **[!UICONTROL 特征]**&#x200B;您可以确定在触发应用程序内消息时应看到的用户，并将受众过滤(区段)到具有指定数据的点击。例如，可以定义一个“目标点”包含“Denver”的规则。在消息触发时，此过滤器会将消息显示给姓名中含有目标点 Denver 的客户。



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>触发器和特征使用从应用程序传递到Analytics的数据。系统是将这些值作为上下文数据、已映射的变量和量度来传递的。变量是基于文本的值，而量度则是数值。

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL “标准变量和量度”]**
* **[!UICONTROL 自定义变量]**
* **[!UICONTROL 自定义量度]**

验证映射后，请选择恰当的匹配项或逻辑运算符，以配置消息的受众。

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![触发器选项](assets/custom_trigger_matcher_options.png)

以下场景可帮助您确定是选择指标还是变量作为触发器：

### 量度

量度是数字，例如购买数量便是一个量度。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. 在&#x200B;****&#x200B;受众]选项卡的&#x200B;**[!UICONTROL 触发器]部分，完成以下步骤：[!UICONTROL **

   1. Select a standard event such as **[!UICONTROL Launched]** and select **[!UICONTROL exists]**.
   1. 再选择一个属于自定义数据点且已映射到量度的触发器。
   1. Under **[!UICONTROL Number]**, select a matcher option.

### 变量

变量是用作唯一标识符的文本字符串，例如国家/地区、机场等都属于变量。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. 在&#x200B;****&#x200B;受众]选项卡的&#x200B;**[!UICONTROL 触发器]部分，完成以下步骤：[!UICONTROL **

   1. Select a standard event such as **[!UICONTROL Launched]** and select **[!UICONTROL exists]**.
   1. 再选择一个属于自定义数据点且已映射到变量的触发器。
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
