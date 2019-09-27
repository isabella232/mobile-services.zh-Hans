---
description: 在 Adobe Analytics 中，你可以在“管理工具主页”页面上管理角色。
seo-description: 在 Adobe Analytics 中，你可以在“管理工具主页”页面上管理角色。
seo-title: 角色和权限
title: 角色和权限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

在 Adobe Analytics 中，你可以在“管理工具主页”页面上管理角色。

## 概述 {#section_91B8192891E14E5285718C8118912500}

以下角色可管理 Mobile Services UI 中的权限：

### Analytics 管理员

Analytics 管理员可管理用户组和分配权限，其中一个是移动设备应用程序管理员。Experience Cloud 管理员将您的 Adobe ID 关联到您的 Adobe Analytics 帐户，这样您便可以使用 Adobe ID 登录到 Mobile Services UI。有关 Experience Cloud 管理员的更多信息，请参阅[管理 - 用户管理和常见问题解答](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!TIP]
>
>现有的Analytics管理员可以将Analytics管理员角色分配给任何用户。

有关此角色的更多信息，请参阅以下内容：

* [User management overview](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [用户和用户组权限更改](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### 移动应用程序管理员

此角色是 Mobile Services UI 的管理员。

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是有关访问 Mobile Services UI 中选项的其他信息：

### Apps and report suites

所有 Mobile Service 应用程序都与报表包绑定。如果用户无权访问报表包，则无法访问该报表包的关联应用程序。

### Mobile services和Analytics功能

如果贵公司没有访问 UI 中功能（例如推送消息）的 Analytics 合同，则无论权限等级如何，贵公司中的任何用户都将无权访问该功能。

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

以下是 Mobile Services UI 中的角色及其相关权限：

### Analytics 管理员

* 所有用户和移动应用程序管理员权限
* 使用新的报表包创建应用程序
* 从 Mobile Services 中删除应用程序

   >[!IMPORTANT]
   >
   >尽管应用程序已在Mobile Services UI中删除，但Analytics中仍存在报表包。

* 管理应用程序设置

   * 启用生命周期报告
   * 启用位置报告
   * 创建/更新/删除变量和量度

### 移动应用程序管理员

* 所有用户权限
* 使用现有的报表包创建应用程序
* 管理应用程序设置

   * 配置应用程序的 Mobile SDK 选项
   * 配置应用程序的 UI 设置
   * 配置已链接的应用商店应用程序
   * 配置应用程序的通用链接选项
   * 配置推送服务证书和 API 密钥
   * 创建/更新/激活/停用/复制/存档/删除回发
   * 创建/更新/存档/删除链接目标

* 创建/更新/存档营销链接
* 创建/导入/更新/删除旧版客户获取链接
* 创建/导入/更新/删除地点（目标点）配置
* 创建/更新/发送/计划/取消/复制/存档/删除推送消息
* 创建/更新/激活/停用/复制/存档/删除应用程序内消息

有关群组和用户的更多信息，请参阅：

* [User group settings](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [将用户添加到群组](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile services用户

该角色具有只查看权限，并可以在 Mobile Services UI 中提供反馈。

* 在 Mobile Services UI 中提供反馈
* 查看应用程序

   >[!IMPORTANT]
   >
   >用户只能在Adobe Analytics中查看其有权访问的报表包。

* 查看应用程序设置

   * 下载应用程序 SDK 配置
   * 查看所有 UI 和 SDK 设置
   * 查看变量和量度配置
   * 查看回发
   * 查看链接目标

* View and Run Reports
* 查看营销链接
* 查看和导出旧版客户获取链接
* 查看和导出地点（目标点）配置
* 查看推送消息
* 查看应用程序内消息
