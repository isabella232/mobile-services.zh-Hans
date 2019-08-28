---
description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以在服务器调用中设置产品。
keywords: android；库；移动；sdk
seo-description: 无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以在服务器调用中设置产品。
seo-title: 产品变量
solution: Marketing Cloud，Analytics
title: 产品变量
topic: 开发人员和实施
uuid: f4484022-cb8 b-4dea-9209-5a110 ba607 df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

无法使用处理规则设置产品变量。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以在服务器调用中设置产品。

To set the *products* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *products* variable:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

例如：

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

*在图像请求上设置products* 变量，其他变量设置为上下文数据。必须使用处理规则映射所有上下文数据变量：

![](assets/map-products.png)

您不需要使用处理规则映射&#x200B;*products* 变量使用处理规则，因为此变量是直接在SDK的图像请求上设置的。
