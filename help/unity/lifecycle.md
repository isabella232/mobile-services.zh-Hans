---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 实现生命周期
solution: Marketing Cloud，开发人员
title: 实现生命周期
uuid: 7ff2c194-569c-42a6-922d-dcr2 aa9 eb8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 实现生命周期{#implement-lifecycle}

有关在实现生命周期后可由移动库自动测量的指标和维度的更多信息，请参阅iOS中的 [生命周期指标](/help/android/metrics.md) 或 [生命周期](/help/ios/metrics.md)。

## iOS

生命周期指标在iOS中自动收集。

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

