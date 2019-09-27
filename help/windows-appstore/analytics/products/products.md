---
description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。
seo-description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。
seo-title: 产品变量
solution: Marketing Cloud,Analytics
title: 产品变量
topic: 开发人员和实施
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable{#products-variable}

无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置产品。

To set the  variable, set a context data key to , and set the value using the syntax defined for the :*`products`*`"&&products"`*`products`*

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

*`products`* 直接在图像请求上设置，其他变量则设置为上下文数据。 必须使用处理规则映射所有上下文数据变量：

![](assets/products-procrules.png)

You do not need to map the  variable using processing rules since it is set directly on the image request by the SDK.*`products`*
