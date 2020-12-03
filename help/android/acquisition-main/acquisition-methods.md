---
description: 'Android 库提供了以下客户获取方法 '
keywords: android;library;mobile;sdk
seo-description: 'Android 库提供了以下客户获取方法 '
seo-title: 客户获取方法
solution: Experience Cloud,Analytics
title: 客户获取方法
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---


# 客户获取方法{#acquisition-methods}

Android 库提供了以下客户获取方法：

* **campaignStartForApp**

   允许开发人员像用户单击链接一样，启动应用程序客户获取促销活动。这有助于您自行创建手动客户赢取链接并处理应用商店重定向。

   * 以下是此方法的语法：

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
