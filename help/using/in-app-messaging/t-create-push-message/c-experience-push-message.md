---
description: 您可以为推送消息和富推送消息配置体验选项，包括名称、消息文本和目标选项。您还可以配置高级选项，包括适用于 iOS 设备的负载选项和自定义选项。
keywords: mobile
seo-description: 您可以为推送消息和富推送消息配置体验选项，包括名称、消息文本和目标选项。您还可以配置高级选项，包括适用于 iOS 设备的负载选项和自定义选项。
seo-title: 体验推送消息
solution: Marketing Cloud，Analytics
title: 体验推送消息
topic: 量度
uuid: 1a8baf3e-9fea-452c-b0 fc-4ba8 ac270861
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: push message {#experience-push-message}

您可以为推送消息和富推送消息配置体验选项，包括名称、消息文本和目标选项。您还可以配置高级选项，包括适用于 iOS 设备的负载选项和自定义选项。

1. 在“受众”页面上，以获取新推送消息，单击 **[!UICONTROL “体验]**”。

   ![体验推送消息屏幕](assets/experience-push-message.png)

1. 为此消息键入一个名称。
1. 在&#x200B;**[!UICONTROL 消息]部分的以下字段中键入相应信息：**

   * **[!UICONTROL 内容]**

      指定消息的文本。您最多可以指定 140 个字符。

   * **[!UICONTROL 媒体 URL]**

      键入您计划在推送通知消息中使用的媒体文件 URL。有关使用丰富推送通知的要求，请参阅 *下方丰富推送通知* 的要求。

      >[!IMPORTANT]
      >
      >要在推送通知中显示图像或视频，请记住以下内容：
      > * `attachment-url` 数据在推送负载中进行处理。
      > * 媒体 URL 必须能够处理峰值请求。


   * **[!UICONTROL 目标]**

      指定一个特定目标（如 Web、深层链接或混合链接）以在用户点进消息时将用户发送到该目标。有关更多信息，请参阅 [目标](/help/using/acquisition-main/c-create-destinations.md)。

      >[!TIP]
      >
      >When you use the * **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. 仅跟踪&#x200B;**[!UICONTROL 深层链接]。**

## 丰富推送通知的要求

以下是发送丰富推送通知的要求：

* **支持的版本**

   以下版本支持丰富推送通知：
   * Android 4.1.0 或更高版本
   * iOS 10 或更高版本

      >[!IMPORTANT]
      >
      >请牢记以下信息：
      >* 仍将发送发送到先前版本的丰富推送消息，但只显示文本。
      >* 当前不支持手表。


* **文件格式**

   以下是支持的文件格式：
   * 图像：JPG 和 PNG
   * 动画（仅限 iOS）：GIF
   * 视频（仅限 iOS）：MP4

* **URL格式**
   * 仅限 HTTPS

* **大小调整**
   * 图像必须采用2：1格式，否则它们会被裁剪。

有关配置富推送通知的更多信息，请参阅以下内容：

* [在Android中接收推送通知](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [在iOS中接收富推送通知](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

要在Experience页面上配置推送消息，请执行以下操作：

1. (**Optional**) Click the **[!UICONTROL Show Advanced Options]** link to configure additional options:

   * **[!UICONTROL 负载：数据]**

      提供 JSON 格式的自定义推送负载，该负载将通过推送通知或本地通知发送到应用程序。Android 和 iOS 的大小限制是 4 KB。

   * **[!UICONTROL Apple 选项：类别]**

      为推送和本地通知提供一个类别。有关更多信息，请参阅“iOS 开发人员库”**&#x200B;中的[管理应用程序通知支持](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9)。

   * **[!UICONTROL Apple 选项：声音]**

      在您的应用程序包中提供要播放的声音文件的名称。如果未设置此选项，则播放默认的警报声。有关更多信息，请参阅“iOS 开发人员库”中的[管理应用程序通知支持](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10)**。

   * **[!UICONTROL Apple 选项：可用内容]**

      选择此选项，以便在有消息到来时，iOS 唤醒位于后台的应用程序并允许它根据消息负载执行代码。For more information, see [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) in the *iOS Developer Library*.

1. （可选）单击以下图标，预览消息的布局：

   * **[！UICCONTROL x摘要}**

      隐藏预览窗格。单击 ![预览](assets/icon_preview.png) 以再次显示预览窗格。

   * **[!UICONTROL 更改方向]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 对于手表，方向从圆形表盘更改为方形表盘。

   * **[!UICONTROL 在用户的观察上预览]**

      要预览消息，如同显示在用户的手表上，单击 ![“观察”图标](assets/icon_watch.png)。

   * **[!UICONTROL 在用户的手机上预览]**

      要预览消息，如同在用户的移动电话上显示 ![的电话图标](assets/icon_phone.png)上一样。

   * **[!UICONTROL 在用户的平板电脑上预览]**

      要在用户的平板电脑中预览消息，请单击 ![平板电脑图标](assets/icon_tablet.png)。
   在预览窗格的底部，您可以查看上一步所选受众的描述。

1. (**Optional**) Click **[!UICONTROL Test]** to push your message to specified devices for testing purposes.
1. 选择服务并至少为一个要接收推送消息的设备键入推送令牌。

   以逗号分隔的列表形式指定令牌，以将消息推送到多个设备。

1. 配置消息的计划选项。

   有关更多信息，请参阅 [计划：推送消息](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)。
