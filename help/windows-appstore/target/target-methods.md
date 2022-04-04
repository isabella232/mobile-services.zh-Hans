---
description: Windows 8.1通用App Store库提供的Target方法列表。
solution: Experience Cloud Services,Analytics
title: Target 方法
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Target 方法 {#target-methods}

Windows 8.1通用App Store库提供的Target方法列表。

SDK当前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target和Audience Manager。 方法将根据解决方案来添加前缀。Analytics方法的前缀为“Target”。

[生命周期量度](/help/windows-appstore/metrics.md)将作为参数发送至每个 mbox 负载。

>[!TIP]
>
>您何时使用 `winmd` 方法(来自winJS(JavaScript))中，所有方法都会自动将其第一个字母小写。

## 类引用：TargetLocationRequest

### 属性

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 字符串常量

此信息可帮助您设置自定义参数的键。

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

   发送 `request` 返回在块中生成的选件的字符串值 `callback`.

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest(winJS:createRequest)**

   创建 `TargetLocationRequest` 对象。

   * 以下是此方法的语法：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **创建订&#x200B;单确认请求(winJS:createOrder &#x200B; ConfirmRequest)**

   创建 `TargetLocationRequest` 对象。

   * 以下是此方法的语法：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies(winJS:clearCookies)**

   清除当前设备上应用程序的Target Cookie。

   * 以下是此方法的语法：

      ```csharp
      static void ClearCookies(); 
      ```

   * 以下是此方法的代码示例：

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId(winJS:getPcId)**

   返回当前设备的PC ID Cookie。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * 以下是此方法的代码示例：

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId(winJS:getSessionId)**

   返回当前设备的会话ID Cookie。

   * 以下是此方法的语法：

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * 以下是此方法的代码示例：

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
