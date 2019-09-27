---
description: 操作是指在您要测量的应用程序中发生的事件。每个操作均具有一个或多个对应的量度，每当发生事件时，这些量度的数量都会递增。例如，每当进行了新订阅、查看完文章或完成某个级别时，您都可以相应地进行跟踪。这些事件对应的量度分别配置为订阅数、阅读的文章数和完成的级别数。
seo-description: 操作是指在您要测量的应用程序中发生的事件。每个操作均具有一个或多个对应的量度，每当发生事件时，这些量度的数量都会递增。例如，每当进行了新订阅、查看完文章或完成某个级别时，您都可以相应地进行跟踪。这些事件对应的量度分别配置为订阅数、阅读的文章数和完成的级别数。
seo-title: 跟踪应用程序操作
solution: Marketing Cloud,Analytics
title: 跟踪应用程序操作
topic: 开发人员和实施
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 跟踪应用程序操作 {#track-app-actions}

操作是指在您要测量的应用程序中发生的事件。每个操作均具有一个或多个对应的量度，每当发生事件时，这些量度的数量都会递增。例如，每当进行了新订阅、查看完文章或完成某个级别时，您都可以相应地进行跟踪。这些事件对应的量度分别配置为订阅数、阅读的文章数和完成的级别数。

系统不会自动跟踪操作，因此要跟踪事件，您必须调用 `trackAction`。

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. 导入库。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 当您的应用程序中发生要跟踪的操作时，请调用 `trackAction` 以发送此操作的点击。

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >If the code where you are adding this call might run while the app is in the background, call `trackActionFromBackground` instead of `trackAction`.

1. In the Adobe Mobile services UI, select your app and click **[!UICONTROL Manage App Settings]**.

1. 单击&#x200B;**[!UICONTROL 管理变量和量度]**，然后再单击&#x200B;**自定义量度]选项卡。[!UICONTROL **

1. 将代码中定义的上下文数据名称（例如 `a.action=myapp.ActionName`）映射到某个自定义事件。

   ![](assets/map-event-context-data.png)

You can also set a prop to hold all action values by mapping a custom prop with a name like **[!UICONTROL Custom Actions]** and setting the value to `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了操作名称之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

上下文数据值必须映射到自定义变量：

![](assets/map-variable-context-action.png)

## Tracking background actions {#section_AC13013F207D4FBAAF27E4412034251E}

如果用于跟踪操作的代码可能会在应用程序处于后台时运行，请调用 `trackActionFromBackground`，而不是 `trackAction`。尽管 `trackActionFromBackground` 包含其他一些逻辑，可阻止生命周期调用在不应触发时被触发，但参数是相同的。

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| 界面 | 报表 |
|--- |--- |
| Adobe Mobile Services | ****&#x200B;操作路径报告. 查看操作在应用程序中发生的顺序。您还可以单击任何报表中的&#x200B;**[!UICONTROL 自定义]，以查看操作排名、趋势或在划分报表中查看操作，也可以应用过滤器以查看特定区段的操作。** |
| Marketing Reports and Analytics | **[!UICONTROL 自定义事件]**&#x200B;报表。在将操作映射到自定义事件后，您可以查看与所有其他 Analytics 事件类似的移动设备事件。 |
| Ad hoc analytics | **[!UICONTROL 自定义事件]**&#x200B;报表。在将操作映射到自定义事件后，您可以查看与所有其他 Analytics 事件类似的移动设备事件。 |