---
description: 您可以查看应用程序内消息和推送消息的消息报表。
keywords: mobile
seo-description: 您可以查看应用程序内消息和推送消息的消息报表。
seo-title: View message reports
solution: Marketing Cloud,Analytics
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

   For more information about creating a sticky filter, see Add a sticky filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)

>[!TIP]
>
>根据您查看的消息类型，报告可能会有所不同。

## In-app messages {#section_90B79BA58E8141F78538C187EB1BF8C7}

如果您查看的是应用程序内消息的报表，则该报表类似于以下插图：

![report message](assets/report_message.png)

### In-app message metrics

Here is a list of the metrics that are available for in-app messages:

* **[!UICONTROL 印象]**，消息触发时。

* **[!UICONTROL 点进]**，当用户按下警报或全屏消息上的“点进 **** ”按钮时，以及用户从本地通知打开应用程序时。

* **[!UICONTROL 取消]**，当用户按下警报或全 **[!UICONTROL 屏消息上的]** “取消”按钮时。

* **[!UICONTROL 参与率]**,Adobe Analytics的一个计算量度，它是点击次数除以展示次数的结果。

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

如果您查看的是推送消息的报表，则该报表类似于以下插图：

![推送消息](assets/report_message_push.png)

顶部的图表显示了已打开消息的用户数量。

### Push message metrics

Here is a list of the metrics that are available for push messages:

* **[!UICONTROL 时间]**

   将消息从 Mobile Services 推送到设备的时间。

* **[!UICONTROL 状态]**

   The status of the message, and the available statuses are:

   * **[!UICONTROL Cancelled]**
   * **[!UICONTROL 已计划]**
   * **[!UICONTROL Executing]**
   * **[!UICONTROL 已执行]**

* **[!UICONTROL 已发布]**

   成功发送到Apple Push Notification Service/Firebase Cloud Messaging(APNS/FCM)以向用户设备发送消息的设备令牌数。

* **[!UICONTROL 失败]**

   The number of device tokens not successfully sent to APNS/FCM. 失败的一些可能原因：

   * pushID 无效

   * 为作业应用程序提供的推送平台（APNS、FCM等）不存在。 例如，此平台可收集 iOS 推送令牌但并未配置 APNS 服务。

   * 消息可能会因为推送服务配置错误或 Mobile Services 系统关闭而推送失败。
   >[!IMPORTANT]
   >
   >如果您遇到了异乎寻常的大量失败，请检查您的推送服务配置。如果推送服务看似配置正确，请联系 Adobe 客户关怀。

* **[!UICONTROL 已列入黑名单]**

   不再有效的设备令牌数发送到APNS或FCM。 这通常意味着该应用程序已从设备中卸载，或用户更改了用来接收消息的选择启用设置。对于在何时将令牌计入黑名单，Android 和 iOS 存在不同。Android 令牌会立即在列入黑名单的计数中显示。iOS 令牌最初会显示为已发布，但随后会根据来自 APNS 的反馈在后续消息中显示为已列入黑名单。
