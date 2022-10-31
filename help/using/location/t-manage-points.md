---
description: 您可以创建并管理目标点，通过目标点，您可以定义用于关联的地理位置，还可以使用应用程序内消息确定目标，等等。当在某个目标点中发送点击时，该目标点会附加到该点击。
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 管理目标点
topic-fix: Metrics
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
exl-id: 9598b06b-fb6a-436c-811c-f74015cc2ab0
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---

# 管理目标点 {#manage-points-of-interest}

{#eol}

您可以创建并管理目标点 (POI)，通过 POI，您可以定义用于关联的地理位置，还可以使用应用程序内消息确定目标，等等。在 POI 中发送点击时，POI 将会附加到该点击中。

在使用“位置”之前，请验证是否满足以下要求：

* 您必须拥有 Analytics—Mobile Apps 或 Analytics Premium。
* 您必须为应用程序启用&#x200B;**[!UICONTROL 位置报表]**。
* 如果您使用的是低于 4.2 版本的 iOS SDK 或 Android SDK，则您在添加新的&#x200B;**[!UICONTROL 目标点]**&#x200B;之后，必须下载新的配置文件，并将其提供给您的应用程序开发人员。

   如果您使用的是 4.2 或更高版本的 iOS SDK 或 Android SDK，则不需要将应用程序更新提交到应用商店，即可更新您的&#x200B;**[!UICONTROL 目标点]**。在“管理目标点”页面上，当您单击&#x200B;**[!UICONTROL 保存]**&#x200B;之后，相应更改会打包到&#x200B;**[!UICONTROL 目标点]**&#x200B;列表，并且活动应用程序的配置文件会进行更新。执行保存操作还会更新用户设备上应用程序中的点列表，只要该应用程序使用的是更新的 SDK 并配置了远程 POI URL。

在用户的设备上，对于要分配到&#x200B;**[!UICONTROL 目标点]**&#x200B;的点击，必须为应用程序启用位置。

要使用“位置”，请完成以下任务：

1. 单击应用程序的名称，以转到其“管理应用程序设置”页面。
1. 单击&#x200B;**[!UICONTROL 位置]** > **[!UICONTROL 管理目标点]**。

   ![步骤结果](assets/poi.png)

1. 在以下每个字段中键入信息：

   * **[!UICONTROL 点名称]**

      键入&#x200B;**[!UICONTROL 目标点]**&#x200B;名称。

      它可以是某城市、国家或地区的名称。您还可以创建特定位置（例如体育场馆或企业）周围的&#x200B;**[!UICONTROL 目标点]**。

   * **[!UICONTROL 纬度]**

      键入&#x200B;**[!UICONTROL 目标点]**&#x200B;的纬度。您可以从其他来源查找此信息，如 Internet。

   * **[!UICONTROL 经度]**

      键入&#x200B;**[!UICONTROL 目标点]**&#x200B;的经度。您可以从其他来源查找此信息，如 Internet。

   * **[!UICONTROL 半径（米）]**

      键入要包含的&#x200B;**[!UICONTROL 目标点]**&#x200B;周围区域的半径（以米为单位）。例如，如果您为科罗拉多的丹佛创建一个目标点，则可以指定一个大到足以包含丹佛市及其周边地区（但不包括科罗拉多的斯普林斯）的半径。

   * **[!UICONTROL 地图图标]**

      选择将显示在[概述](/help/using/location/c-location-overview.md)报表和[地图](/help/using/location/c-map-points.md)报表中的图标。

1. 根据需要添加其他 POI。

   我们建议，添加的 POI 不超过 5,000 个。如果您添加的目标点超过 5000 个，您可以保存这些点，但是您将收到警告消息，提醒您最佳实践提出的要求是添加 5000 个以下的目标点。

1. 单击&#x200B;**[!UICONTROL 保存]**。

要删除一个或多个目标点，请选中所需的复选框，然后单击&#x200B;**[!UICONTROL 删除选定项]**。

要使用 **[!UICONTROL 文件而不使用 Adobe Mobile 用户界面来处理数据，请单击]**&#x200B;导入&#x200B;**[!UICONTROL 或]**&#x200B;导出`.csv`。
