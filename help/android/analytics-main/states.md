---
description: 状态是指您的应用程序中的不同屏幕或视图。
seo-description: 状态是指您的应用程序中的不同屏幕或视图。
seo-title: 跟踪应用程序状态
solution: Marketing Cloud，Analytics
title: 跟踪应用程序状态
topic: 开发人员和实施
uuid: 69c99d05-5816-4c86-97c5-d218 dc26 c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 跟踪应用程序状态 {#track-app-states}

状态是指您的应用程序中的不同屏幕或视图。

每当应用程序中显示了新状态（例如，用户从主页导航到新闻源）时，都会发送一个 `trackState` 调用。在 Android 中，每当加载新活动时，通常都会调用 `trackState`。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *在核心实施和生命周期* 中 [将SDK和Config文件添加到IntelliJ IDEA或Eclipse项目](/help/android/getting-started/dev-qs.md)。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 在 `onCreate` 函数中，调用 `trackState` 以便为此状态视图发送点击：

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. 在其他Analytics界面 `View State` 中，报告为 `Page Name`， `state views` 并报告为 `page views`。

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

状态通常使用路径报表来查看，该报表允许您查看用户在应用程序中导航的方式以及最常查看的状态。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 视图状态]报表。**&#x200B;此报表基于用户在您的应用程序中浏览的路径。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 可以从任何能够查看页面的位置查看状态，如&#x200B;**页面**&#x200B;报表、**[!UICONTROL 页面查看次数]**&#x200B;报表和&#x200B;**路径[!UICONTROL 报表。]** |
| Ad hoc analytics | 可以从任何能够使用&#x200B;**页面**&#x200B;维度、**[!UICONTROL 页面查看次数]**&#x200B;量度和&#x200B;**路径[!UICONTROL 报表查看页面的位置查看状态。]** |


