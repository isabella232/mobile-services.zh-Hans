---
description: 以下是 iOS 库提供的 Adobe Target 方法列表。
seo-description: 以下是 iOS 库提供的 Adobe Target 方法列表。
seo-title: 适用于 Adobe Mobile Services 的 iOS Target 方法
solution: Experience Cloud,Analytics
title: 适用于 iOS 的 Target 方法
topic: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '656'
ht-degree: 100%

---


# 适用于 iOS 的 Target 方法 {#target-methods}

以下是 iOS 库提供的 Adobe Target 方法列表。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀。例如，Target 方法的前缀为 `target`。

>[!TIP]
>
>生命周期量度将作为参数发送至每个 mbox 负载。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。如果您在 `didFinishLaunching` 委托方法中发送 Target 请求，请在 Target 实施代码前添加 `[ADBMobile trackAction:data:]` 或 `[ADBMobile trackState:data:]` 调用。这样，Target 请求将包含完整的生命周期数据。

## 类引用：ADBTargetLocationRequest

### 属性

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### 字符串常量

>[!TIP]
>
>在为自定义参数设置键时，可以方便地使用以下常量。

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* 如果您使用的是&#x200B;**低于** 4.14.0 版本的 SDK，请参阅[输入参数](https://developers.adobetarget.com/api/#input-parameters)以了解参数限制。
   >
   >
* 如果您使用的是 4.14.0 版本&#x200B;**或更高版本**&#x200B;的 SDK，请参阅[批量输入参数](https://developers.adobetarget.com/api/#batch-input-parameters)以了解参数限制。


### 方法

* **targetLoadRequest:callback**

   向您配置的 Target 服务器发送 request，并返回在块 `callback` 中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   向您配置的 Target 服务器发送请求，并返回在块回调中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * 返回：不适用

   * 以下是此方法的参数：

      * **`name`**

         要检索的 Target mbox/位置的名称。

         * **类型**：NSString*
      * **`defaultContent`**

         Target 服务器不可访问或用户不符合促销活动资格时，在回调中返回的值。

         * **类型**：NSString*
      * **`profileParameters`**

         该词典中的值将在对 Target 的请求中用于“profileParameters”对象。

         * **类型**：NSDictionary*
      * **`orderParameters`**

         该词典中的值将在对 Target 的请求中用于“order”对象。

         * **类型**：NSDictionary
      * **`mboxParameters`**

         该词典中的值将在对 Target 的请求中用于“mboxParameters”对象。

         * **类型**：NSDictionary*
      * **`requestLocationParameters`**

         该词典中的值将在对 Target 的请求中用于“requestLocation”对象。

         **类型**：NSDictionary*

      * **`callback`**

         此方法将通过来自 Target 服务器的选件内容进行调用。如果 Target 服务器不可访问，或者用户不符合促销活动资格，则将返回 defaultContent。
      **类型**：函数

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      有关基础 Target API 的更多信息，请参阅 [Adobe Target 开发人员](https://docs.adobe.com/dev/products/target/reference/delivery.html)。







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   向您配置的 Target 服务器发送 request，并返回在块 callback 中生成的选件的字符串值。

   * 以下是此方法的语法：

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrderConfirmRequestWithName:orderId:orderTotal:productPurchasedId:parameters**

   创建 `ADBTargetLocationRequest`。

   * 以下是此方法的语法：

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:defaultContent:parameters**

   一个方便使用的构造函数，用于使用给定参数创建 ADBTargetLocationRequest 对象。

   * 以下是此方法的语法：

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   返回第三方 ID。

   * 以下是此方法的语法：

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   设置第三方 ID。

   * 以下是此方法的语法：

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   清除应用程序中的任何目标 Cookie。

   >[!TIP]
   >
   >自 SDK 版本 4.10.0 起，Target 不再使用 Cookie。此方法会重置 thirdPartyID 和 sessionID。

   * 以下是此方法的语法：

      ```objective-c
      + (void) targetClearCookies;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   返回 PcID。

   * 以下是此方法的语法：

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   返回 SessionID。

   * 以下是此方法的语法：

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### 示例

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
