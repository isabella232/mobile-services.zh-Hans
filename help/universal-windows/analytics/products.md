---
description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。
seo-description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。
seo-title: 产品变量
solution: Marketing Cloud，Analytics
title: 产品变量
topic: 开发人员和实施
uuid: 607983d6-48ac-4274-bfc8-b1 ca4 e5 add1 b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products` variable:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

例如：

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

The *`products`* is set directly on the image request, and the other variables are set as context data. 必须使用处理规则映射所有上下文数据变量：

![](assets/products-procrules.png)

您无需使用处理规则映射 *`products`* 变量，因为它是直接在SDK的图像请求上设置的。

## Products variable with merchandising eVars and product-specific events {#section_685D53AD3D064F9A8E225F995A9BA545}

An example of the *`products`* variable with Merchandising eVars and product-specific events.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>如果使用变量 *`&&products`* 触发特定于产品的事件，则还必须在 *`&&events`* 变量中设置该事件，否则在处理过程中会筛选出该事件。

