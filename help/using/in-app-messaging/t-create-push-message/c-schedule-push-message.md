---
description: 在 Adobe Mobile Services UI 中，您可以将推送消息计划为立即传送、稍后传送以及定期传送。定期传送的周期可以为每天、每周或每月传送一次。
keywords: mobile
seo-description: 在 Adobe Mobile Services UI 中，您可以将推送消息计划为立即传送、稍后传送以及定期传送。定期传送的周期可以为每天、每周或每月传送一次。
seo-title: 计划推送消息
solution: Marketing Cloud，Analytics
title: 计划推送消息
topic: 量度
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# 计划：推送消息{#schedule-push-message}

在 Adobe Mobile Services UI 中，您可以将推送消息计划为立即传送、稍后传送以及定期传送。定期传送的周期可以为每天、每周或每月传送一次。

>[!TIP]
>
>用户可以随时修改推送消息作业的日程安排设置。如果没有适用的日期以供定期发送已计划的消息，例如，每月的第 31 天、2 月 31 日或当月的第 5 个星期二定期发送一次，则不发送消息。

请牢记以下信息：

* 正确的日期和时间格式是 `hh:mm` 和 `mm/dd/yyyy`。

* 您可以通过以下方式编辑计划的消息：

   * 将日期更改为以后日期。
   * 将重复时间间隔更改为其他时间间隔。

      例如，如果您原本每天发送一条消息，则可以将重复周期切换为每周发送。

## 计划循环推送消息之前

在计划定期推送消息之前，您&#x200B;**必须**&#x200B;了解以下信息：

* **[!UICONTROL 重复]下拉列表中显示的选项取决于您键入或选择的日期。**

   例如，如果键入 `Saturday, October 7`了以下选项，则会显示以下选项：

   * **[!UICONTROL 从不]**
   * **[!UICONTROL 每天]**
   * **[!UICONTROL 每个星期六]**
   * **[!UICONTROL 每月 7 日]**
   * **[!UICONTROL 每月第 1 个星期六]**

* 根据格林尼治标准时间 (GMT) 计划和发送推送消息。

   例如，如果您计划在每周六下午 12:00（中午）**(PST)** 定期发送消息，则从 10 月 7 日开始，将实际于星期六晚上 7:00 **(GMT)** 发送消息。
* 根据您位于美国、欧洲还是亚洲，发送消息的时间会有所不同。

   例如，如果您位于加利福尼亚州的圣何塞，并计划于 ***10 月 31 日***&#x200B;下午 5:30 **(PST)** 发送消息，则实际上会在 ***11 月 1 日***&#x200B;上午 12:30 **(GMT)** 发送消息。如果您位于东京，并计划在 ***1 月 1 日***&#x200B;上午 5:30 发送消息，则会在 ***12 月 31 日***&#x200B;晚上 8:30 **(GMT)** 发送消息。
* 根据夏令时的调整，将提前或推迟一小时发送推送消息。
* 您在查看推送消息报表时，消息将以系统的本地时区显示。

   例如，如果您的开始时间是中午 12:00 **(PST)**，尽管消息将在晚上 7:00 **(GMT)** 发送，但消息报表将会显示发送时间为中午 12:00 **(PST)**。

## Schedule a recurring push message {#section_675BD754E5A04423A1751193698A978F}

1. 在“计划”页面的新推送消息中，选择 **[!UICONTROL “计划”]** 或 **[!UICONTROL “现在]**”。

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   If you selected **[!UICONTROL Now]**, the message is pushed immediately. To prevent the message from being scheduled immediately, click **[!UICONTROL Save as Draft]**.

   ![](assets/schedule-push-message.png)

1. If you selected **[!UICONTROL Scheduled]**, click the calendar icon and select or type a start date.
1. 键入时间。 
1. Under **[!UICONTROL Repeat]**, select one of the following options:

   * **[!UICONTROL 从不]**
   * **[!UICONTROL 每天]**
   * **[!UICONTROL 每个星期二]**
   * **`<Day x>`当月中**

      显示的选项会根据您选择或键入的开始日期而发生更改。
   * **`<nth day>`每月的**

      显示的值会根据您选择或键入的开始日期而发生更改。

1. In **[!UICONTROL End Repeat]**, type an end date and time.
1. 单击以下选项之一：

   * **[!UICONTROL 另存为草稿]**

      此选项会将消息保存为草稿格式。您可以选择此选项来保存未完成的消息，或保存消息以便他人在激活它之前能够编辑或批准该消息。

      If you selected **[!UICONTROL Now]** in the previous step, the draft message is sent immediately on activation. 如果您选择了推送消息的日期和时间，则会根据此计划推送消息。

   * **[!UICONTROL 保存并计划]**

      此选项会在计划的日期和时间发送消息。

要稍后推送草稿消息，请完成以下任务之一：

* Click **[!UICONTROL Manage Messages]**, select the check box next to the message, and click **[!UICONTROL Activate Selected]**.
* 单击&#x200B;**[!UICONTROL 保存并发送]以保存消息并发送它。**
