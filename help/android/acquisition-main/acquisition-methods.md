---
description: '以下获取方法由Android库提供 '
keywords: android；库；移动；sdk
seo-description: '以下获取方法由Android库提供 '
seo-title: 客户获取方法
solution: Marketing Cloud，Analytics
title: 客户获取方法
topic: 开发人员和实施
uuid: 22ec432f-e7 ae-4e89-be07-26206bbkf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

以下获取方法由Android库提供：

* **campaignStartForApp**

   允许开发人员像用户单击链接一样，发起应用程序客户获取促销活动。这有助于您自行创建手动客户赢取链接并处理应用商店重定向。

   * 下面是这种方法对应的语法：

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
