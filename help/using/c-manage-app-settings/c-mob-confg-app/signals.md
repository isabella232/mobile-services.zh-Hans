---
description: 回发允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 Mobile Services 以将自定义数据发送至第三方目标。
seo-description: 回发允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 Mobile Services 以将自定义数据发送至第三方目标。
seo-title: 配置回发
title: 配置回发
uuid: a026575c-057b-4868-b6 c8-9514cbc32 b4 d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

回发允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 Mobile Services 以将自定义数据发送至第三方目标。

>[!IMPORTANT]
>
>要使用回音，您必须安装4.6SDK或更高版本。有关更多信息，请参阅 [Android - 回发](/help/android/analytics-main/postbacks/postbacks.md)或 [iOS - 回发](/help/ios/analytics-main/postback/postback.md)。

1. 单击所需应用程序的名称以转到其“管理应用程序设置”页面，然后单击页面右上方的&#x200B;**管理回发**&#x200B;链接。
1. Click **[!UICONTROL Create Postback]**.
1. 在字段中键入以下信息：

   * **[!UICONTROL 回发类型]**

      Choose **[!UICONTROL Custom]**. 模板将在将来提供。

   * **[!UICONTROL 名称]**

      为回发指定描述性名称。

   * **[!UICONTROL URL]**

      指定有效的端点URL(根据GET请求需要适当的查询参数)。您从数据被发送到的参与方获取此 URL（广告服务器或您自己的端点）。`https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`例如，

   * **[!UICONTROL 上下文变量]**

      突出显示 URL 的某些部分，并从下拉列表中选择所需的上下文变量。您还可以将上下文变量插入到URL中，URL会用点击中的值替换所有模板变量。

   * **[!UICONTROL 添加帖子正文]**

      指定任何其他帖子正文内容，例如在帖子请求中。如果指定正文文本，请指定帖子正文的内容类型。例如：`application/json`。

   * **[!UICONTROL 超时（以秒为单位）]**

      指定等待回发的时间（以秒为单位）。

   * **[!UICONTROL 触发器]**

      指定一个或多个数据标记和触发回发的条件。For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. 您还可以指定激活回发的量度。For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL 特征]**
   指定可在消息触发后查看消息的对象。Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. 单击&#x200B;**[!UICONTROL 保存]**&#x200B;以创建回发，并将其添加到&#x200B;**管理回发]列表。[!UICONTROL **

   之后若要激活回发，请执行以下操作之一：

   * Select the checkbox next to the postback in the **[!UICONTROL Manage Postbacks]** list and click **[!UICONTROL Activate Selected]**.
   * 单击&#x200B;**[!UICONTROL 保存并激活]以保存您的更改，并立即激活回发。**
