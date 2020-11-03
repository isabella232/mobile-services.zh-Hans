---
description: 通用链接 (iOS) 和应用程序链接 (Android) 允许您连接到 iOS 或 Android 应用程序中的深层链接。
keywords: mobile
seo-description: 通用链接 (iOS) 和应用程序链接 (Android) 允许您连接到 iOS 或 Android 应用程序中的深层链接。
seo-title: Apple 通用链接和 Android 应用程序链接
solution: Experience Cloud,Analytics
title: Apple 通用链接和 Android 应用程序链接
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1142'
ht-degree: 100%

---


# Apple 通用链接和 Android 应用程序链接{#universal-links-and-app-links}

通用链接 (iOS) 和应用程序链接 (Android) 允许您连接到 iOS 或 Android 应用程序中的深层链接。

>[!IMPORTANT]
>
>从 iOS 9.2 开始，不支持深层链接。您必须使用 Apple 通用链接来提供到应用程序或网站的深层链接。

## 通用链接 {#section_F8147944679A42E59CF4FD8814E5EF12}

通用链接允许您连接到 iOS 应用程序中的深层链接，iOS 9.2 或更高版本支持此类链接。在访问通用链接时，iOS 会将该链接直接重定向到您的应用程序中的深层链接。如果未安装您的应用程序，则会在浏览器中打开您网站的 URL。有关通用链接的更多信息，请参阅[支持通用链接](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)。

## 应用程序链接

应用程序链接允许您连接到 Android 应用程序中的深层链接，Android 6.0 或更高版本支持此类链接。在访问应用程序链接时，Android 会将该链接直接重定向到您的应用程序中的深层链接。如果未安装您的应用程序，则会在浏览器中打开您网站的 URL。有关应用程序链接的更多信息，请参阅[处理 Android 应用程序链接](https://developer.android.com/training/app-links/index.html)。

## 使用通用链接或应用程序链接创建营销链接 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以创建使用通用链接或应用程序链接的营销链接。

### 配置通用链接

1. 要在 iOS 应用程序中设置通用链接，请转到 [Apple 的处理通用链接](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. 在 Adobe Mobile Services 中，设置网站关联文档：

   a. 在 Mobile Services 主页中，选择您要为其设置通用链接的应用程序。

   b. 单击&#x200B;**[!UICONTROL 管理应用程序设置]**。

   c. 确保在&#x200B;**[!UICONTROL 添加应用商店应用程序]**&#x200B;部分添加了可处理通用链接的 iOS 应用程序。

   >[!TIP]
   >
   >如果&#x200B;**[!UICONTROL 添加应用商店应用程序]**&#x200B;部分未显示，请单击&#x200B;**[!UICONTROL 添加应用商店应用程序]**&#x200B;链接。

   d. 在&#x200B;**[!UICONTROL 通用链接和应用程序链接选项]**&#x200B;部分，选择 iOS 应用程序并键入应用程序 ID。

   f. 单击&#x200B;**[!UICONTROL 保存]**。

   您必须至少提供一个 iOS 应用程序选择和一个应用程序 ID，否则您将收到错误。

   >[!IMPORTANT]
   >
   >您可以通过单击通用链接和应用程序链接选项部分中的“更新”来更新文档。但是，当您单击&#x200B;**[!UICONTROL 更新]**&#x200B;时，系统会发出警告，通知您以前创建的所有通用链接或应用程序链接都将受到影响。

### 使用通用链接

1. 在 Adobe Mobile Services 中，创建一个使用通用链接的营销链接：

   a. 从 Mobile Services 主页中选择应用程序，单击&#x200B;**[!UICONTROL 客户获取]** > **[!UICONTROL 营销链接生成器]**。

   b. 单击&#x200B;**[!UICONTROL 新建]**。

   c. 在&#x200B;**[!UICONTROL 营销链接选项]**&#x200B;下，选择&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**。

   d. 如果您在上面的&#x200B;*在 Adobe Mobile Services 中设置网站关联文档*&#x200B;部分中配置了网站关联文档，则默认情况下会选中此选项。

   如果未配置文档，则&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**&#x200B;选项会处于禁用状态，并且默认情况下会选中&#x200B;**[!UICONTROL 使用插播式广告]**。

   e. 如果已选中&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**&#x200B;选项，则会显示&#x200B;**[!UICONTROL 自定义路径]**&#x200B;字段。

   这允许用户使用任意查询参数来定义域之后的 URL 路径。例如，如果您键入 `my/universal/link?os=9.2`，则完整营销链接 URL 将变为 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`。

   f. 单击&#x200B;**[!UICONTROL 决策]**&#x200B;选项卡并配置决策树。

   h. 如果安装了 iOS 应用程序，则应用程序会使用其逻辑来处理深层链接。最终目标仅在未安装应用程序的情况下用作回退。由于未安装应用程序，最终目标只能是 Web 链接或应用商店。

   i. 单击&#x200B;**[!UICONTROL 保存]**。

>[!TIP]
>
>保存营销链接后，便无法更改营销链接选项。这是因为您不希望更改可能已分发的营销链接行为。


### 配置应用程序链接

1. 要在 Android 应用程序中设置应用程序链接，请转到[添加 Android 应用程序链接](https://developer.android.com/studio/write/app-link-indexing)。

1. 在 Adobe Mobile Services 中，设置网站关联文档：

   a. 在 Mobile Services 主页中，选择您要为其设置应用程序链接的应用程序。

   b. 单击&#x200B;**[!UICONTROL 管理应用程序设置]**。

   c. 确保在&#x200B;**[!UICONTROL 添加应用商店应用程序]**&#x200B;部分添加了可处理通用链接或应用程序链接的 Android 应用程序。

   >[!TIP]
   >
   >如果未显示此部分，请单击&#x200B;**[!UICONTROL 添加应用商店应用程序]**&#x200B;链接。

   d. 滚动到&#x200B;**[!UICONTROL 通用链接和应用程序链接选项]**&#x200B;部分。

   e. 单击&#x200B;**[!UICONTROL 应用程序链接 (Android)]** 选项卡。

   f. 选择一个 Android 应用程序并键入 SHA-256 证书指纹。

   g. 单击&#x200B;**[!UICONTROL 保存]**。

   您必须至少提供一个 Android 应用程序选择和一个 SHA-256 证书，否则您将收到错误。

   >[!IMPORTANT]
   >
   >您可以通过单击&#x200B;**[!UICONTROL 通用链接和应用程序链接选项]**&#x200B;部分中的&#x200B;**[!UICONTROL 更新]**&#x200B;来更新文档。但是，当您单击&#x200B;**[!UICONTROL 更新]**&#x200B;时，系统会发出警告，通知您以前创建的所有通用链接或应用程序链接都将受到影响。

### 使用应用程序链接

1. 在 Adobe Mobile Services 中，创建一个使用应用程序链接的营销链接：

   a. 从 Mobile Services 主页中选择应用程序，单击&#x200B;**[!UICONTROL 客户获取]** > **[!UICONTROL 营销链接生成器]**。

   b. 单击&#x200B;**[!UICONTROL 新建]**。

   c. 在&#x200B;**[!UICONTROL 营销链接选项]**&#x200B;部分，选择&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**。

   d. 如果您在步骤 2 中配置了网站关联文档，则默认情况下会选中此选项。

   如果未配置，则&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**&#x200B;选项会处于禁用状态，并且默认情况下会选中&#x200B;**[!UICONTROL 使用插播式广告]**。

   e. 如果已选中&#x200B;**[!UICONTROL 使用通用链接或应用程序链接]**，则会显示&#x200B;**[!UICONTROL 自定义路径]**&#x200B;字段。

   这允许用户使用任意查询参数来定义域之后的 URL 路径。例如，如果您键入 `my/app/link?os=6.0`，则完整营销链接 URL 将变为 `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`。

   f. 单击&#x200B;**[!UICONTROL 决策]**&#x200B;选项卡并配置决策树。

   g. 如果安装了 Android 应用程序，则应用程序会使用其逻辑来处理深层链接。

   最终目标仅在未安装应用程序的情况下用作回退。由于未安装应用程序，最终目标只能是 Web 链接或应用商店。

   h. 单击&#x200B;**[!UICONTROL 保存]**。

>[!TIP]
>
>保存营销链接后，便无法更改&#x200B;**[!UICONTROL 营销链接选项]**。这是因为您不希望更改可能已分发的营销链接行为。

## 使用营销链接

现在，您可以在应用程序的消息传送和其他区域中使用这些营销链接。

>[!IMPORTANT]
>
>您将看不到通用链接或应用程序链接的点击跟踪计数，也无法使用插播式广告。

