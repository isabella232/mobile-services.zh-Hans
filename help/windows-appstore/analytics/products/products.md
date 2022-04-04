---
description: 无法使用处理规则设置产品变量。 在Mobile SDK中，必须在上下文数据参数中使用特殊语法来直接在服务器调用中设置产品。
solution: Experience Cloud Services,Analytics
title: Products 变量
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Products 变量{#products-variable}

无法使用处理规则设置产品变量。 在Mobile SDK中，必须在上下文数据参数中使用特殊语法来直接在服务器调用中设置产品。

设置 *`products`* 变量，请将上下文数据键设置为 `"&&products"`，然后使用为 *`products`*:

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

*`products`* 直接在图像请求中设置，而其他变量则设置为上下文数据：必须使用处理规则映射所有上下文数据变量：

![](assets/products-procrules.png)

您无需映射 *`products`* 变量，因为该变量是由SDK直接在图像请求中设置的。
