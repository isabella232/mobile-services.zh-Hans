---
description: 由通用 Windows 平台库提供的 Target 方法列表。
seo-description: 由通用 Windows 平台库提供的 Target 方法列表。
seo-title: Target 方法
solution: Marketing Cloud,Analytics
title: Target 方法
topic: 开发人员和实施
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods {#target-methods}

由通用 Windows 平台库提供的 Target 方法列表。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。

[生命周期指标](/help/universal-windows/metrics.md) (Lifecycle metrics)作为参数发送到每个mbox加载。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## 类引用：TargetLocationRequest

## 资产

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 字符串常量

此信息可帮助您为自定义参数设置键。

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

* **LoadRequest(winJS:loadRequest)**

   向您配置的 Target 服务器发送 `request`，并返回在块 `callback` 中生成的选件的字符串值。

   * 下面是这种方法对应的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 以下是这种方法的代码示例：

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest(winJS:createRequest)**

   通过给定参数创建 `TargetLocationRequest` 对象。

   * 下面是这种方法对应的语法：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder&#x200B;ConfirmRequest (winJS: createOrder&#x200B;ConfirmRequest)**

   通过给定参数创建 `TargetLocationRequest` 对象。

   * 下面是这种方法对应的语法：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies (winJS: clearCookies)**

   清除当前设备上的应用程序的 Target Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      static void ClearCookies();
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   返回当前设备的 PC ID Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * 以下是这种方法的代码示例：

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId (winJS: getSessionId)**

   返回当前设备的会话 ID Cookie。

   * 下面是这种方法对应的语法：

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 以下是这种方法的代码示例：

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```

