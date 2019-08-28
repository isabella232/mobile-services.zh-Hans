---
description: 此信息可帮助您排查应用程序内消息传送问题。
keywords: mobile
seo-description: 此信息可帮助您排查应用程序内消息传送问题。
seo-title: 应用程序内消息传递疑难解答
solution: Marketing Cloud，Analytics
title: 应用程序内消息传递疑难解答
topic: 量度
uuid: 39c3a21d-92c2-4004-b00 f-99b6 f91 d3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# 应用程序内消息传递疑难解答{#troubleshooting-in-app-messaging}

此信息可帮助您排查应用程序内消息传送问题。

如果您符合应用程序内消息传送的所有要求，但消息仍无法显示，请检查以下各项：

## 应用程序中是否纳入了新配置和新 SDK？

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## 我的全屏消息在 Android 中不显示。我使用的 SDK 和配置正确无误，而且也触发了触发器。

您是否更新了清单文件以定义全屏活动？

## 我的本地通知消息在 Android 中无法使用。

确保在清单中声明了本地通知广播接收器。For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## 消息是实时的吗？

要验证您的消息是否为实时消息，请在管理应用程序内消息页面上的&#x200B;**状态**&#x200B;列中，检查消息列表。

## 观看 *节目一次*，始终 *显示*， *在“受众”选项卡上显示脱机* 设置。

验证已按照您所需的方式设置了这些设置。在&#x200B;**[!UICONTROL 受众]**&#x200B;选项卡中，检查您的&#x200B;**触发器]选项，这些选项允许您指定消息显示的频率。[!UICONTROL **

## 如果使用启动事件作为触发器…

启动项只会在新会话中触发。有关会话何时开始的更多信息，请参阅 `lifecycleTimeout`JSON 配置[中的 ](/help/android/configuration/json-config/json-config.md) 行。

## 我远程更新了消息，但我的应用程序仍显示旧消息。

请牢记以下信息：

* 动态标签管理可能要用几分钟时间来使用您的新定义更新其端点。请稍等片刻，然后重试。
* 只有在全新启动之后，该配置才会更新。如果应用程序是在生命周期会话超时期间重新启动的，则可能未下载您的新配置。

有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

## 我的图像不完全适合模板提供的空间。

应用程序内消息全屏模板支持显示来自远程服务器（图像 URL）或来自应用程序包（捆绑图像）的图像。图像应采用标准图像格式，例如 JPG、GIF 或 PNG。由于设备屏幕具有多种不同的尺寸，因此图像很可能并不完全适合模板提供的空间。模板主要用于显示图像的中央部分，如果图像不适合，则会裁剪（纵向）或淡化（横向）侧边。

以下是每个方向的准确定位和大小调整规则：

* **纵向**
   * 对于手机，高度为 195 像素.
   * 对于平板电脑，高度为 529 像素.
   * 如果图像宽度小于设备宽度，则将图像居中。
   * 如果图像宽度大于设备宽度，则裁剪图像。

* **横向**
   * 图像缩放至设备高度的 100%。
   * 宽度为设备的 75%，并在右侧淡出。
   如果您的全屏模板存在问题，则可以下载并使用自定义 HTML 模板。此模板为图像提供了更高的灵活性，并允许完全控制模板。

