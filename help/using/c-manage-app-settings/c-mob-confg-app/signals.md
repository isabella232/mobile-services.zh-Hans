---
description: 回传允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以将 Mobile Services 配置为将自定义数据发送至第三方目标。
seo-description: 回传允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以将 Mobile Services 配置为将自定义数据发送至第三方目标。
seo-title: 配置回发
title: 配置回发
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '474'
ht-degree: 100%

---


# 配置回发 {#configure-postbacks}

回传允许您将 Adobe Mobile 收集的数据发送至单独的第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以将 Mobile Services 配置为将自定义数据发送至第三方目标。

>[!IMPORTANT]
>
>要使用回发，您必须安装 SDK 4.6 或更高版本。有关更多信息，请参阅 [Android - 回发](/help/android/analytics-main/postbacks/postbacks.md)或 [iOS - 回发](/help/ios/analytics-main/postback/postback.md)。

1. 单击所需应用程序的名称以转到其“管理应用程序设置”页面，然后单击页面右上方的&#x200B;**[!UICONTROL 管理回发]**&#x200B;链接。
1. 单击&#x200B;**[!UICONTROL 创建回发]**。
1. 在字段中键入以下信息：

   * **[!UICONTROL 回发类型]**

      选择&#x200B;**[!UICONTROL 自定义]**。模板将在将来提供。

   * **[!UICONTROL 名称]**

      为回发指定描述性名称。

   * **[!UICONTROL URL]**

      指定一个有效的端点 URL（以及 GET 请求所需的相应查询参数）。您从数据被发送到的参与方获取此 URL（广告服务器或您自己的端点）。例如：`https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`。

   * **[!UICONTROL 上下文变量]**

      突出显示 URL 的某些部分，并从下拉列表中选择所需的上下文变量。您还可以将上下文变量插入到 URL 中，该 URL 将使用来自点击的值替换所有模板变量。

   * **[!UICONTROL 添加帖子正文]**

      指定任何其他帖子正文内容，例如在帖子请求中。如果您指定帖子正文文本，请指定帖子正文的内容类型。例如：`application/json`。

   * **[!UICONTROL 超时（以秒为单位）]**

      指定等待回发的时间（以秒为单位）。

   * **[!UICONTROL 触发器]**

      指定一个或多个数据标记和触发回发的条件。例如，您可以选择&#x200B;**[!UICONTROL 已崩溃]**&#x200B;作为触发器，选择&#x200B;**[!UICONTROL 存在]**&#x200B;作为条件，以便在应用程序崩溃时触发回发。您还可以指定激活回发的量度。例如，您可以选择&#x200B;**[!UICONTROL 设备名称]**&#x200B;作为触发器，选择&#x200B;**[!UICONTROL 等于]**&#x200B;以及 **[!UICONTROL iPhone 6 Plus]** 作为条件，以便当应用程序在 iPhone 6 Plus 设备上崩溃时激活回发。

   * **[!UICONTROL 特征]**
   指定可在消息触发后查看消息的对象。选项包括&#x200B;**[!UICONTROL 会话时长]**、**[!UICONTROL 首次启动日期]**&#x200B;和&#x200B;**[!UICONTROL 应用程序 ID]**。

1. 单击&#x200B;**[!UICONTROL 保存]**&#x200B;以创建回发，并将其添加到&#x200B;**[!UICONTROL 管理回发]**&#x200B;列表。

   之后若要激活回发，请执行以下操作之一：

   * 选中&#x200B;**[!UICONTROL 管理回发]**&#x200B;列表中的回发旁边的复选框，然后单击&#x200B;**[!UICONTROL 激活选定项]**。
   * 单击&#x200B;**[!UICONTROL 保存并激活]**&#x200B;以保存您的更改，并立即激活回发。
