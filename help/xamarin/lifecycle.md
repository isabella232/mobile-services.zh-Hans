---
description: 此信息可帮助您实施适用于Android的生命周期量度。 将自动为iOS收集生命周期量度。
keywords: 沙马林
solution: Experience Cloud Services
title: 实施生命周期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# 实施生命周期 {#implement-lifecycle}

此信息可帮助您为Android实施生命周期量度。

>[!TIP]
>
>将自动为iOS收集生命周期量度。

有关实施生命周期后可由移动设备库自动测量的量度和维度，请参阅 [生命周期量度](/help/ios/metrics.md).

## iOS

在iOS中，会自动收集生命周期量度。

## Android

在您的主活动中，设置Android SDK的应用程序上下文。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

在每个活动中实施生命周期调用。

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
