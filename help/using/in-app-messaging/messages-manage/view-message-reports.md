---
description: 您可以查看应用程序内消息和推送消息的消息报表。
keywords: mobile
seo-description: 您可以查看应用程序内消息和推送消息的消息报表。
seo-title: 查看消息报告
solution: Marketing Cloud，Analytics
title: 查看消息报告
topic: 量度
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

您可以查看应用程序内消息和推送消息的消息报表。

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   有关创建粘性滤镜的更多信息，请参阅 [添加粘性滤镜](/help/using/usage/reports-customize/t-sticky-filter.md)。

>[!TIP]
>
>根据您正在查看的消息类型，报告可能会有所不同。

## In-app messages {#section_90B79BA58E8141F78538C187EB1BF8C7}

如果您查看的是应用程序内消息的报表，则该报表类似于以下插图：

![报告消息](assets/report_message.png)

### 应用程序内消息指标

下面列出了应用程序内消息的可用指标：

* **[!UICONTROL 在]**&#x200B;触发消息时印象。

* **[!UICONTROL 单击，]**&#x200B;当用户按下警报或全屏消息上 **[!UICONTROL 的“点击点进]** ”按钮，以及用户从本地通知打开应用程序时点击。

* **[!UICONTROL 取消]**，当用户按下警报上的 **[!UICONTROL “取消]** ”按钮或全屏消息时。

* **[!UICONTROL 参与率]**&#x200B;是Adobe Analytics中计算得出的指标，是点击次数除以次数的结果。

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

如果您查看的是推送消息的报表，则该报表类似于以下插图：

![推送消息](assets/report_message_push.png)

顶部的图表显示了已打开消息的用户数量。

### 推送消息指标

以下是可用于推送消息的指标列表：

* **[!UICONTROL 时间]**

   将消息从 Mobile Services 推送到设备的时间。

* **[!UICONTROL 状态]**

   消息的状态以及可用状态有：

   * **[!UICONTROL 已取消]**
   * **[!UICONTROL 已安排]**
   * **[!UICONTROL 执行执行]**
   * **[!UICONTROL 已执行]**

* **[!UICONTROL 已发布]**

   成功发送到Apple Push Notification Service/Firebase Cloud Messaging(APNS/FCM)的设备令牌数量，用于向用户设备发送消息。

* **[!UICONTROL 失败]**

   未成功发送到APNS/FCM的设备令牌数。失败的可能原因如下：

   * pushID 无效

   * 为作业的应用程序提供的推送平台(APNS、FCM等)不存在。例如，此平台可收集 iOS 推送令牌但并未配置 APNS 服务。

   * 消息可能会因为推送服务配置错误或 Mobile Services 系统关闭而推送失败。
   >[!IMPORTANT]
   >
   >如果您遇到了异乎寻常的大量失败，请检查您的推送服务配置。如果推送服务看似配置正确，请联系 Adobe 客户关怀。

* **[!UICONTROL 已列入黑名单]**

   不再有效地发送到APNS或FCM的设备令牌数。这通常意味着该应用程序已从设备中卸载，或用户更改了用来接收消息的选择启用设置。对于在何时将令牌计入黑名单，Android 和 iOS 存在不同。Android 令牌会立即在列入黑名单的计数中显示。iOS 令牌最初会显示为已发布，但随后会根据来自 APNS 的反馈在后续消息中显示为已列入黑名单。
