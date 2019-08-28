---
description: 此信息可帮助您排查应用程序内消息传送问题。
keywords: mobile
seo-description: 此信息可帮助您排查应用程序内消息传送问题。
seo-title: 排查应用程序内消息传送问题
solution: Marketing Cloud，Analytics
title: 排查应用程序内消息传送问题
topic: 量度
uuid: 8813e8d8-bb1 e-46ad-83cd-98e68 f73 ce6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

此信息可帮助您排查应用程序内消息传送问题。

如果完成了应用程序内消息传送的所有要求，但消息仍不显示，则请验证以下项：

## 应用程序中是否纳入了新配置和新 SDK？

* 确认 SDK 的版本为 4.2 或更高，并且已正确配置 SDK。

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## 我的全屏消息在 Android 中不显示。我使用的 SDK 和配置正确无误，而且也触发了触发器。

您是否更新了清单文件以定义全屏活动？

## 我的本地通知消息不能在 Android 中使用。

确认清单中声明了本地通知广播接收器。For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## 消息是实时的吗？

检查“**管理应用程序内消息”页面上状态**&#x200B;列中的列表视图，确认消息是否是实时的。

## 观看 *节目一次*， *始终显示*， *在“受众”页面上显示脱机* 设置。

请确认这些设置正确无误。在“受众”页面上，查看&#x200B;**触发器**&#x200B;选项卡中的选项，您可以在此选项卡上指定消息的显示频率。

## 如果使用启动项作为触发器...

启动项只会在新会话中触发。有关会话何时开始的信息，请参阅`lifecycleTimeout` 在 [AdobeMobile JSON配置](/help/ios/configuration/json-config/json-config.md) 文件中。

## 我远程更新了消息，但我的应用程序仍显示旧消息。

完成以下任务之一：

* Dynamic Tag Management 可能需要几分钟的时间来根据您的新定义更新消息端点。

   请稍候片刻，然后重试。

* 只有在全新启动之后，该配置才会更新。

   如果是在生命周期会话超时期间重新启动的应用程序，则您的新配置可能没有下载下来。

## 我的图像不完全适合模板提供的空间。

应用程序内消息全屏模板支持显示来自远程服务器（图像 URL）或来自应用程序包（捆绑图像）的图像。图像应采用标准格式，例如 JPG、GIF 或 PNG。

由于设备屏幕具有多种不同的尺寸，图像可能与模板所提供的空间达不到完全匹配。如果图像不适合，则模板通常会着重显示图像的中心，并裁剪（纵向）或淡化（横向）边缘。

以下是每个方向的准确定位和大小调整规则：

* **纵向**：处于这个方向时，模板会在手机上将图像的高度调整为 195px，在平板电脑上将图像的高度调整为 529px。如果图像宽度小于设备宽度，则图像居中；如果图像宽度大于设备宽度，则模板会对图像进行剪裁。

* **横向**：处于这个方向时，模板会将图像的高度调整为设备高度的 100%，将其宽度调整为设备宽度的 75%，还会在右侧对图像进行淡化处理。

   如果您的全屏模板存在问题，则可以下载并使用自定义 HTML 模板。通过自定义 HTML 模板，您可以更加灵活地处理图像，还可以实现对该模板的完全控制。

## 我的消息没有反映我在 UI 中所做的更改/更新。

SDK 在生命周期启动时获取全新/更新的消息。这仅在应用程序关闭/转入后台的时间超过了生命周期超时值然后又重新打开的情况下才适用。

完成以下步骤：

1. 在配置文件中卷起您的消息URL以验证远程消息是否已更新(例如， `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. 关闭应用程序。
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. 打开应用程序，导航到消息应当显示的地方，并验证它是否已更新。