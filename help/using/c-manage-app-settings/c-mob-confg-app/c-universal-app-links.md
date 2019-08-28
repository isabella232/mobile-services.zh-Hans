---
description: 通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。
keywords: mobile
seo-description: 通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。
seo-title: Apple Universal Links和Android应用程序链接
solution: Marketing Cloud，Analytics
title: Apple Universal Links和Android应用程序链接
topic: 量度
uuid: 8d6441dc-4307-4454-95ea-d77 ec796 f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links和Android应用程序链接{#universal-links-and-app-links}

通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。

>[!IMPORTANT]
>
>从iOS9.2开始，不支持深层链接。您必须使用Apple Universal Links以深层链接到应用程序或网站。

## 通用链接 {#section_F8147944679A42E59CF4FD8814E5EF12}

通用链接允许您连接到iOS应用程序中的深层链接，并在iOS9.2或更高版本中受支持。当访问Universal Link时，iOS将链接直接重定向到应用程序中的取消链接。如果未安装您的应用程序，它将在浏览器中打开网站的URL。有关通用链接的更多信息，请参阅 [支持通用链接](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)。

## 应用程序链接

应用程序链接允许您连接到Android应用程序中的深层链接，在Android6.0或更高版本中支持此链接。当访问App Link时，Android会将链接直接重定向到应用程序中的取消链接。如果未安装您的应用程序，它将在浏览器中打开网站的URL。For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 使用通用或应用程序链接创建营销链接 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以创建使用通用或App链接的营销链接。

### 配置通用链接

1. 要在iOS应用程序中设置通用链接，请转到 [Apple中的处理通用链接](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. 在Adobe Mobile Services中，设置站点关联文档：

   a. 在Mobile Services主页中，选择您要为其设置通用链接的应用程序。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 确保处理通用链接的iOS应用程序添加到 **[!UICONTROL “添加应用商店应用程序]** ”部分。

   >[!TIP]
   >
   >如果 **[!UICONTROL 未显示添加App Store应用程序]** 部分，请单击 **[!UICONTROL 添加应用商店应用程序]** 链接。

   d. 在 **[!UICONTROL 通用链接和应用程序链接选项]** 部分中，选择iOS应用程序并键入App ID。

   f. 单击 **[!UICONTROL “保存]**”。

   您必须至少提供一个iOS应用程序选择和一个应用程序ID，否则您将收到一个错误。

   >[!IMPORTANT]
   >
   >您可以通过单击通用链接和应用程序链接选项部分中的“更新”来更新文档。However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用通用链接

1. 在Adobe Mobile Services中，创建使用通用链接的营销链接：

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 单击 **[!UICONTROL “新建]**”。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. 如果您在上面的Adobe Mobile *Services* 部分设置站点关联文档中配置了站点关联文档，则默认情况下会选择此选项。

   如果未配置文档，则禁用 **[!UICONTROL “使用通用链接”或“应用程序链接”]** 选项，默认情况下 **[!UICONTROL 将选中“使用交叉时间”]** 。

   e. 如果选择 **[!UICONTROL 了“使用通用链接”或“应用程序链接]** ”选项，则会显示 **[!UICONTROL “自定义路径]** ”字段。

   它允许用户依据域以及任意查询参数来定义 URL 路径。例如，如果您键入`my/universal/link?os=9.2`您的完整营销链接URL `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`将变为。

   f. 单击 **[!UICONTROL “决策]** ”选项卡并配置您的决策树。

   h. 如果安装了iOS应用程序，应用程序将处理与其逻辑的分离。最终目标仅用作未安装应用程序时的回退。由于未安装应用程序，最终目标只能是Web链接或应用商店。

   i. 单击 **[!UICONTROL “保存]**”。

>[!TIP]
>
>保存营销链接后，营销链接选项将无法更改。这是因为您不希望更改可能已经分发的营销链接的行为。


### 配置应用程序链接

1. 要在Android应用程序中设置应用程序链接，请转到 [添加Android应用程序链接](https://developer.android.com/studio/write/app-link-indexing)。

1. 在Adobe Mobile Services中，设置站点关联文档：

   a. 在Mobile Services主页中，选择要为其设置应用程序链接的应用程序。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 确保处理通用链接或应用程序链接的Android应用程序添加到 **[!UICONTROL “添加应用商店应用程序]** ”部分。

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. 滚动到 **[!UICONTROL 通用链接和应用程序链接选项]** 部分。

   e. 单击“App Links”( **[!UICONTROL 应用程序链接)(Android)]** 选项卡。

   f. 选择Android应用程序并键入SHA-256证书指纹。

   g. 单击 **[!UICONTROL “保存]**”。

   您必须至少提供一个Android应用程序选择和一个SHA-256证书，否则您将收到一个错误。

   >[!IMPORTANT]
   >
   >您可以通过单击&#x200B;**[!UICONTROL 通用链接和应用程序链接选项]**&#x200B;部分中的“**更新]”来更新文档。[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用应用程序链接

1. 在Adobe Mobile Services中，创建使用应用程序链接的营销链接：

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 单击 **[!UICONTROL “新建]**”。

   c. 在 **[!UICONTROL “营销链接选项]** ”部分中，选择 **[!UICONTROL “使用通用链接”或“应用程序链接]**”。

   d. 如果您从步骤中配置了站点关联文档，则默认情况下会选中此选项。

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. 如果 **[!UICONTROL 选择了“使用通用链接”或“应用程序链接]** ”，则会显示 **[!UICONTROL “自定义路径]** ”字段。

   它允许用户依据域以及任意查询参数来定义 URL 路径。例如，如果您键入`my/app/link?os=6.0`您的完整营销链接URL `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`将变为。

   f. 单击 **[!UICONTROL “决策]** ”选项卡并配置您的决策树。

   g. 如果安装了Android应用程序，应用程序将处理与其逻辑的亵渎。

   最终目标仅用作未安装应用程序时的回退案例。由于未安装应用程序，最终目标只能是Web链接或应用商店。

   h.  单击 **[!UICONTROL “保存]**”。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. 这是因为您不希望更改可能已经分发的营销链接的行为。

## 使用营销链接

您现在可以在应用程序中的消息和其他区域中使用这些营销链接。

>[!IMPORTANT]
>
>您不会看到具有通用链接或应用程序链接的点击跟踪计数，而且您也不能使用交互性。

