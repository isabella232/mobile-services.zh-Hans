---
description: 在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。
title: 角色和权限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# 角色和权限{#roles-and-permissions}

在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。

## 概述 {#section_91B8192891E14E5285718C8118912500}

以下角色可管理 Mobile Services UI 中的权限：

### Analytics 管理员

Analytics 管理员可管理用户组和分配权限，其中一个是移动设备应用程序管理员。The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=zh-Hans)

>[!TIP]
>
>现有的 Analytics 管理员可以将 Analytics 管理员角色分配给任何用户。

### 移动设备应用程序管理员

此角色是 Mobile Services UI 的管理员。

>[!IMPORTANT]
>
>对于某些功能（例如推送消息），Analytics 管理员必须选中“用户管理”中的&#x200B;**[!UICONTROL 区段创建]**&#x200B;复选框。

## 管理访问权限 {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是有关访问 Mobile Services UI 中选项的其他信息：

### 应用程序和报表包

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Mobile Services 和 Analytics 功能

如果贵公司没有访问 UI 中功能（例如推送消息）的 Analytics 合同，则无论权限等级如何，贵公司中的任何用户都将无权访问该功能。

## 角色和权限 {#section_20AA029D5B8C413C8659777E79B11620}

以下是 Mobile Services UI 中的角色及其相关权限：

### Analytics 管理员 permissions

* 所有用户和移动设备应用程序管理员权限
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >虽然该应用程序已从 Mobile Services UI 中删除，但该报表包仍存在于 Analytics 中。

* 管理应用程序设置

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### 移动设备应用程序管理员 permissions

* All User Permissions
* Create App with existing report suite
* 管理应用程序设置

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=zh-Hans)
* [将用户添加到群组](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services 用户

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >用户只能在 Adobe Analytics 中查看他们有权访问的报表包。

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* 查看和运行报表
* 查看营销链接
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
