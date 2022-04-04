---
description: 测量可由移动设备库自动测量的量度和维度
keywords: Unity
solution: Experience Cloud Services
title: 实施生命周期
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# 实施生命周期{#implement-lifecycle}

有关实施生命周期后可由移动设备库自动测量的量度和维度的更多信息，请参阅 [Android中的生命周期量度](/help/android/metrics.md) 或 [iOS中的生命周期](/help/ios/metrics.md).

## iOS

生命周期量度在iOS中自动收集。

## Android

在Unity脚本中，您为Android SDK设置应用程序上下文。 将以下代码添加到 `Awake()` 第一个场景的函数：

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
