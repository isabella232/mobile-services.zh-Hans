---
description: 为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。
keywords: mobile
seo-description: 为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。
seo-title: 体验：应用程序内消息
solution: Marketing Cloud,Analytics
title: 体验：应用程序内消息
topic: 量度
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# 体验：应用程序内消息 {#experience-in-app-message}

为应用程序内消息配置体验选项，包括类型（全屏、警报或通知）和显示、文本与按钮选项。

1. 在应用程序中，单击&#x200B;**[!UICONTROL 消息传送]** &gt; **[!UICONTROL 管理消息]** &gt; **[!UICONTROL 创建消息]** &gt; **[!UICONTROL 创建应用程序内消息]**。
1. 在体验页面上，键入消息的名称。
1. 填写&#x200B;**[!UICONTROL 类型]**&#x200B;部分中的字段：

   * **[!UICONTROL 类型]**
为您的应用程序内消息促销活动选择消息类型：

      * **[!UICONTROL 全屏幕]**
      * **[!UICONTROL 警报]**
      * **[!UICONTROL 本地通知]**
   * **[!UICONTROL 模板]**

      为您的内容自定义主题响应消息模板。

      >[!TIP]
      >
      >仅当您选择&#x200B;**[!UICONTROL 全屏]**&#x200B;消息类型时，才会显示此选项。

   * **[!UICONTROL 自定义]**

      加载您的自定义 HTML 内容（仅全屏幕）。您必须提供点进链接和取消链接。

      1. 单击&#x200B;**[!UICONTROL 浏览]**&#x200B;并下载 HTML 文件或将 HTML 文档拖到窗口中。
      1. 单击&#x200B;**[!UICONTROL 下载示例]**&#x200B;以查看示例自定义 HTML 内容。
      >[!TIP]
      >
      >仅当您选择&#x200B;**[!F全屏]**&#x200B;消息类型时，才会显示此选项。



1. 填写&#x200B;**[!UICONTROL 显示]**&#x200B;部分中的字段：

   * **[!UICONTROL 主题]**
   选择一个消息主题。

   * **[!UICONTROL 版式]**

      在设备屏幕上选择应用程序布局。

   * **[!UICONTROL 图像 URL]**

      图像的 URL。如果您在使用全屏模板时遇到大小调整问题，请参阅[排查应用程序内消息传送问题](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)中的“我的图像不完全适合模板提供的空间”**。

   * **[!UICONTROL 捆绑图像]**

      应用程序代码包中图像的路径。此选项在图像不存在或图像不可用时使用。例如，如果设备处于离线状态，则图像可能不可用。如果您在使用全屏模板时遇到大小调整问题，请参阅[排查应用程序内消息传送问题](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)中的“我的图像不完全适合模板提供的空间”**。


1. 填写&#x200B;**[!UICONTROL 文本]**&#x200B;部分中的字段：

   * **[!UICONTROL 头]**

      键入消息标题的文本。

   * **[!UICONTROL 内容]**

      键入消息内容的文本。

1. 填写&#x200B;**[!UICONTROL 按钮]**&#x200B;部分中的字段：

   * **[!UICONTROL 点进按钮]**

      **[!UICONTROL 点进]**&#x200B;按钮的标签。点按此按钮即计为一次成功的点进。系统会将用户重定向到目标。

   * **[!UICONTROL 目标]**

      指定一个特定目标（如 Web、深层链接或混合链接）以在用户点进消息时将用户发送到该目标。成功点进的重定向 URL。

      此 URL 可能包含以下信息：

      * `{userId}`，以用户标识符替换，或者在未设置用户标识符时留空。
      * `{trackingId}`，以相应的 ID（与 *s_vi* Cookie 相关）替换。
      * `{messageId}`，以应用程序内消息的唯一 ID 替换。
      * `{lifetimeValue}`，以生命周期值替换；或者如果不存在生命周期值，则使用 0。
      以下是用户 ID 跟踪示例：`https://www.mysite.com?uid={userId}`。

      如果点进 URL 使用 `https://` 或 `https://`，则该 URL 将在应用程序外的设备浏览器中打开。否则，每个平台都支持允许您打开或引用您的应用程序的方案，但前提是开发的应用程序支持自定义方案。

      >[!TIP]
      >
      >当您使用 **[!UICONTROL Web 链接]**&#x200B;或&#x200B;**[!UICONTROL 自定义链接]**&#x200B;目标类型时，不会跟踪该目标类型。仅跟踪&#x200B;**[!UICONTROL 深层链接]**。有关更多信息，请参阅[目标](/help/using/acquisition-main/c-create-destinations.md)。


1. （可选）单击以下图标，预览消息的布局：

   * **[!UICONTROL 摘要]**&#x200B;将隐藏预览窗格。

      单击 ![预览](assets/icon_preview.png) 可重新显示预览窗格。

   * **[!UICONTROL 更改方向]**

      要将预览的方向从纵向更改为横向模式，请单击 ![方向](assets/icon_orientation.png)。对于手表，方向会从圆形表盘更改为方形表盘。

   * **[!UICONTROL 在用户的手表上预览]**

      要预览显示在用户手表上的消息，请单击 ![观看图标](assets/icon_watch.png)。

   * **[!UICONTROL 在用户的手机上预览]**

      要预览显示在用户手机上的消息，请单击 ![电话图标](assets/icon_phone.png)。

   * **[!UICONTROL 在用户的平板电脑上预览]**

      要预览显示在用户平板电脑上的消息，请单击 ![平板电脑图标](assets/icon_tablet.png)。

      在预览窗格的底部，您可以查看上一步所选受众的描述。您还可以在预览窗格的底部查看上一步骤中所选受众的描述。

1. 配置[计划选项](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)。
