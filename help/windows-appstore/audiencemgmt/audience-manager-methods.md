---
description: 列表Windows 8.1通用应用商店库提供的Audience Manager方法。
seo-description: 列表Windows 8.1通用应用商店库提供的Audience Manager方法。
seo-title: Audience Manager 方法
solution: Marketing Cloud,Analytics
title: Audience Manager 方法
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Audience Manager 方法 {#audience-manager-methods}

列表Windows 8.1通用应用商店库提供的Audience Manager方法。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。 方法将根据解决方案来添加前缀。Audience Manager方法前缀为“AudienceManager”。

>[!NOTE]
>
>当您使用winJS(JavaScript)中的winmd方法时，所有方法都自动将其第一个字母小写。

如果在JSON文件中配置了受众管理器，则包含生命周期指标的信号会随生命周期点击发送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   返回最近获取的访客资料。Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * 以下是此方法的语法：

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
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

   发送Audience Manager具有特征的信号，并在块回调中获取返回的匹配段。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

