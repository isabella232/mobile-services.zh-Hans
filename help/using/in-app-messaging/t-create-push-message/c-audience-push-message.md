---
description: 您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。
keywords: mobile
seo-description: 您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。
seo-title: 受众定义和配置推送消息的受众细分
solution: Marketing Cloud，Analytics
title: 受众定义和配置推送消息的受众细分
topic: 量度
uuid: efd410e7-3b6c-4cf4-a26 f-b11688 adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# 受众：推送消息{#audience-define-and-configure-audience-segments-for-push-messages}

您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

在为推送消息创建受众区段时，该区段可能会涉及来自一个或多个应用程序的用户，这是因为报表包或虚拟报表包可能包含来自一个或多个应用程序的数据。有关虚拟报表包的更多信息，请参阅[虚拟报告套件](/help/using/manage-apps/c-mob-vrs.md)。

在 Adobe Mobile Services 中，营销人员只能将消息推送到每个平台的一个应用程序。如果营销人员尝试将消息推送到包含多个应用程序中用户的区段，则会显示一条警告消息，提醒继续操作会导致严重的推送失败，并且用户可能会被加入黑名单。如果遇到推送失败，请参阅“解决推送失败”**（位于[推送推送疑难解答](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)。

要在区段定义中使用 Audience Manager 数据，请参阅[受众分析](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html)。

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

如果您选择包含跨多个应用程序用户的受众细分，您可能会看到以下警告：

![多个应用程序名称](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>版本号为可选号。

最多会删除版本的 6 组数字和捆绑 ID 的 5 组数字。

例如：

* `Bea[rd]cons 1.0 (123)` 将显示为 `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` 将显示为 `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` 将显示为 `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` 将显示为 `Bea[rd]cons (.6)`

要继续将推送消息发送到列出的应用程序，请选择&#x200B;**是，我要继续。** 复选框，然后单击 **[!UICONTROL “发送]**”。

## 最佳实践

以下是一些最佳实践：

* 为了减少混淆，应&#x200B;**避免**&#x200B;定义包含多个应用程序中数据的移动设备应用程序虚拟报表包。
* **每次**&#x200B;要发送推送消息时，在受众区段中使用唯一的应用程序 ID。这可确保将推送通知发送到&#x200B;**仅**&#x200B;属于一个应用程序的受众区段。

### 示例

以下这些示例可帮助您了解如何正确定义区段：

**应做事项**：营销人员为一个应用程序（例如 Adobe Photoshop）的 iOS 和 Android 版本提供推送证书。营销人员可能会将推送通知发送到跨两个平台的用户区段。

**勿做事项**：多个营销人员为一个应用程序（例如 Adobe Photoshop）的 iOS 和 Android 版本提供推送证书。如果营销人员创建一个包含“最近 30 天内所有活动用户”**&#x200B;的区段，并将消息推送至该区段，则只有 Adobe Photoshop iOS 和 Android 应用程序的用户才能收到推送消息，且所有的 Adobe Illustrator iOS 和 Android 应用程序用户将被列入黑名单。有关更详细的示例，请参阅“解决推送消息失败”**（位于[排查推送消息问题](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md)中）。

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. 转到“受众”页面以获取新推送消息。

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * **[!UICONTROL 预计的选择启用受众]**&#x200B;是指与 Adobe Analytics 区段匹配的设备数量&#x200B;**和**&#x200B;选择启用的设备数量。

      您可以查看选定区段内选择接收消息并将接收推送消息的预计用户数量。应用程序用户的总数量显示低于预期，无论其选择启用状态如何。

   * **[!UICONTROL 合计]是与 Adobe Analytics 区段匹配的设备数量。**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      这意味着 SDK 为推送消息选择启用 evar 发送了值 `True`。

   * 虽然设备具有有效的设备令牌，但除非Adobe Analytics已设置了已选择加入的标志，否则该消息不会推送到设备。

   * 有关排查推送消息问题的更多信息，请参阅以下内容：

      * [在iOS中推送消息](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [在Android中推送消息](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. 在以下字段中键入相应信息：

   * **[!UICONTROL 时段]**

      键入将用于预计受众的时间范围。从&#x200B;**[!UICONTROL 时段:]下拉列表中选择一个属性：**

   * **[!UICONTROL 最近]**&#x200B;允许您从计划推送消息的时间中选择一个相对的时间范围（例如，最近 7 天、最近 30 天或最近 60 天）。

      例如，如果您选择最近 30 天，并计划在 10 月 31 日推送消息，则预计受众将是选择在 10 月 31 日前 30 天内接收推送消息的用户数量。

   * **[!UICONTROL 静态范围]**&#x200B;允许您通过选取预计受众范围的起始和结束日期，来选择一个静态范围。

      对于上述示例，如果您选择起始于 10 月 1 日并结束于 10 月 15 日的日期范围，但计划在 10 月 31 日推送消息，预计受众将是选择在您指定的静态日期范围内（10 月 1 日至 10 月 15 日）接收推送消息的用户数量。

   * **[!UICONTROL Analytics 区段]**

      从下拉列表中选择现有的Adobe Analytics区段。For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL 自定义区段]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. 例如以下自定义区段目标用户，他们拥有运行 iOS 的手机并位于加利福利亚（美国）地区之内。
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
