---
description: 由 Windows 8.1 通用应用商店库提供的 Audience Manager 方法列表。
seo-description: 由 Windows 8.1 通用应用商店库提供的 Audience Manager 方法列表。
seo-title: Audience Manager方法
solution: Marketing Cloud，Analytics
title: Audience Manager方法
topic: 开发人员和实施
uuid: e39c9c3e-fd53-4b46-8fff-88101a064 a9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

由 Windows 8.1 通用应用商店库提供的 Audience Manager 方法列表。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。方法将根据解决方案来添加前缀。Audience Manager 方法具有“AudienceManager”前缀。

>[!NOTE]
>
>当您使用WinJS(JavaScript)中的winmd方法时，所有方法自动将其第一个字母小写。

如果在 JSON 文件中配置了 Audience Manager，则会随生命周期点击发送一个包含生命周期量度的信号。

* **getVisitorProfile(WinJS：getVisitorProfile)**

   返回最近获取的访客资料。如果尚未提交任何信号，则返回 `null`。访客资料保存在 `SharedPreferences` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **getDpid(WinJS：getDpid)**

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

* **getPuuID(WinJS：getPuuID)**

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

* **setDpIDAndPuuID(WinJS：setDpIDAndPuUI)**

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

* **SignalWithData(WinJS：signalWithData)**

   向 Audience Manager 发送一个具有特征的信号，并获取块回调中返回的匹配区段。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

