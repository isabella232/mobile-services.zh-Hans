---
description: 在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。
title: 角色和权限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f6a62a46a90c30edaf999085873bf21f2a03a68e
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 48%

---

# 角色和权限{#roles-and-permissions}

在 Adobe Analytics 中，您可以在“管理工具主页”页面上管理角色。

## 概述 {#section_91B8192891E14E5285718C8118912500}

以下角色可管理 Mobile Services UI 中的权限：

### Analytics 管理员

Analytics 管理员可管理用户组和分配权限，其中一个是移动设备应用程序管理员。Experience Cloud管理员将您的Adobe ID关联到您的Adobe Analytics帐户，这允许您使用Adobe ID登录到Mobile Services UI。 有关Experience Cloud管理员的详细信息，请参阅 [管理Experience Cloud用户和产品](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) 中的Experience Cloud中心界面组件指南。

>[!TIP]
>
>现有的 Analytics 管理员可以将 Analytics 管理员角色分配给任何用户。

有关此角色的更多信息，请参阅Adobe Analytics文档中的以下内容：

* [用户管理概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=zh-Hans)
* [用户和群组权限更改](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### 移动设备应用程序管理员

此角色是 Mobile Services UI 的管理员。

>[!IMPORTANT]
>
>对于某些功能（例如推送消息），Analytics 管理员必须选中“用户管理”中的&#x200B;**[!UICONTROL 区段创建]**&#x200B;复选框。

## 管理访问权限 {#section_E6939C2695AA4A0DBF432D50B2670920}

以下是有关访问 Mobile Services UI 中选项的其他信息：

### 应用程序和报表包

所有Mobile Service应用程序都与报表包绑定。 如果用户无权访问报表包，则他们将无权访问该报表包的关联应用程序。

### Mobile Services 和 Analytics 功能

如果贵公司没有访问 UI 中功能（例如推送消息）的 Analytics 合同，则无论权限等级如何，贵公司中的任何用户都将无权访问该功能。

## 角色和权限 {#section_20AA029D5B8C413C8659777E79B11620}

以下是 Mobile Services UI 中的角色及其相关权限：

### Analytics 管理员 权限

* 所有用户和移动设备应用程序管理员权限
* 使用新报表包创建应用程序
* 从Mobile Services中删除应用程序

   >[!IMPORTANT]
   >
   >虽然该应用程序已从 Mobile Services UI 中删除，但该报表包仍存在于 Analytics 中。

* 管理应用程序设置

   * 启用生命周期报告
   * 启用位置报表
   * 创建/更新/删除变量和量度

### 移动设备应用程序管理员 权限

* 所有用户权限
* 使用现有报表包创建应用程序
* 管理应用程序设置

   * 配置应用程序的Mobile SDK选项
   * 配置应用程序的UI设置
   * 配置链接的App Store应用程序
   * 配置应用程序的通用链接选项
   * 配置推送服务证书和API密钥
   * 创建/更新/激活/停用/复制/存档/删除回发
   * 创建/更新/存档/删除链接目标

* 创建/更新/存档营销链接
* 创建/导入/更新/删除旧版客户获取链接
* 创建/导入/更新/删除位置（目标点）配置
* 创建/更新/发送/计划/取消/复制/存档/删除推送消息
* 创建/更新/激活/停用/复制/存档/删除应用程序内消息

有关组和用户的更多信息，请参阅Adobe Analytics文档中的以下内容：

* [用户组设置（旧版）](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)
* [将用户添加到群组](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services 用户

此角色具有仅查看权限，并可在Mobile Services UI中提供反馈。

* 提供有关Mobile Services UI的反馈
* 查看应用程序

   >[!IMPORTANT]
   >
   >用户只能在 Adobe Analytics 中查看他们有权访问的报表包。

* 查看应用程序设置

   * 下载应用程序SDK配置
   * 查看所有UI和SDK设置
   * 查看变量和量度配置
   * 查看回发
   * 查看链接目标

* 查看和运行报表
* 查看营销链接
* 查看和导出旧版客户获取链接
* 查看和导出位置（目标点）配置
* 查看推送消息
* 查看应用程序内消息
