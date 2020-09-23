---
description: 您可以发送信号并从受众管理中检索访客区段。
keywords: android;library;mobile;sdk
seo-description: 您可以发送信号并从受众管理中检索访客区段。
seo-title: Audience Manager 配置
solution: Experience Cloud,Analytics
title: Audience Manager 配置
topic: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%

---


# Audience Manager 配置{#audience-manager-configuration}

您可以发送信号并从 Audience Manager 中检索访客区段。

## 设置应用程序上下文 {#section_37CAE496FF894FCA821F7760605574CA}

**（必需）**&#x200B;必须在主活动的 `onCreate()` 方法中调用一次 `setContext()` 方法。

以下是此方法的代码示例：

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您在实施 Analytics 或 Target 时添加了此方法调用，则无需再次添加。
