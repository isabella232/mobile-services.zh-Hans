---
description: Adobe Target 预取功能使用 iOS Mobile SDK 获取选件内容，并通过缓存服务器响应来尽量减少获取次数。
title: 在 iOS 中预取选件内容
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 85%

---

# 在 iOS 中预取选件内容 {#prefetch-offer-content-in-ios}

Adobe Target 预取功能使用 iOS Mobile SDK 获取选件内容，并通过缓存服务器响应来尽量减少获取次数。

>[!IMPORTANT]
>
>Adobe Target 中的 Auto Target、Auto Allocate 和 Automated Personalization 活动类型不支持 iOS Mobile SDK 中的预取功能。

此过程可缩短加载时间，阻止多个网络调用，并允许Adobe Target接收有关移动设备应用程序用户访问了哪个mbox的通知。 在预取调用期间将检索和缓存所有内容，对于将来所有包含指定mbox名称的缓存内容的调用，都将从缓存中检索此内容。

在启动时，预取内容不会持久保留。只要应用程序处于活动状态，或者在调用 `clearPrefetchCache()` 方法之前，都会一直缓存预取内容。

>[!IMPORTANT]
>
>Target 预取 API 自 SDK 版本 4.14.0 起便已推出。有关参数限制的更多信息，请参阅[批量处理输入参数](https://developers.adobetarget.com/api/#batch-input-parameters)。

在 SDK 版本 4.14 或更高版本中，如果已指定 `environmentId`，则在发起 v2 批量 mbox TNT 调用时，会从 `ADBMobileConfig.json` 文件中选取指定的 environmentId。如果未在此文件中指定 `environmentId`，则不会在 TNT 批量 mbox 调用中发送任何环境参数，将交付默认环境的选件。

例如：

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## 预取方法 {#section_05967F1F3A554B0FBC2C08A954554BDE}

以下是可用于在 iOS 中进行预取的方法：

* **targetPrefetchContent**

   将包含位置数组的预取请求发送到配置的 Target 服务器，并在提供的回调中返回请求状态。

   * 以下是此方法的语法：

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * 以下是此方法的参数：

      * **`targetPrefetchArray`**

         `TargetPrefetchObjects` 的数组，其中包含要预取的每个 Target 位置的名称和 mboxParameters。

      * **`profileParameters`**

         包含要在此请求中用于每个位置预取的配置文件参数的键和值。

      * **`callback`**

         在预取完成时被调用。如果预取成功，则返回 `true`；如果预取失败，则返回 `false`。

* **targetLoadRequests**

   执行批量请求，以获取请求数组中指定的多个 mbox 位置。数组中的每个对象都包含一个回调函数，当其给定的 mbox 位置有相应的内容可用时，将会调用该函数。

   >[!IMPORTANT]
   >
   >如果所请求位置的内容已经缓存，则会立即在提供的回调中返回该内容。否则，SDK 将向 Target 服务器发送网络请求，以检索该内容。

   * 以下是此方法的语法：

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * 以下是此方法的参数：

      * **`requests`**

         `TargetRequestObjects` 的数组，其中包含要检索的每个位置的名称、默认内容、参数和回调函数。

      * **`profileParameters`**

         包含要在此请求中用于每个位置预取的配置文件参数的键和值。

* **targetPrefetchClearCache**

   清除通过 Target 预取缓存的数据。

   * 以下是此方法的语法：

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * 此方法没有参数。

* **targetRequestObjectWithName**

   使用提供的数据创建并返回 `TargetRequestObject` 的实例。

   * 以下是此方法的语法：

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * 此方法没有参数。

* **createTargetPrefetchObject**

   使用提供的数据创建并返回 `TargetPrefetchObject` 的实例。

   * 以下是此方法的语法：

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## 公共类 {#section_A273E53F069E4327BBC8CE4910B37888}

以下是 iOS 中支持预取的公共类：

### 类引用：TargetPreFetchObject

封装 mbox 名称以及用于 mbox 预取的参数。

* **`name`**

   要检索的位置/mbox 的名称。

   * **类型**：NSString*

* **`mboxParameters`**

   包含 mbox 参数键值对的可选词典。

   * **类型**：NSDictionary*

* **`orderParameters`**

   包含顺序参数键值对的字典。

   * **类型**：NSDictionary*

* **`productParameters`**

   包含产品参数键值对的字典。

   * **类型**：NSDictionary*

### 类引用：TargetRequestObject

此类封装用于 Target 位置请求的 mbox 名称、默认内容、mbox 参数以及返回的回调。

* **`name`**

   请求的位置的名称。

   * **类型**：NSString*

* **`mboxParameters`**

   表示要检索的位置/mbox名称的NSString值。

   * **类型**：NSString*

* **`defaultContent`**

   Target服务器不可访问时将返回的默认内容。

   * **类型**：NSString*

* **`callback`**

   在批量请求 Target 位置时，如果此位置有相应的内容可用，将会调用 callback。

   * **类型**：函数

## 代码示例 {#section_BF7F49763D254371B4656E17953D520C}

以下是如何使用 iOS SDK 预取内容的示例：

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

以下是使用 iOS SDK 批量处理 `loadRequest` 的示例：

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## 其他信息 {#section_A454BAD1CD49423E86C71BAEE06125FD}

以下是有关上述示例的其他一些信息：

* `ProductParameters` 仅允许使用以下键：

   * `id`
   * `categoryId`

* `OrderParameters` 仅允许使用以下键：

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` 接受字符串数组。
