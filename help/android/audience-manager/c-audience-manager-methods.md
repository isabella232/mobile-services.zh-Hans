---
description: 以下是 Android 库提供的 Audience Manager 方法列表。
keywords: Android;库;移动;SDK
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
exl-id: 707b40b8-e56e-4c26-8b59-87c5d71cad0c
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 100%

---

# Audience Manager 方法{#audience-manager-methods}

以下是 Android 库提供的 Audience Manager 方法列表。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀。例如，Experience Cloud ID 方法的前缀为 `audience manager`。

如果在 JSON 文件中配置了 Audience Manager，则会随生命周期点击发送一个包含生命周期量度的信号。

* **getVisitorProfile**

   返回最近获取的访客资料，如果没有提交任何信号，则返回 `null`。访客资料保存在 `SharedPreferences` 中，以供在多次启动应用程序时轻松访问。

   * 以下是此方法的语法：

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   返回当前 DPID。

   * 以下是此方法的语法：

      ```java
      public static void getDpid(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   返回当前 DPUUID。

   * 以下是此方法的语法：

      ```java
      public static void getDpuuid(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   设置 DPID 和 DPUUID，这些值会随每个信号一起发送。

   如果传递到此方法的 DPUUID 值包含非 URL 安全字符，则客户必须先对该参数进行编码，然后再将其传递到 SDK。

   * 以下是此方法的语法：

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * 以下是此方法的代码示例：

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   向受众管理发送一个具有特征的信号，并获取块回调中返回的匹配区段。

   * 以下是此方法的语法：

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * 以下是此方法的代码示例：

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
