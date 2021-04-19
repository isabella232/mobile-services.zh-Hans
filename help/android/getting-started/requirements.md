---
description: '在配置报表包并收集 Android 应用程序数据之前，请完成以下先决任务 '
seo-description: '在配置报表包并收集 Android 应用程序数据之前，请完成以下先决任务 '
seo-title: 开始之前
solution: Experience Cloud,Analytics
title: 开始之前
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 100%

---

# 开始之前 {#before-you-start}

在配置报表包并收集 Android 应用程序数据之前，请完成以下先决任务：

## 特定于角色的任务 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理员和应用程序开发人员必须完成以下任务：

### Analytics 管理员

要配置报表包并收集移动设备应用程序数据，请执行以下操作：

1. 完成[登录 Adobe Mobile Services UI](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) 中的任一部分。
1. 为每个应用程序开发人员创建一个 Analytics 帐户。

应用程序开发人员现在将有权查看您创建的报表包。

>[!IMPORTANT]
>
>要创建新的报表包并下载 SDK，您必须是 Analytics 管理员。

### 应用程序开发人员

1. 确保 Analytics 管理员已完成&#x200B;*特定于角色的任务*&#x200B;中的“Analytics 管理员”[](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)的步骤。
1. 确认 Analytics 管理员已完成[登录到 Adobe Mobile Services 用户界面](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)中的某一部分。
1. 配置报表包后，完成[下载 SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46) 中的步骤。

有关角色和权限的更多信息，请参阅[角色和权限](/help/using/gs/c-mob-roles-and-permissions.md)。

## 登录 Adobe Mobile Services UI {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services 是用于移动设备应用程序分析和定位的主要报告界面。完成这些步骤后，您可以下载一个配置文件，该文件已预先配置了数据收集服务器、报表包和许多其他设置。

您可以通过以下某种方式登录 Adobe Mobile Services UI：

### Experience Cloud

使用您的 Adobe ID 登录到 [Experience Cloud](https://experiencecloud.adobe.com)。此方法假定您的公司已在 Experience Cloud 中进行配置，并且您已经关联 Analytics 帐户。有关更多信息，请参阅[管理 Experience Cloud 用户和产品](https://docs.adobe.com/content/help/zh-Hans/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!TIP]
>
>如果不确定您的公司是否已在 Experience Cloud 中进行配置，请使用现有的 Adobe Analytics 帐户。

### Adobe Analytics

单击&#x200B;**[!UICONTROL 使用 Analytics 登录]**&#x200B;并输入您的 Analytics 公司名称、用户名和密码。

## 创建报表包 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

要创建报表包以收集应用程序数据并定义应用程序，请执行以下操作：

1. 在浏览器中键入 [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) 以登录 Mobile Services UI。
1. 单击&#x200B;**[!UICONTROL 创建应用程序]**。

   如果未看到此按钮，请单击&#x200B;**[!UICONTROL 管理应用程序]** > **[!UICONTROL 添加]**。

1. 在&#x200B;**[!UICONTROL 报表包]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 新的报表包]**。

1. 输入应用程序的名称并选择一种报表包类型。

   例如，报表包 ID 为 `mycomobileappdev`。由于您需要为开发版本和生产版本分别设置不同的报表包和应用程序，因此在准备好设置生产版本时，可以重复这些步骤。
1. 在&#x200B;**[!UICONTROL 报表包 ID]** 中，确认显示了您的报表包名称。
1. 在&#x200B;**[!UICONTROL 从以下来源复制设置]**&#x200B;中，确认已选中&#x200B;**[!UICONTROL 移动设备应用程序模板]**。

   此模板将启用时间戳以收集离线数据，并激活移动设备解决方案变量以捕获生命周期量度。

1. 选择您的时区和货币，然后单击&#x200B;**[!UICONTROL 保存]**。

## 下载 SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

要下载 Mobile SDK，请执行以下操作：

1. 在浏览器中键入 [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) 以登录 Mobile Services UI。
1. 在左窗格中，单击&#x200B;**[!UICONTROL 所有应用程序]**&#x200B;下拉列表，然后选择您的应用程序。您还可以在右侧窗格中选择您的应用程序。

   >[!IMPORTANT]
   >
   >要在右侧窗格中显示您的应用程序，您必须先创建应用程序。有关创建应用程序的信息，请参阅[添加新应用程序](https://docs.adobe.com/content/help/zh-Hans/mobile-services/using/manage-apps-ug/t-new-app.html)。

1. 在应用程序的左侧窗格中，单击&#x200B;**[!UICONTROL 管理应用程序设置]**。

   >[!IMPORTANT]
   >
   >如果看不到&#x200B;**[!UICONTROL 管理应用程序设置]**&#x200B;选项，请确保您已登录 Adobe Mobile Services。要进行验证，请单击页面右上方的![解决方案切换器](assets/solution-switcher.png)图标，并确保 **[!UICONTROL Adobe Mobile Services]** 显示在左上方。

1. 在“管理应用程序设置”页面底部的&#x200B;**[!UICONTROL 应用程序 SDK 下载]**&#x200B;部分中，下载适用于您平台的 SDK 和示例应用程序。

>[!TIP]
>
>您应用程序的配置文件会自动包含在 SDK 下载中，因此无需单独下载该文件。但是，如果您已经下载了 SDK，并且想要获取更新的设置，则需要再次下载配置文件。

如果您使用的是 Android Studio，则还可以将以下内容添加到应用程序的 `build.gradle` 文件中：

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

请牢记以下信息：

* 将代码示例中的版本号替换为 Android SDK 的相应版本。
* 下载配置文件并将其包含到您的项目中。
