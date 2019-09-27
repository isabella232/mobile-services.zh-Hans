---
description: 此信息可帮助您排查应用程序内消息传送问题。
keywords: mobile
seo-description: 此信息可帮助您排查应用程序内消息传送问题。
seo-title: 排查应用程序内消息传送问题
solution: Marketing Cloud,Analytics
title: 排查应用程序内消息传送问题
topic: 量度
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

此信息可帮助您排查应用程序内消息传送问题。

如果您符合应用程序内消息传送的所有要求，但消息仍无法显示，请检查以下各项：

## 应用程序中是否纳入了新配置和新 SDK？

确认 SDK 的版本为 4.2 或更高，并且已正确配置 SDK。Ensure that you have a `Messages` section in your configuration (downloaded JSON file), or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## 我的全屏消息在 Android 中不显示。我使用的 SDK 和配置正确无误，而且也触发了触发器。

您是否更新了清单文件以定义全屏活动？

## 我的本地通知消息不能在 Android 中使用。

确保在清单中声明了本地通知广播接收器。For more information, see step 2 in [Enabling In-App Messages](/help/android/messaging-main/messaging/messaging.md).

## 消息是实时的吗？

查看“管理应用程序内消息”页面上列表视图下的“状态”列，确认消息是否为实时消息。

## Look at show once, show always, show offline settings on the Audience tab.******

验证已按照您所需的方式设置了这些设置。在&#x200B;**[!UICONTROL 受众]**&#x200B;选项卡中，检查您的&#x200B;**触发器]选项，这些选项允许您指定消息显示的频率。[!UICONTROL **

## 如果使用启动项作为触发器...

启动项只会在新会话中触发。For more information about when a session begins, see the `lifecycleTimeout` row in the JSON Config file. For more information, see  ADBMobile JSON Config.[](/help/ios/configuration/json-config/json-config.md)

## 我远程更新了消息，但我的应用程序仍显示旧消息。

完成以下任务之一：

* Dynamic Tag Management 可能要用几分钟时间来使用您的新定义更新其端点。

   请稍等片刻，然后重试。

* 只有在全新启动之后，该配置才会更新。如果应用程序是在生命周期会话超时期间重新启动的，则可能未下载您的新配置。

   有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

## 我的图像不完全适合模板提供的空间。

应用程序内消息全屏模板支持显示来自远程服务器（图像 URL）或来自应用程序包（捆绑图像）的图像。图像应采用标准图像格式，例如 JPG、GIF 或 PNG。

由于设备屏幕具有多种不同的尺寸，因此图像很可能并不完全适合模板提供的空间。模板主要用于显示图像的中央部分，如果图像不适合，则会裁剪（纵向）或淡化（横向）侧边。

以下是每个方向的准确定位和大小调整规则：

* **纵向**:
   * 对于手机，高度为 195 像素
   * 对于平板电脑，高度为 529 像素
   * 如果图像宽度小于设备宽度，则将图像居中。
   * 如果图像宽度大于设备宽度，则裁剪图像。

* **横向**:
   * 图像缩放至设备高度的 100%。
   * 宽度为设备的 75%，并在右侧淡出。

如果您的全屏模板存在问题，则可以下载并使用自定义 HTML 模板。此模板为图像提供了更高的灵活性，并允许完全控制模板。

## 无法在 iPhone X 上以全屏模式显示应用程序内消息。

要在 iPhone X 上以全屏模式显示应用程序内消息，请执行以下操作：

1. Add `viewport-fit=cover` in the meta tag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. 在 CSS 中为顶部 UI 元素设置适当的边距，如下所示：

   ```html
   topelement {
     padding-top:20px;
     /*Status bar height on iOS 11.0*/
     padding-top:constant(safe-area-inset-top);
     /*Status bar height on iOS 11+ */
     padding-top:env(safe-area-inset-top);
     } 
   ```

   这些设置可阻止 UI 元素与状态栏发生冲突。
