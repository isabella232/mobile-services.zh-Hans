---
description: 此信息可帮助您排查应用程序内消息传送问题。
keywords: mobile
seo-description: 此信息可帮助您排查应用程序内消息传送问题。
seo-title: 排查应用程序内消息传送问题
solution: Experience Cloud,Analytics
title: 排查应用程序内消息传送问题
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 100%

---


# 排查应用程序内消息传送问题￼{#troubleshooting-in-app-messaging}

此信息可帮助您排查应用程序内消息传送问题。

如果您已完成应用程序内消息传送服务的所有要求，但却没有显示消息，请检查以下条目：

## 应用程序中是否纳入了新配置和新 SDK？

确认 SDK 的版本为 4.2 或更高版本，并且已正确配置 SDK。确保您的配置（已下载的 JSON 文件）中包含 `Messages` 部分，或者您具有消息远程端点，以便可以通过 Dynamic Tag Management 进行检索。

## Android 中未显示我的全屏消息。我使用了正确的 SDK 和配置，并且也满足触发器条件。

是否更新清单文件以定义全屏活动？

## Android 中的本地通知消息不起作用。

确保在清单中声明了本地通知广播接收器。有关更多信息，请参阅[启用应用程序内消息](/help/android/messaging-main/messaging/messaging.md)中的步骤 2。

## 消息是实时的吗？

检查“管理应用程序内消息”页面上“状态”列中的列表视图，验证它是否处于启用状态。

## 查看“受众”选项卡上的“显示一次”**、“始终显示”**&#x200B;和“脱机显示”**&#x200B;设置。

验证已按照您所需的方式设置了这些设置。在&#x200B;**[!UICONTROL 受众]**&#x200B;选项卡中，检查您的&#x200B;**[!UICONTROL 触发器]**&#x200B;选项，这些选项允许您指定消息显示的频率。

## 如果使用启动事件作为触发器...

启动项只会在新会话中触发。有关会话何时开始的更多信息，请参阅 JSON 配置文件中的 `lifecycleTimeout` 行。有关更多信息，请参阅 [ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)。

## 我远程更新了消息，但我的应用程序仍显示旧的消息。

完成以下任务之一：

* Dynamic Tag Management 可能要用几分钟时间来使用您的新定义更新其端点。

   请稍等片刻，然后重试。

* 只有在全新启动之后，该配置才会更新。如果应用程序是在生命周期会话超时期间重新启动的，则可能未下载您的新配置。

   有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

## 我的图像不能准确地放入模板提供的空间。

应用程序内消息全屏模板，可支持显示来自远程服务器（图像 URL）或来自应用程序捆绑包（捆绑的图像）的图像。图像应采用标准图像格式，例如 JPG、GIF 或 PNG。

由于设备屏幕具有多种不同的尺寸，因此图像很可能并不完全适合模板提供的空间。模板主要用于显示图像的中央部分，如果图像不适合，则会裁剪（纵向）或淡化（横向）侧边。

以下是每个方向的准确定位和大小调整规则：

* **纵向**：
   * 对于手机，高度为 195 像素
   * 对于平板电脑，高度为 529 像素
   * 如果图像宽度小于设备宽度，则居中显示。
   * 如果图像宽度大于设备宽度，则进行裁剪。

* **横向**：
   * 图像缩放到与设备等高的效果。
   * 宽度是设备的 75%，右侧为淡出显示效果。

如果全屏模板存在问题，您可以下载并使用自定义的 HTML 模板。这种模板为图像提供了更大的灵活性，并允许完全调控模板。

## iPhone X 上的应用程序内消息不以全屏模式显示。

要在 iPhone X 上以全屏模式显示应用程序内消息，请执行以下操作：

1. 在 Meta 标记中添加 `viewport-fit=cover`。

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. 在 CSS 中为顶部 UI 元素设置适当的填充，例如：

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   这些设置可防止 UI 元素与状态栏产生冲突。
