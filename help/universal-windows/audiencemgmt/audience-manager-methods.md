---
description: 由通用 Windows 平台库提供的 Audience Manager 方法列表。
seo-description: 由通用 Windows 平台库提供的 Audience Manager 方法列表。
seo-title: Audience manager方法
solution: Marketing Cloud,Analytics
title: Audience manager方法
topic: 开发人员和实施
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

由通用 Windows 平台库提供的 Audience Manager 方法列表。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。方法将根据解决方案来添加前缀。Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

如果在JSON文件中配置了Audience Manager，则包含生命周期指标的信号会随生命周期点击发送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回 `null`。访客资料保存在 `SharedPreferences` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid(winJS:getDpid)**

   返回当前 DPID。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid(winJS:getDpuuid)**

   返回当前 DPUUID。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid(winJS:setDpidAndDpuuid)**

   设置 DPID 和 DPUUID。如果设置了 DPID 和 DPUUID，它们将与每个信号一起发送。

   * 下面是这种方法对应的语法：

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData(winJS:signalWithData)**

   向受众管理发送一个具有特征的信号，并获取块回调中返回的匹配区段。

   * 下面是这种方法对应的语法：

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      
