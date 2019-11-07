---
description: 您可以发送信号并从受众管理中检索访客区段。
keywords: Android;库;移动;SDK
seo-description: 您可以发送信号并从受众管理中检索访客区段。
seo-title: Audience Manager 配置
solution: Marketing Cloud,Analytics
title: Audience Manager 配置
topic: 开发人员和实施
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

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
