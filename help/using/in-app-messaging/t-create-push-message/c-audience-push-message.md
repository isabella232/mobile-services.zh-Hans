---
description: 您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。
keywords: mobile
seo-description: 您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。
seo-title: 受众：为推送消息定义和配置受众区段
solution: Marketing Cloud,Analytics
title: 受众：为推送消息定义和配置受众区段
topic: 量度
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: ht
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# 受众：推送消息{#audience-define-and-configure-audience-segments-for-push-messages}

您可以为推送消息定义和配置受众选项，包括日期范围选项、Analytics 区段和自定义区段。

## 定义受众区段 {#section_7C4D2393CF7441959FE2381A02867CAC}

在为推送消息创建受众区段时，该区段可能会涉及来自一个或多个应用程序的用户，这是因为报表包或虚拟报表包可能包含来自一个或多个应用程序的数据。有关虚拟报表包的更多信息，请参阅[虚拟报表包](/help/using/manage-apps/c-mob-vrs.md)。

在 Adobe Mobile Services 中，营销人员只能将消息推送到每个平台的一个应用程序。如果营销人员尝试将消息推送到包含多个应用程序中用户的区段，则会显示一条警告消息，提醒继续操作会导致严重的推送失败，并且用户可能会被加入黑名单。如果遇到推送失败，请参阅“解决推送失败”**（位于[排查推送消息问题](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)中）。

要在区段定义中使用 Audience Manager 数据，请参阅[受众分析](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html)。

>[!IMPORTANT]
>
>如果应用程序用户被列入黑名单，则营销人员再也&#x200B;**不**&#x200B;能向这些受影响的用户发送推送消息。

如果您选择的受众区段包含跨多个应用程序的用户，则可能会看到以下提醒：

![多个应用程序名称](assets/multiple_appname.png)

应用程序名称基于 appId 的精简版，由 Mobile Services SDK 以 `<app name> <version number> (<bundle id>)` 格式自动发送到 Adobe Analytics。

>[!TIP]
>
>版本号为可选参数。

最多会删除版本的 6 组数字和捆绑 ID 的 5 组数字。

例如：

* `Bea[rd]cons 1.0 (123)` 将显示为 `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` 将显示为 `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` 将显示为 `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` 将显示为 `Bea[rd]cons (.6)`

要继续将推送消息发送到列出的应用程序，请选择&#x200B;**是，我要继续。**&#x200B;复选框，然后单击&#x200B;**[!UICONTROL 发送]**。

## 最佳实践

请牢记以下一些最佳实践：

* 为了减少混淆，应&#x200B;**避免**&#x200B;定义包含多个应用程序中数据的移动设备应用程序虚拟报表包。
* **每次**&#x200B;要发送推送消息时，在受众区段中使用唯一的应用程序 ID。这可确保将推送通知发送到&#x200B;**仅**&#x200B;属于一个应用程序的受众区段。

### 示例

以下这些示例可帮助您了解如何正确定义区段：

**应做事项**：营销人员为一个应用程序（例如 Adobe Photoshop）的 iOS 和 Android 版本提供推送证书。营销人员可能会将推送通知发送到跨两个平台的用户区段。

**勿做事项**：多个营销人员为一个应用程序（例如 Adobe Photoshop）的 iOS 和 Android 版本提供推送证书。如果营销人员创建一个包含“最近 30 天内所有活动用户”**&#x200B;的区段，并将消息推送至该区段，则只有 Adobe Photoshop iOS 和 Android 应用程序的用户才能收到推送消息，且所有的 Adobe Illustrator iOS 和 Android 应用程序用户将被列入黑名单。有关更详细的示例，请参阅“解决推送消息失败”**（位于[排查推送消息问题](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md)中）。

## 配置受众区段 {#section_A92C60885A30421B8150820EC1CCBF13}

1. 转到“受众”页面以获取新的推送消息。

   有关更多信息，请参阅[创建推送消息](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md)。

   在配置受众选项时，请记住以下“重要”****&#x200B;信息：

   * **[!UICONTROL 预计的选择启用受众]**&#x200B;是指与 Adobe Analytics 区段匹配的设备数量&#x200B;**和**&#x200B;选择启用的设备数量。

      您可以查看选定区段内选择接收消息并将接收推送消息的预计用户数量。应用程序用户的总数量显示低于预期，无论其选择启用状态如何。

   * **[!UICONTROL 合计]**&#x200B;是与 Adobe Analytics 区段匹配的设备数量。

   * 推送消息会被发送到定义的 Adobe Analytics 区段所包含的设备&#x200B;**以及**&#x200B;已选择启用推送消息的设备。

      这意味着 SDK 为推送消息选择启用 evar 发送了值 `True`。

   * 即使设备具有有效的设备令牌，但除非 Adobe Analytics 设置了选择启用标志，否则不会将消息推送至该设备。

   * 有关排查推送消息问题的更多信息，请参阅以下内容：

      * [iOS 中的推送消息](https://docs.adobe.com/content/help/zh-Hans/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Android 中的推送消息](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. 在以下字段中键入相应信息：

   * **[!UICONTROL 时段]**

      键入将用于预计受众的时间范围。从&#x200B;**[!UICONTROL 时段:]** 下拉列表中选择一个属性：

   * **[!UICONTROL 最近]**&#x200B;允许您从计划推送消息的时间中选择一个相对的时间范围（例如，最近 7 天、最近 30 天或最近 60 天）。

      例如，如果您选择最近 30 天，并计划在 10 月 31 日推送消息，则预计受众将是选择在 10 月 31 日前 30 天内接收推送消息的用户数量。

   * **[!UICONTROL 静态范围]**&#x200B;允许您通过选取预计受众范围的起始和结束日期，来选择一个静态范围。

      对于上述示例，如果您选择起始于 10 月 1 日并结束于 10 月 15 日的日期范围，但计划在 10 月 31 日推送消息，预计受众将是选择在您指定的静态日期范围内（10 月 1 日至 10 月 15 日）接收推送消息的用户数量。

   * **[!UICONTROL Analytics 区段]**

      从下拉列表中选择一个现有的 Adobe Analytics 区段。有关更多信息，请参阅[构建区段](https://docs.adobe.com/content/help/zh-Hans/analytics/components/segmentation/segmentation-workflow/seg-build.html)。

   * **[!UICONTROL 自定义区段]**

      从下拉列表中选择一个量度或变量（例如，**[!UICONTROL 上次使用后间隔天数]**&#x200B;或&#x200B;**[!UICONTROL 目标点]**），然后根据需要配置过滤器。例如以下自定义区段目标用户，他们拥有运行 iOS 的手机并位于加利福利亚（美国）地区之内。
   >[!IMPORTANT]
   >
   >在&#x200B;**[!UICONTROL 创建受众]**&#x200B;部分中，如果您单击&#x200B;**[!UICONTROL 和]**，系统会显示一个对话框，提醒您确保列出的每个应用程序都&#x200B;**必须**&#x200B;拥有一个有效证书。如果您单击&#x200B;**[!UICONTROL 或]**，则会出现默认对话框。有关有效证书和报表包的更多信息，请参阅[虚拟报表包](/help/using/manage-apps/c-mob-vrs.md)。
