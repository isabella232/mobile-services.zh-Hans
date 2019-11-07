---
description: 'Android 库提供了以下客户获取方法 '
keywords: Android;库;移动;SDK
seo-description: 'Android 库提供了以下客户获取方法 '
seo-title: 客户获取方法
solution: Marketing Cloud,Analytics
title: 客户获取方法
topic: 开发人员和实施
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

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
