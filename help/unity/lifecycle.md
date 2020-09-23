---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 实施生命周期
solution: Experience Cloud
title: 实施生命周期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 4%

---


# 实施生命周期{#implement-lifecycle}

有关在实施生命周期后移动库可以自动测量的指标和维度的更多信息，请参 [阅Android中的生命周期](/help/android/metrics.md)[指标或iOS中的生命周期](/help/ios/metrics.md)。

## iOS

生命周期指标会在iOS中自动收集。

## Android

在Unity脚本中，您为Android SDK设置应用程序上下文。 将以下代码添加 `Awake()` 到FIRST场景的函数：

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

要收集生命周期指标，请将以下代码添加到您的所有场景脚本中：

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

