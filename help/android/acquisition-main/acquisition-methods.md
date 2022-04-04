---
description: 'Android 库提供了以下客户获取方法 '
keywords: Android;库;移动;SDK
solution: Experience Cloud Services,Analytics
title: 客户获取方法
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '74'
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
