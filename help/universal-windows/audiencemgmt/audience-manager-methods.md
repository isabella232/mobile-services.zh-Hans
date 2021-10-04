---
description: 通用Windows平台库提供的Audience Manager方法列表。
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 44%

---

# Audience Manager 方法{#audience-manager-methods}

通用Windows平台库提供的Audience Manager方法列表。

SDK当前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target和Audience Manager。 方法将根据解决方案来添加前缀。Audience Manager方法的前缀为`AudienceManager`。

>[!TIP]
>
>当您从winJS(JavaScript)中使用`winmd`方法时，所有方法都会自动将其第一个字母小写。

如果在JSON文件中配置了audience manager，则会随生命周期点击发送一个包含生命周期量度的信号。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回`null`。 访客配置文件保存在`SharedPreferences`中，以便在多次启动应用程序时轻松访问。

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

   向受众管理发送一个具有特征的信号，并获取块回调中返回的匹配区段。

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
