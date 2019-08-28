---
description: 状态是指您的应用程序中的不同屏幕或视图。每当应用程序中显示了新状态（例如，用户从主页导航到新闻源）时，都应发送一个跟踪状态调用。在 iOS 中，通常会在每个视图的 viewDidLoad 方法中跟踪状态。
seo-description: 状态是指您的应用程序中的不同屏幕或视图。每当应用程序中显示了新状态（例如，用户从主页导航到新闻源）时，都应发送一个跟踪状态调用。在 iOS 中，通常会在每个视图的 viewDidLoad 方法中跟踪状态。
seo-title: 跟踪应用程序状态
solution: Marketing Cloud，Analytics
title: 跟踪应用程序状态
topic: 开发人员和实施
uuid: 12cca4eb-1f15-4cec-a58 f-76b69 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 跟踪应用程序状态 {#track-app-states}

状态是指您的应用程序中的不同屏幕或视图。每当应用程序中显示了新状态（例如，用户从主页导航到新闻源）时，都应发送一个跟踪状态调用。在 iOS 中，通常会在每个视图的 viewDidLoad 方法中跟踪状态。

>[!TIP]
>
>To track states, make a call to `trackState`. 不会自动跟踪状态。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *将SDK和配置文件添加到核心实施和生命周期* 中 [的项目](/help/ios/getting-started/dev-qs.md)。
1. 导入库。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 调用 `trackState` 以便为此状态视图发送点击。

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In Adobe Mobile services, the **[!UICONTROL State Name]** is reported in the *`View State`* variable, and a view is recorded for each `trackState` call. 在其他 Analytics 界面中，“**[!UICONTROL 视图状态]**”将被报告为“**[!UICONTROL 页面名称]**”，“状态查看次数”将被报告为“页面查看次数”。

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

上下文数据值必须映射到自定义变量：

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

状态通常使用路径报表来查看，以便您能够查看用户在应用程序中导航的方式以及最常查看的状态。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 视图状态]报表。**&#x200B;此报表基于用户在您的应用程序中浏览的路径。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 可以从任何能够查看页面的位置查看状态，如&#x200B;**页面**&#x200B;报表、**[!UICONTROL 页面查看次数]**&#x200B;报表和&#x200B;**路径[!UICONTROL 报表。]** |
| Ad hoc analytics | 可以从任何能够使用&#x200B;**页面**&#x200B;维度、**[!UICONTROL 页面查看次数]**&#x200B;量度和&#x200B;**路径[!UICONTROL 报表查看页面的位置查看状态。]** |
