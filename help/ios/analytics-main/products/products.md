---
description: 无法使用处理规则设置产品变量。在 iOS 4.x SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置产品。
seo-description: 无法使用处理规则设置产品变量。在 iOS 4.x SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置产品。
seo-title: 产品变量
solution: Marketing Cloud，Analytics
title: 产品变量
topic: 开发人员和实施
uuid: 6e4d27-ef86-435c-a6 f7-bd76 be1 c95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

无法使用处理规则设置产品变量。在 iOS 4.x SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置产品。

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

例如：

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* 在图像请求上直接设置，其他变量设置为上下文数据。必须使用处理规则映射所有上下文数据变量：

![](assets/map-products.png)

您不需要使用处理规则映射&#x200B;*`products`*&#x200B;变量，因为该变量是由 SDK 直接在图像请求中设置的。
