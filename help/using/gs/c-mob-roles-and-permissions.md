---
description: 在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。
seo-description: 在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。
seo-title: 角色和权限
title: 角色和权限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 59%

---


# 角色和权限{#roles-and-permissions}

在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。

## 概述 {#section_91B8192891E14E5285718C8118912500}

以下角色可管理 Mobile Services UI 中的权限：

### Analytics 管理员

Analytics 管理员可管理用户组和分配权限，其中一个是移动设备应用程序管理员。Experience Cloud管理员将您的Adobe ID链接到您的Adobe Analytics帐户，这允许您使用Adobe ID登录Mobile Services UI。 有关 Experience Cloud 管理员的更多信息，请参阅[管理 - 用户管理和常见问题解答](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!TIP]
>
>现有的 Analytics 管理员可以将 Analytics 管理员角色分配给任何用户。

有关此角色的更多信息，请参阅以下内容：

* [用户管理概述](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/user-product-management/user-management/users.html)

* [用户和群组权限更改](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/user-product-management/user-management/permissions-changes.html)

### 移动设备应用程序管理员

此角色是 Mobile Services UI 的管理员。

>[!IMPORTANT]
>
>对于某些功能（例如推送消息），Analytics 管理员必须选中“用户管理”中的&#x200B;**[!UICONTROL 区段创建]**&#x200B;复选框。

## 管理访问权限 {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是有关访问 Mobile Services UI 中选项的其他信息：

### 应用程序和报表包

所有Mobile Service应用程序都绑定到报表包。 如果用户无权访问报表包，则他们将无权访问该报表包的关联应用程序。

### Mobile Services 和 Analytics 功能

如果贵公司没有访问 UI 中功能（例如推送消息）的 Analytics 合同，则无论权限等级如何，贵公司中的任何用户都将无权访问该功能。

## 角色和权限 {#section_20AA029D5B8C413C8659777E79B11620}

以下是 Mobile Services UI 中的角色及其相关权限：

### Analytics 管理员

* 所有用户和移动设备应用程序管理员权限
* 使用新报表包创建应用程序
* 从Mobile Services中删除应用程序

   >[!IMPORTANT]
   >
   >虽然该应用程序已从 Mobile Services UI 中删除，但该报表包仍存在于 Analytics 中。

* 管理应用程序设置

   * 启用生命周期报告
   * 启用位置报告
   * 创建／更新／删除变量和指标

### 移动设备应用程序管理员

* 所有用户权限
* 使用现有报表包创建应用程序
* 管理应用程序设置

   * 配置应用程序的移动SDK选项
   * 配置应用程序的UI设置
   * 配置链接的App Store应用程序
   * 配置应用程序的通用链接选项
   * 配置推送服务证书和API密钥
   * 创建／更新／激活／取消激活/重复/存档／删除回传
   * 创建／更新／存档／删除链接目标

* 创建／更新／存档营销链接
* 创建／导入／更新／删除旧版客户获取链接
* 创建／导入／更新／删除地点（兴趣点）配置
* 创建／更新／发送/计划/取消/重复/存档／删除推送消息
* 创建／更新／激活／取消激活/重复/存档／删除应用程序内消息

有关组和用户的详细信息，请参阅：

* [用户组设置](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/user-product-management/user-groups/groups.html)
* [将用户添加到群组](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services 用户

此角色具有仅视图权限，并可在Mobile Services UI中提供反馈。

* 提供Mobile Services UI的反馈
* 视图应用程序

   >[!IMPORTANT]
   >
   >用户只能在 Adobe Analytics 中查看他们有权访问的报表包。

* 视图应用程序设置

   * 下载应用程序SDK配置
   * 视图所有UI和SDK设置
   * 视图变量和度量配置
   * 视图回传
   * 视图链接目标

* 查看和运行报表
* 查看营销链接
* 视图和导出旧版客户获取链接
* 视图和导出地点（目标点）配置
* 视图推送消息
* 视图应用程序内消息
