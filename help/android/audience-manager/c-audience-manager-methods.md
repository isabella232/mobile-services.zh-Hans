---
description: 以下是 Android 库提供的 Audience Manager 方法列表。
keywords: android；库；移动；sdk
seo-description: 以下是 Android 库提供的 Audience Manager 方法列表。
seo-title: Audience Manager方法
solution: Marketing Cloud，Analytics
title: Audience Manager方法
topic: 开发人员和实施
uuid: 2f6e4664-1306-41d4-9fa7-e3 a99 f1 df4 ab
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

以下是 Android 库提供的 Audience Manager 方法列表。

SDK目前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

如果在 JSON 文件中配置了 Audience Manager，则会随生命周期点击发送一个包含生命周期量度的信号。

* **getVisitorProfile**

   返回最近获取的访客资料，如果没有提交任何信号，则返回 `null`。访客资料保存在 `SharedPreferences` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   返回当前 DPID。

   * 下面是这种方法对应的语法：

      ```java
      public static void getDpid(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   返回当前 DPUUID。

   * 下面是这种方法对应的语法：

      ```java
      public static void getDpuuid(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   设置 DPID 和 DPUUID，这些值会随每个信号一起发送。

   如果传递给此方法的DPUUID值包含非URL安全字符，则客户必须对该参数进行编码，然后才能将其传递给SDK。

   * 下面是这种方法对应的语法：

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   向受众管理发送一个具有特征的信号，并获取块回调中返回的匹配区段。

   * 下面是这种方法对应的语法：

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * 以下是这种方法的代码示例：

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
