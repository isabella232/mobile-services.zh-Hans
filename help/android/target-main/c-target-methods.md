---
description: 以下是 Android 库提供的 Adobe Target 方法列表。
keywords: android;library;mobile;sdk
seo-description: 以下是 Android 库提供的 Adobe Target 方法列表。
seo-title: 适用于 Android 的 Target 方法
solution: Marketing Cloud,Analytics
title: 适用于 Android 的 Target 方法
topic: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '603'
ht-degree: 100%

---


# 适用于 Android 的 Target 方法{#target-methods}

以下是 Android 库提供的 Adobe Target 方法列表。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀。例如，Experience Cloud ID 方法的前缀为 `target`。

>[!TIP]
>
>[生命周期量度](/help/android/metrics.md)将作为参数发送至每个 mbox 负载。

## 类引用：TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**属性：**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**字符串常量**

>[!TIP]
>
>在为自定义参数设置键时，可以方便地使用以下常量。

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* 如果您使用的是&#x200B;**低于** 4.14.0 版本的 SDK，请访问 [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) 以了解参数限制。
   >
   >
* 如果您使用的是 4.14.0 版本&#x200B;**或更高版本**&#x200B;的 SDK，请访问 [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) 以了解参数限制。


* **loadRequest**

   向您配置的 Target 服务器发送 request，并返回在块 callback 中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   向您配置的 Target 服务器发送 request，并返回在块 callback 中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * 以下是此方法的代码示例：

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   向您配置的 Target 服务器发送请求，并返回在 TargetCallback 中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **返回：**&#x200B;不适用

   * **参数：**

      以下是此方法的参数：

      * **name**

         要检索的 Target mbox/位置的名称。

         * **类型：**&#x200B;字符串
      * **defaultContent**

         Target 服务器不可访问或用户不符合促销活动资格时，在回调中返回的值。

         * **类型：**&#x200B;字符串
      * **profileParameters**

         该词典中的值将在对 Target 的请求中用于“profileParameters”对象。

         * **类型：** Map `<String, Object>`
      * **orderParameters**

         该词典中的值将在对 Target 的请求中用于“order”对象。

         * **类型：** Map `<String, Object>`
      * **mboxParameters**

         该词典中的值将在对 Target 的请求中使用。

         * **类型：** Map `<String, Object>`
      * **requestLocationParameters**

         该词典中的值将在对 Target 的请求中用于“requestLocation”对象。

         * **类型：** Map `<String, Object>`
      * **callback**

         此方法将通过来自 Target 服务器的选件内容进行调用。如果 Target 服务器不可访问，或者用户不符合促销活动资格，则将返回 defaultContent。

         * **类型：** TargetCallback `<String>`
   * 以下是此方法的代码示例：

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      有关基本 Target API 的更多信息，请参阅 Target 开发人员帮助中的[交付](https://docs.adobe.com/dev/products/target/reference/delivery.html)。








* **createOrder&#x200B;ConfirmRequest**

   通过给定参数创建 TargetLocationRequest 对象。

   * 以下是此方法的语法：

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * 以下是此方法的代码示例：

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   通过给定参数创建 TargetLocationRequest 对象。

   * 以下是此方法的语法：

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * 以下是此方法的代码示例：

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   清除应用程序中的任何目标 Cookie。

   * 以下是此方法的语法：

      ```java
      public static void clearCookies();
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   返回 pcID。

   * 以下是此方法的语法：

      ```java
      public static String getPcID();
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   返回会话 ID。

   * 以下是此方法的语法：

      ```java
      public static String getSessionID();
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   设置第三方 ID。

   * 以下是此方法的语法：

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * 以下是此方法的代码示例：

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   返回第三方 ID。

   * 以下是此方法的语法：

      ```java
      public static String getThirdPartyID();
      ```

   * 以下是此方法的代码示例：

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
