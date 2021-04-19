---
description: 列表通用Windows平台库提供的Audience Manager方法。
seo-description: 列表通用Windows平台库提供的Audience Manager方法。
seo-title: Audience Manager 方法
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---

# Audience Manager 方法{#audience-manager-methods}

列表通用Windows平台库提供的Audience Manager方法。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。 根据解预定方法。Audience Manager方法以`AudienceManager`为前缀。

>[!TIP]
>
>当您从winJS(JavaScript)使用`winmd`方法时，所有方法都会自动将其第一个字母小写。

如果在JSON文件中配置了受众管理器，则包含生命周期量度的信号会随生命周期点击一起发送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回`null`。 访客用户档案保存在`SharedPreferences`中，以便在多个应用程序启动时轻松访问。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid(winJS:getDpid)**

   返回当前 DPID。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid(winJS:getDpuuid)**

   返回当前 DPUUID。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid(winJS:setDpidAndDpuuid)**

   设置 DPID 和 DPUUID。如果设置了 DPID 和 DPUUID，则它们将随每个信号一起发送。

   * 以下是此方法的语法：

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData(winJS:signalWithData)**

   向受众管理发送具有特征的信号，并在块回调中获取返回的匹配段。

   * 以下是此方法的语法：

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```
