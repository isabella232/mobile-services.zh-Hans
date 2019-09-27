---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 实现生命周期
solution: Marketing Cloud，开发人员
title: 实现生命周期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 实现生命周期{#implement-lifecycle}

有关在实施生命周期后由移动库自动测量的指标和维度的详细信息，请参阅Android中的生命周期指标 [或iOS中](/help/android/metrics.md) 的生命周期 [](/help/ios/metrics.md)。

## iOS

Lifecycle metrics are automatically collected in iOS.

## Android

在您的 Unity 脚本中，您可以设置适用于 Android SDK 的应用程序上下文。Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

要收集生命周期量度，请将下列代码添加到您的所有场景脚本中：

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

