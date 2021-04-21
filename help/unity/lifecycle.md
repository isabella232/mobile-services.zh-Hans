---
description: 衡量可由移动库自动衡量的指标和维度
keywords: Unity
solution: Experience Cloud
title: 实施生命周期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# 实施生命周期{#implement-lifecycle}

有关在实施生命周期后移动库可以自动测量的量度和维度的详细信息，请参阅[Android](/help/android/metrics.md)或iOS](/help/ios/metrics.md)中的[Lifecycle中的生命周期量度。

## iOS

在iOS中会自动收集生命周期量度。

## Android

在Unity脚本中，您为Android SDK设置应用程序上下文。 将以下代码添加到FIRST场景的`Awake()`函数：

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

要收集生命周期量度，请将以下代码添加到您的所有场景脚本中：

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
