---
description: 操作是指您要测量的 Android 应用程序中发生的事件。
seo-description: 操作是指您要测量的 Android 应用程序中发生的事件。
seo-title: 跟踪应用程序操作
solution: Marketing Cloud，Analytics
title: 跟踪应用程序操作
topic: 开发人员和实施
uuid: fe01c1df-f6 bb-4b32-b3 ef-959d2 c724 af6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 跟踪应用程序操作 {#track-app-actions}

操作是指您要测量的 Android 应用程序中发生的事件。

每个操作均具有一个或多个对应的量度，每当发生事件时，这些量度的数量都会递增。例如，对于每个新订阅，每当查看文章时，或每当完成某个级别时，您都可以发送一个 `trackAction` 调用。系统不会自动跟踪操作，因此您必须在发生要跟踪的事件时调用 `trackAction`，并将操作映射到一个自定义事件。

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *在核心实施和生命周期* 中 [将SDK和Config文件添加到IntelliJ IDEA或Eclipse项目](/help/android/getting-started/dev-qs.md)。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 当您的应用程序中发生要跟踪的操作时，请调用 `trackAction` 以发送此操作的点击：

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. In the Adobe Mobile Services UI, select your app and click **[!UICONTROL Manage App Settings]**.
1. 单击&#x200B;**[!UICONTROL 管理变量和量度]**，然后再单击&#x200B;**自定义量度]选项卡。[!UICONTROL **

1. 将代码中定义的上下文数据名称（例如 `myapp.ActionName`）映射到某个自定义事件。

   ![](assets/map-event-context-data.png)

You can also set a prop to hold all action values by mapping a custom prop with a name like **[!UICONTROL Custom Actions]** and setting the value to `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了操作名称之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-context-action.png)

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| 界面 | 报表 |
|--- |--- |
| Adobe Mobile Services | ****&#x200B;操作路径报告.  查看操作在应用程序中发生的顺序。您还可以单击任何报表中的&#x200B;**[!UICONTROL 自定义]，以查看操作排名、趋势或在划分报表中查看操作，也可以应用过滤器以查看特定区段的操作。** |
| Marketing Reports &amp; Analytics | **[!UICONTROL 自定义事件]**&#x200B;报表。在将操作映射到自定义事件后，您可以查看与所有其他 Analytics 事件类似的移动设备事件。 |
| Ad hoc analytics | **[!UICONTROL 自定义事件]**&#x200B;报表。在将操作映射到自定义事件后，您可以查看与所有其他 Analytics 事件类似的移动设备事件。 |

