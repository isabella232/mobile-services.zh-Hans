---
description: 列表通用Windows平台库提供的目标方法。
seo-description: 列表通用Windows平台库提供的目标方法。
seo-title: Target 方法
solution: Experience Cloud,Analytics
title: Target 方法
topic-fix: Developer and implementation
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
exl-id: d7aeee41-1c34-4f98-8455-e9f429287cfc
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 36%

---

# Target 方法 {#target-methods}

列表通用Windows平台库提供的目标方法。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。

[生命](/help/universal-windows/metrics.md) 周期量度作为参数发送到每个mbox加载。

>[!TIP]
>
>当您从winJS(JavaScript)使用`winmd`方法时，所有方法都会自动将其第一个字母小写。

## 类引用：TargetLocationRequest

## 属性

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

   将`request`发送到配置的目标服务器，并返回块`callback`中生成的优惠的字符串值。

   * 以下是此方法的语法：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 以下是此方法的代码示例：

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest(winJS:createRequest)**

   使用给定参数创建`TargetLocationRequest`对象。

   * 以下是此方法的语法：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest(winJS:createOrder &#x200B; ConfirmRequest)**

   使用给定参数创建`TargetLocationRequest`对象。

   * 以下是此方法的语法：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是此方法的代码示例：

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies(winJS:clearCookies)**

   清除当前设备上目标的应用程序Cookie。

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
      staticPlatform::String ^GetPcId();
      ```

   * 以下是此方法的代码示例：

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId(winJS:getSessionId)**

   返回当前设备的会话ID Cookie。

   * 以下是此方法的语法：

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 以下是此方法的代码示例：

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```
