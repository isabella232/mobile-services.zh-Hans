---
description: 状态是指您的应用程序中的不同屏幕或视图。
seo-description: 状态是指您的应用程序中的不同屏幕或视图。
seo-title: 跟踪应用程序状态
solution: Experience Cloud,Analytics
title: 跟踪应用程序状态
topic: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 88%

---


# 跟踪应用程序状态 {#track-app-states}

状态是指您的应用程序中的不同屏幕或视图。

每当应用程序中显示了新状态（例如，用户从主页导航到新闻源）时，都会发送一个 `trackState` 调用。在 Android 中，每当加载新活动时，通常都会调用 `trackState`。

## 跟踪状态 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

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

在 Adobe Mobile Services 中，`"State Name"` 将在 `View State` 变量中进行报告，并且每个 `trackState` 调用均会记录一个视图。在其他 Analytics 界面中，`View State` 将被报告为 `Page Name`，`state views` 将被报告为 `page views`。

## 发送其他数据 {#section_CFDB4F944496401786A145C209AB387C}

除了 `"State Name"` 之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

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

## 应用程序状态报告 {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

状态通常通过使用路径报告来查看，该报告允许您查看用户如何导航您的应用程序以及最频繁查看的状态。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 视图状态]**&#x200B;报表。此报表基于用户在您的应用程序中浏览的路径。A sample path is  **[!UICONTROL Home]**  >  **[!UICONTROL Settings]**  > **[!UICONTROL Feed]**. |
| Adobe Analytics | 可以从任何能够查看页面的位置查看状态，如&#x200B;**[!UICONTROL 页面]**&#x200B;报表、**[!UICONTROL 页面查看次数]**&#x200B;报表和&#x200B;**[!UICONTROL 路径]**&#x200B;报表。 |
| Ad Hoc Analytics | 可以使用&#x200B;**[!UICONTROL 页面]**&#x200B;维度、**[!UICONTROL 页面查看次数]**&#x200B;量度和&#x200B;**[!UICONTROL 路径]**&#x200B;报表从任何能够查看页面的位置查看状态。 |


