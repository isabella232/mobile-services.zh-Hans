---
description: 您可以发送信号并从受众管理中检索访客区段。
keywords: android；库；移动；sdk
seo-description: 您可以发送信号并从受众管理中检索访客区段。
seo-title: Audience manager配置
solution: Marketing Cloud,Analytics
title: Audience manager配置
topic: 开发人员和实施
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

您可以从Audience manager发送信号并检索访客细分。

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**（必需）** ，在主 `setContext()` 活动的方法中必须调用 `onCreate()` 该方法一次。

以下是这种方法的代码示例：

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

如果您在实施Analytics或Target时添加了此方法调用，则无需再添加它。
