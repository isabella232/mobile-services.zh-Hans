---
description: 您可以在 Android 应用程序中提供目标内容。
keywords: Android;库;移动;SDK
solution: Experience Cloud,Analytics
title: Target 配置
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 100%

---

# Target 配置 {#target-configuration}

您可以在 Android 应用程序中提供目标内容。

## 设置应用程序上下文 {#section_37CAE496FF894FCA821F7760605574CA}

**（必需）**&#x200B;必须在主活动的 `onCreate()` 方法中调用一次 `setContext()` 方法。

例如：

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您在实施 Analytics 或受众管理时已经添加此方法调用，则无需再次添加。
