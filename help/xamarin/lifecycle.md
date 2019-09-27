---
description: 有关帮助实施适用于 Android 的生命周期量度的信息。对于 iOS，将自动收集生命周期量度。
keywords: Xamarin
seo-description: 有关帮助实施适用于 Android 的生命周期量度的信息。对于 iOS，将自动收集生命周期量度。
seo-title: 实施生命周期
solution: Marketing Cloud,Developer
title: 实施生命周期
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

This information helps you implement Lifecycle metrics for Android.

>[!TIP]
>
>对于 iOS，将自动收集生命周期量度。

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

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

In every activity, implement lifecycle calls.

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
