---
description: Windows8.1通用App Store库提供的Target方法列表。
seo-description: Windows8.1通用App Store库提供的Target方法列表。
seo-title: Target 方法
solution: Marketing Cloud，Analytics
title: Target 方法
topic: 开发人员和实施
uuid: 8c35b31c-c70 b-4dba-8759-173342a301 e9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods {#target-methods}

Windows8.1通用App Store库提供的Target方法列表。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。方法将根据解决方案来添加前缀。Analytics 方法具有“Target”前缀。

[生命周期量度](/help/windows-appstore/metrics.md)将作为参数发送至每个 mbox 负载。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## 类引用：targetLocationRequest

### 属性

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## String常量

此信息可帮助您设置自定义参数的密钥。

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest(WinJS：loadRequest)**

   向您配置的 Target 服务器发送 `request`，并返回在块 `callback` 中生成的选件的字符串值。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateEquest(WinJS：createRequest)**

   通过给定参数创建 `TargetLocationRequest` 对象。

   * 下面是这种方法对应的语法：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **createOrderConfirmRequest(WinJS：createOrderConfirmRequest)**

   通过给定参数创建 `TargetLocationRequest` 对象。

   * 下面是这种方法对应的语法：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **clearCookies(WinJS：clearCookies)**

   清除当前设备上的应用程序的 Target Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      static void ClearCookies(); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **getPCID(WinJS：getPCID)**

   返回当前设备的 PC ID Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * 以下是这种方法的代码示例：

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **getSessionID(WinJS：getSessionID)**

   返回当前设备的会话 ID Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

