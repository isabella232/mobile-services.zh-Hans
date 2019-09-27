---
description: 通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。
keywords: mobile
seo-description: 通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。
seo-title: Apple Universal Links和Android应用程序链接
solution: Marketing Cloud,Analytics
title: Apple Universal Links和Android应用程序链接
topic: 量度
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links和Android应用程序链接{#universal-links-and-app-links}

通用链接(iOS)和应用程序链接(Android)允许您连接到iOS或Android应用程序中的深层链接。

>[!IMPORTANT]
>
>从iOS 9.2开始，不支持深层链接。 您必须使用Apple Universal Links来深度链接到您的应用程序或网站。

## 通用链接 {#section_F8147944679A42E59CF4FD8814E5EF12}

通用链接允许您连接到iOS应用程序中的深层链接，iOS 9.2或更高版本支持这些链接。 当访问通用链接时，iOS会将链接直接重定向到应用程序中的开发人员。 如果未安装应用程序，它会在浏览器中为您的网站打开一个URL。 有关通用链接的详细信息，请参阅 [支持通用链接](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)。

## 应用程序链接

应用程序链接允许您连接到Android应用程序中的深层链接，Android 6.0或更高版本支持该链接。 访问应用程序链接时，Android会将链接直接重定向到应用程序中的开发人员。 如果未安装应用程序，它会在浏览器中为您的网站打开一个URL。 For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 使用通用链接或应用程序链接创建营销链接 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

您可以创建使用通用链接或应用程序链接的营销链接。

### 配置通用链接

1. 要在iOS应用程序中设置通用链接，请转到Apple [中的“处理通用链接”](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. 在Adobe Mobile services中，设置站点关联文档：

   a.在Mobile services主页中，选择要为其设置通用链接的应用程序。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the iOS app that handles the Universal Links is added to the **[!UICONTROL Add App Store Apps]** section.

   >[!TIP]
   >
   >If the **[!UICONTROL Add App Store Apps]** section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. In the Universal Links and App Links Options section, select an iOS app and type the App ID.****

   f. Click Save.****

   You must provide at least one iOS app selection and one App ID, or you will receive an error.

   >[!IMPORTANT]
   >
   >您可以通过单击通用链接和应用程序链接选项部分中的“更新”来更新文档。However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Use a Universal Link

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.单击“ **[!UICONTROL 新建”]**。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. If you configured the site-association documents in the Setting up site-association documents in Adobe Mobile Services section above, this option is selected by default.**

   If you did not configure the documents, the Use Universal Links or App Links option is disabled and Use Interstitials is selected by default.********

   e.如果选择 **[!UICONTROL 了“使用通用链接”或“应用程序链接]** ”选项，则会显 **[!UICONTROL 示“自定义路径]** ”字段。

   它允许用户依据域以及任意查询参数来定义 URL 路径。例如，如果您键入 您 `my/universal/link?os=9.2`的完整营销链接URL将变为 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`。

   f.单击“决 **[!UICONTROL 策]** ”选项卡并配置决策树。

   h. If the iOS app is installed, the app handles the deeplink with its logic. 最终目标仅在未安装应用程序时用作回退。 Since the app is not installed, the final destination can only be a web link or app store.

   i.单击“ **[!UICONTROL 保存]**”。

>[!TIP]
>
>保存营销链接后，“营销链接选项”便无法更改。 这是因为您不希望更改可能已分发的营销链接的行为。


### Configure an App Link

1. To set up App Links in your Android app, go to Add Android App Links.[](https://developer.android.com/studio/write/app-link-indexing)

1. In Adobe Mobile Services, set up the site-association documents:

   a.在Mobile services主页中，选择要为其设置应用程序链接的应用程序。

   b. Click **[!UICONTROL Manage App Settings]**.

   c.确保将处理通用链接或应用程序链接的Android应用程序添加到“添 **[!UICONTROL 加应用商店应用程序]** ”部分。

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d.滚动到“通用 **[!UICONTROL 链接和应用程序链接选项]** ”部分。

   e.单击“应 **[!UICONTROL 用程序链接(Android)”选项卡]** 。

   f.选择一个Android应用程序并键入SHA-256证书指纹。

   g.单击“ **[!UICONTROL 保存]**”。

   您必须至少提供一个Android应用程序选择和一个SHA-256证书，否则您将收到错误。

   >[!IMPORTANT]
   >
   >您可以通过单击&#x200B;**[!UICONTROL 通用链接和应用程序链接选项]**&#x200B;部分中的“**更新]”来更新文档。[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 使用应用程序链接

1. 在Adobe Mobile services中，创建一个使用应用程序链接的营销链接：

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.单击“ **[!UICONTROL 新建”]**。

   c.在“营销链 **[!UICONTROL 接选项”部分]** ，选择“使 **[!UICONTROL 用通用链接”或“应用程序链接”]**。

   d.如果您从步骤2中配置了站点关联文档，则默认情况下会选择此选项。

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e.如果 **[!UICONTROL 选择了“使用通用链接”或“应用程序链接]** ”，则会显 **[!UICONTROL 示“自定义路径]** ”字段。

   它允许用户依据域以及任意查询参数来定义 URL 路径。例如，如果您键入 您 `my/app/link?os=6.0`的完整营销链接URL将变为 `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`。

   f.单击“决 **[!UICONTROL 策]** ”选项卡并配置决策树。

   g.如果安装了Android应用程序，则应用程序将使用其逻辑处理该开发。

   最终目标仅用作未安装应用程序时的备用案例。 由于未安装应用程序，因此最终目标只能是Web链接或应用程序商店。

   h.单击“ **[!UICONTROL 保存]**”。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. 这是因为您不希望更改可能已分发的营销链接的行为。

## 使用营销链接

您现在可以在消息传递和应用程序中的其他区域使用这些营销链接。

>[!IMPORTANT]
>
>您将看不到通用链接或应用程序链接的点击跟踪计数，也无法使用插播式广告。

