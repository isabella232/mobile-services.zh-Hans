---
description: 帮助您实施Android生命周期指标的信息。 为iOS自动收集生命周期指标。
keywords: Xamarin
seo-description: 帮助您实施Android生命周期指标的信息。 为iOS自动收集生命周期指标。
seo-title: 实施生命周期
solution: Experience Cloud
title: 实施生命周期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 1%

---


# 实施生命周期 {#implement-lifecycle}

此信息可帮助您实施Android的生命周期指标。

>[!TIP]
>
>为iOS自动收集生命周期指标。

有关在实施生命周期后移动库可以自动衡量的指标和维度，请参 [阅生命周期](/help/ios/metrics.md)。

## iOS

在iOS中，生命周期指标会自动收集。

## Android

在主活动中，为Android SDK设置应用程序上下文。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

在每个活动实施生命周期调用。

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
