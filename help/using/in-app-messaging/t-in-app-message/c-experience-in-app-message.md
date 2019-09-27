---
description: 为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。
keywords: mobile
seo-description: 为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。
seo-title: 体验应用程序内消息
solution: Marketing Cloud,Analytics
title: 体验应用程序内消息
topic: 量度
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 在体验页面上，键入消息的名称。
1. 填写&#x200B;**[!UICONTROL 类型]部分中的字段：**

   * **[!UICONTROL 类型]**&#x200B;为应用程序内消息营销活动选择消息类型：

      * **[!UICONTROL 全屏幕]**
      * **[!UICONTROL 警报]**
      * **[!UICONTROL 本地通知]**
   * **[!UICONTROL 模板]**

      为您的内容自定义主题响应消息模板。

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL 自定义]**

      加载您的自定义 HTML 内容（仅全屏幕）。您必须提供点进链接和取消链接。

      1. 单击&#x200B;**[!UICONTROL 浏览]并下载 HTML 文件或将 HTML 文档拖到窗口中。**
      1. 单击“**[!UICONTROL 下载示例]”以查看示例自定义 HTML 内容。**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. 填写&#x200B;**[!UICONTROL 显示]部分中的字段：**

   * **[!UICONTROL 主题]**
   选择一个消息主题。

   * **[!UICONTROL 版式]**

      在设备屏幕上选择应用程序布局。

   * **[!UICONTROL 图像 URL]**

      图像的 URL。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL 捆绑图像]**

      应用程序代码包中图像的路径。此选项在图像不存在或图像不可用时使用。例如，如果设备处于离线状态，则图像可能不可用。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. 填写&#x200B;**[!UICONTROL 文本]部分中的字段：**

   * **[!UICONTROL 头]**

      键入消息标题的文本。

   * **[!UICONTROL 内容]**

      键入消息内容的文本。

1. 填写&#x200B;**[!UICONTROL 按钮]部分中的字段：**

   * **[!UICONTROL 点进按钮]**

      **[!UICONTROL 点进]按钮的标签。**&#x200B;点击此按钮可计为成功的点进。 用户将被重定向到目标。

   * **[!UICONTROL 目标]**

      指定一个特定目标（如 Web、深层链接或混合链接）以在用户点进消息时将用户发送到该目标。成功点进的重定向 URL。

      此 URL 可能包含以下信息：

      * `{userId}`，将替换为用户标识符，或在未设置用户标识符时为空。
      * `{trackingId}`，将替换为aid(与 *s_vi* cookie关联)。
      * `{messageId}`，将替换为应用程序内消息的唯一ID。
      * `{lifetimeValue}`，将替换为生命周期值；如果不存在生命周期值，则替换为0。
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. 否则，每个平台都支持允许您打开或引用您的应用程序的方案，但前提是开发的应用程序支持自定义方案。

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. 仅跟踪&#x200B;**[!UICONTROL 深层链接]。** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. （可选）单击以下图标，预览消息的布局：

   * **[!UICONTROL “摘要]** ”会隐藏预览窗格。

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL 更改方向]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 对于手表，方向从圆形变为方形表面。

   * **[!UICONTROL 在用户观看时预览]**

      要预览消息在用户观看时的显示效果，请单击观 ![看图标](assets/icon_watch.png)。

   * **[!UICONTROL 在用户的手机上预览]**

      要预览消息在用户手机上的显示效果，请单击“电话 ![”图标](assets/icon_phone.png)。

   * **[!UICONTROL 在用户的平板电脑上预览]**

      要在用户的平板电脑中预览消息，请单击平 ![板电脑图标](assets/icon_tablet.png)。

      在预览窗格的底部，您可以查看上一步所选受众的描述。您还可以在预览窗格的底部查看上一步骤中所选受众的描述。

1. 配置 [计划选项](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)。
