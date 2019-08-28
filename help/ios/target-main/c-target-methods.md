---
description: 以下是 iOS 库提供的 Adobe Target 方法列表。
seo-description: 以下是 iOS 库提供的 Adobe Target 方法列表。
seo-title: Adobe Mobile Services的iOS Target方法
solution: Marketing Cloud，Analytics
title: iOS的目标方法
topic: 开发人员和实施
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# iOS的目标方法 {#target-methods}

以下是 iOS 库提供的 Adobe Target 方法列表。

SDK目前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀。例如， 方法的前缀为 `target`target。

>[!TIP]
>
>生命周期量度将作为参数发送至每个 mbox 负载。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

## 类引用：AdBtargetLocationRequest

### 属性

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### String常量

>[!TIP]
>
>在为自定义参数设置键时，以下常量便于使用。

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
>* If you are using SDKs **before** version 4.14.0, see [Input Parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or after**, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


### 方法

* **targetLoadRequest:callback**

   向您配置的 Target 服务器发送 request，并返回在块 `callback` 中生成的选件的字符串值。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   向您配置的 Target 服务器发送请求，并返回在块回调中生成的选件的字符串值。

   * 下面是这种方法对应的语法：

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

   * 返回：N/A

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

   * 以下是这种方法的代码示例：

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

      有关基础Target API的更多信息，请参阅 [Adobe Target开发人员](https://docs.adobe.com/dev/products/target/reference/delivery.html)。







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback**

   向您配置的 Target 服务器发送 request，并返回在块 callback 中生成的选件的字符串值。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * 以下是这种方法的代码示例：

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

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   创建 `ADBTargetLocationRequest`一个。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   一个方便使用的构造函数，用于使用给定参数创建 ADBTargetLocationRequest 对象。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   返回第三方 ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   设置第三方 ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   清除应用程序中的任何目标 Cookie。

   >[!TIP]
   >
   >从SDK版本4.10.0开始，Target不再使用cookies。此方法会重置 thirdPartyID 和 sessionID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) targetClearCookies;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   返回 PcID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   返回 SessionID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 以下是这种方法的代码示例：

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
